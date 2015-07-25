# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
pkgname=('qemu' 'libcacard')
pkgver=2.3.0
pkgrel=4
arch=('i686' 'x86_64')
license=('GPL2' 'LGPL2.1')
url="http://wiki.qemu.org/Index.html"
makedepends=('pixman' 'libjpeg' 'libpng' 'sdl' 'alsa-lib' 'nss' 'glib2'
             'gnutls' 'bluez-libs' 'vde2' 'util-linux' 'curl' 'libsasl'
             'libgl' 'libpulse' 'seabios' 'libcap-ng' 'libaio' 'libseccomp'
             'libiscsi' 'libcacard' 'spice' 'spice-protocol' 'python2'
             'usbredir' 'ceph' 'glusterfs' 'libssh2' 'lzo')
options=(!strip)
source=(http://wiki.qemu.org/download/${pkgname}-${pkgver}.tar.bz2
        CVE-2015-3456.patch
        65-kvm.rules)

prepare() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  patch -p1 -i ${srcdir}/CVE-2015-3456.patch
}

build ()
{
  cd "${srcdir}/${pkgname}-${pkgver}"
  # qemu vs. make 4 == bad
  export ARFLAGS="rv"
  # http://permalink.gmane.org/gmane.comp.emulators.qemu/238740
  export CFLAGS+=' -fPIC'
  # gtk gui breaks keymappings at the moment
  ./configure --prefix=/usr --sysconfdir=/etc --audio-drv-list='pa alsa sdl' \
              --python=/usr/bin/python2 --smbd=/usr/bin/smbd \
              --enable-docs --libexecdir=/usr/lib/qemu \
              --disable-gtk --enable-linux-aio --enable-seccomp \
              --enable-spice --localstatedir=/var \
              --enable-tpm \
              --enable-modules --enable-{rbd,glusterfs,libiscsi,curl}
  make V=99
}

package_qemu() {
  pkgdesc="A generic and open source processor emulator which achieves a good emulation speed by using dynamic translation."
  depends=('pixman' 'libjpeg' 'libpng' 'sdl' 'alsa-lib' 'nss' 'glib2'
         'gnutls' 'bluez-libs' 'vde2' 'util-linux' 'curl' 'libsasl'
         'libgl' 'libpulse' 'seabios' 'libcap-ng' 'libaio' 'libseccomp'
         'libcacard' 'spice' 'usbredir' 'lzo')
  backup=('etc/qemu/target-x86_64.conf')
  replaces=('qemu-kvm')
  optdepends=('samba: for SMB server support'
			  'libssh2: for remote disks over ssh support'
			  'curl: for remote disks over http/ftp support'
              'libiscsi: for iSCSI support'
              'ceph: for RDB support'
			  'glusterfs: for glusterfs support')
  install=qemu.install
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" libexecdir="/usr/lib/qemu" install
  # provided by seabios package
  rm "${pkgdir}/usr/share/qemu/bios.bin"
  rm "${pkgdir}/usr/share/qemu/acpi-dsdt.aml"
  rm "${pkgdir}/usr/share/qemu/q35-acpi-dsdt.aml"
  rm "${pkgdir}/usr/share/qemu/bios-256k.bin"
  rm "${pkgdir}/usr/share/qemu/vgabios-cirrus.bin"
  rm "${pkgdir}/usr/share/qemu/vgabios-qxl.bin"
  rm "${pkgdir}/usr/share/qemu/vgabios-stdvga.bin"
  rm "${pkgdir}/usr/share/qemu/vgabios-vmware.bin"

  # remove conflicting /var/run directory
  rm -r "${pkgdir}/var"
  install -D -m644 "${srcdir}/65-kvm.rules" \
                   "${pkgdir}/usr/lib/udev/rules.d/65-kvm.rules"
  # bridge_helper needs suid
  # https://bugs.archlinux.org/task/32565
  chmod u+s "${pkgdir}/usr/lib/qemu/qemu-bridge-helper"
  # add sample config
  echo "allow br0" > ${pkgdir}/etc/qemu/bridge.conf.sample
  # strip scripts directory
    find "${pkgdir}/usr/src/linux-${_kernver}/scripts"  -type f -perm -u+w 2>/dev/null | while read binary ; do
      case "$(file -bi "$binary")" in
        *application/x-executable*) # Binaries
        /usr/bin/strip $STRIP_BINARIES "$binary";;
      esac
    done
  # remove libcacard files
  rm -rf ${pkgdir}/usr/include/cacard
  rm -rf ${pkgdir}/usr/lib/libcacard*
  rm -rf ${pkgdir}/usr/lib/pkgconfig/libcacard.pc
  rm -rf ${pkgdir}/usr/bin/vscclient
}

package_libcacard() {
 pkgdesc="Common Access Card (CAC) Emulation"
 options=('strip')
 depends=('nss' 'libaio' 'libcap-ng' 'libiscsi' 'curl' 'vde2' 'glib2')
 mkdir -p ${pkgdir}/usr/bin
 mkdir -p ${pkgdir}/usr/lib/pkgconfig
 mkdir -p ${pkgdir}/usr/include/cacard
 cp -a ${srcdir}/qemu-${pkgver}/libcacard/*.h ${pkgdir}/usr/include/cacard/
 cp -a ${srcdir}/qemu-${pkgver}/.libs/libcacard.so* ${pkgdir}/usr/lib/
 cp -a ${srcdir}/qemu-${pkgver}/libcacard.pc ${pkgdir}/usr/lib/pkgconfig/
 cp -a ${srcdir}/qemu-${pkgver}/.libs/vscclient ${pkgdir}/usr/bin/
}
md5sums=('2fab3ea4460de9b57192e5b8b311f221'
         '5e8a68940c4e0267e795a6ddd144e00e'
         '33ab286a20242dda7743a900f369d68a')
