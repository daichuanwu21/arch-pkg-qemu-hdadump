# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Sébastien "Seblu" Luttringer <seblu@seblu.net>

pkgbase=qemu
pkgname=(qemu qemu-headless qemu-arch-extra
         qemu-block-{iscsi,rbd,gluster} qemu-guest-agent)
pkgdesc="A generic and open source machine emulator and virtualizer"
pkgver=2.6.0
pkgrel=2
arch=(i686 x86_64)
license=(GPL2 LGPL2.1)
url="http://wiki.qemu.org/"
_headlessdeps=(seabios gnutls libpng libaio numactl jemalloc xfsprogs libnfs
               lzo snappy curl vde2 libcap-ng spice usbredir)
depends=(virglrenderer sdl2 vte3 brltty "${_headlessdeps[@]}")
makedepends=(spice-protocol python2 ceph libiscsi glusterfs)
source=("$url/download/${pkgname}-${pkgver}.tar.bz2"
        qemu.sysusers
        qemu-ga.service
        65-kvm.rules)
md5sums=('ca3f70b43f093e33e9e014f144067f13'
         '49778d11c28af170c4bebcc648b0ace1'
         '44ee242d758f9318c6a1ea1dae96aa3a'
         '33ab286a20242dda7743a900f369d68a')

case $CARCH in
  i?86) _corearch=i386 ;;
  x86_64) _corearch=x86_64 ;;
esac

prepare() {
  mkdir build-{full,headless}
  mkdir -p extra-arch-{full,headless}/usr/{bin,share/qemu}

  cd ${pkgname}-${pkgver}
  sed -i 's/vte-2\.90/vte-2.91/g' configure
}

build() {
  _build full \
    --audio-drv-list="pa alsa sdl"

  _build headless \
    --target-list=${_corearch}-softmmu \
    --audio-drv-list= \
    --disable-bluez \
    --disable-sdl \
    --disable-gtk \
    --disable-vte \
    --disable-opengl \
    --disable-virglrenderer \
    --disable-brlapi
}

_build() (
  cd build-$1

  # qemu vs. make 4 == bad
  export ARFLAGS=rv

  # http://permalink.gmane.org/gmane.comp.emulators.qemu/238740
  export CFLAGS+=" -fPIC"

  ../${pkgname}-${pkgver}/configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --localstatedir=/var \
    --libexecdir=/usr/lib/qemu \
    --python=/usr/bin/python2 \
    --smbd=/usr/bin/smbd \
    --with-gtkabi=3.0 \
    --with-sdlabi=2.0 \
    --enable-modules \
    --enable-jemalloc \
    "${@:2}"

  make
)

package_qemu() {
  provides=(qemu-headless)
  replaces=(qemu-kvm)

  _package full
}

package_qemu-headless() {
  pkgdesc="QEMU without graphical user interface"
  depends=("${_headlessdeps[@]}")

  _package headless
}

_package() {
  optdepends=('samba: SMB/CIFS server support'
              'qemu-arch-extra: extra architectures support'
              'qemu-block-iscsi: iSCSI block support'
              'qemu-block-rbd: RBD block support'
              'qemu-block-gluster: glusterfs block support')
  install=qemu.install
  options=(!strip)

  make -C build-$1 DESTDIR="$pkgdir" install "${@:2}"

  # systemd stuff
  install -Dm644 65-kvm.rules "$pkgdir/usr/lib/udev/rules.d/65-kvm.rules"
  install -Dm644 qemu.sysusers "$pkgdir/usr/lib/sysusers.d/qemu.conf"

  # remove conflicting /var/run directory
  cd "$pkgdir"
  rm -r var

  cd usr/lib
  tidy_strip

  # bridge_helper needs suid
  # https://bugs.archlinux.org/task/32565
  chmod u+s qemu/qemu-bridge-helper

  # remove split block modules
  rm qemu/block-{iscsi,rbd,gluster}.so

  cd ../bin
  tidy_strip

  # remove extra arch
  for _bin in qemu-*; do
    [[ -f $_bin ]] || continue

    case ${_bin#qemu-} in
      # guest agent
      ga) rm "$_bin"; continue ;;

      # tools
      img|io|nbd) continue ;;

      # core emu
      system-${_corearch}) continue ;;
    esac

    mv "$_bin" "$srcdir/extra-arch-$1/usr/bin"
  done

  cd ../share/qemu
  for _blob in *; do
    [[ -f $_blob ]] || continue

    case $_blob in
      # provided by seabios package
      bios.bin|acpi-dsdt.aml|bios-256k.bin|vgabios-cirrus.bin|vgabios-qxl.bin|\
      vgabios-stdvga.bin|vgabios-vmware.bin) rm "$_blob"; continue ;;

      # iPXE ROMs
      efi-*|pxe-*) continue ;;

      # core blobs
      kvmvapic.bin|linuxboot.bin|multiboot.bin|sgabios.bin|vgabios*) continue ;;

      # Trace events definitions
      trace-events) continue ;;

      # Logos
      *.bmp|*.svg) continue ;;
    esac

    mv "$_blob" "$srcdir/extra-arch-$1/usr/share/qemu"
  done
}

package_qemu-arch-extra() {
  pkgdesc="QEMU for foreign architectures"
  depends=(qemu)
  options=(!strip)

  mv extra-arch-full/usr "$pkgdir"
}

package_qemu-block-iscsi() {
  pkgdesc="QEMU iSCSI block module"
  depends=(glib2 libiscsi jemalloc)

  install -D build-full/block-iscsi.so "$pkgdir/usr/lib/qemu/block-iscsi.so"
}

package_qemu-block-rbd() {
  pkgdesc="QEMU RBD block module"
  depends=(glib2 ceph)

  install -D build-full/block-rbd.so "$pkgdir/usr/lib/qemu/block-rbd.so"
}

package_qemu-block-gluster() {
  pkgdesc="QEMU GlusterFS block module"
  depends=(glib2 glusterfs)

  install -D build-full/block-gluster.so "$pkgdir/usr/lib/qemu/block-gluster.so"
}

package_qemu-guest-agent() {
  pkgdesc="QEMU Guest Agent"
  depends=(gcc-libs glib2)

  install -D build-full/qemu-ga "$pkgdir/usr/bin/qemu-ga"
  install -Dm644 qemu-ga.service "$pkgdir/usr/lib/systemd/system/qemu-ga.service"
}

# vim:set ts=2 sw=2 et:
