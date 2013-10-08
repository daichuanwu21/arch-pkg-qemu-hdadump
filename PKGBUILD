# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
pkgname=('qemu' 'libcacard')
pkgver=1.6.0
pkgrel=5
arch=('i686' 'x86_64')
license=('GPL2' 'LGPL2.1')
url="http://wiki.qemu.org/Index.html"
makedepends=('texi2html' 'perl' 'python2')
install=qemu.install
source=(http://wiki.qemu.org/download/${pkgname}-${pkgver}.tar.bz2
        65-kvm.rules)
replaces=('qemu-kvm')
options=(!strip)

build ()
{
  cd "${srcdir}/${pkgname}-${pkgver}"
  # gtk gui breaks keymappings at the moment
  ./configure --prefix=/usr --sysconfdir=/etc --audio-drv-list='pa alsa sdl' \
              --python=/usr/bin/python2 --smbd=/usr/bin/smbd \
              --enable-docs --enable-mixemu --libexecdir=/usr/lib/qemu \
              --disable-gtk --enable-linux-aio --enable-seccomp --localstatedir=/var
              make
}

package_qemu() {
  pkgdesc="A generic and open source processor emulator which achieves a good emulation speed by using dynamic translation."
  depends=('pixman' 'libjpeg' 'libpng' 'sdl' 'alsa-lib' 'nss' 'glib2'
         'gnutls>=2.4.1' 'bluez-libs' 'vde2' 'util-linux' 'curl' 'libsasl'
         'libgl' 'libpulse' 'seabios' 'libcap-ng' 'libaio' 'libseccomp'
         'libiscsi' 'libcacard')
  backup=('etc/qemu/target-x86_64.conf')
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" libexecdir="/usr/lib/qemu" install
  # provided by seabios package
  rm "${pkgdir}/usr/share/qemu/bios.bin"
  rm "${pkgdir}/usr/share/qemu/acpi-dsdt.aml"
  rm "${pkgdir}/usr/share/qemu/q35-acpi-dsdt.aml"
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
 options=('strip' '!libtool')
 depends=('nss' 'libaio' 'libcap-ng' 'libiscsi' 'curl' 'vde2')
 mkdir -p ${pkgdir}/usr/bin
 mkdir -p ${pkgdir}/usr/lib/pkgconfig
 mkdir -p ${pkgdir}/usr/include/cacard
 cp -a ${srcdir}/qemu-${pkgver}/libcacard/*.h ${pkgdir}/usr/include/cacard/
 cp -a ${srcdir}/qemu-${pkgver}/.libs/libcacard.so* ${pkgdir}/usr/lib/
 cp -a ${srcdir}/qemu-${pkgver}/libcacard.pc ${pkgdir}/usr/lib/pkgconfig/
 cp -a ${srcdir}/qemu-${pkgver}/.libs/vscclient ${pkgdir}/usr/bin/
}
md5sums=('f3f39308472d629aca57a255a0c91ba9'
         '9d6de26867a05c306157e3d3c612b28a')
