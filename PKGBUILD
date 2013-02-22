# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
pkgname=qemu
pkgver=1.4.0
pkgrel=1
pkgdesc="A generic and open source processor emulator which achieves a good emulation speed by using dynamic translation."
arch=('i686' 'x86_64')
license=('GPL2' 'LGPL2.1')
url="http://wiki.qemu.org/Index.html"
makedepends=('texi2html' 'perl' 'python2')
depends=('libjpeg' 'libpng' 'sdl' 'alsa-lib' 'nss' 'glib2' 'gnutls>=2.4.1' 'bluez' 'vde2' 'util-linux' 'curl' 'libsasl' 'libgl' 'libpulse' 'seabios' 'libcap-ng')
backup=('etc/qemu/target-x86_64.conf')
install=qemu.install
source=(http://wiki.qemu.org/download/${pkgname}-${pkgver}.tar.bz2
        doc-fix-sheepdog-invalid-texi-table-list-syntax.patch
        65-kvm.rules)
replaces=('qemu-kvm')
options=(!strip)

build()
{
  cd "${srcdir}/${pkgname}-${pkgver}"
  sed -i -e 's/lib64/lib/g' ldscripts/x86_64.ld
  # fix building with tex version 5.0
  # https://bugs.launchpad.net/qemu/+bug/1130533
  patch -Np1 -i ${srcdir}/doc-fix-sheepdog-invalid-texi-table-list-syntax.patch
  ./configure --prefix=/usr --sysconfdir=/etc --audio-drv-list=oss,alsa,sdl,pa \
              --python=/usr/bin/python2 \
              --audio-card-list=ac97,sb16,es1370,hda \
              --enable-docs --enable-mixemu --libexecdir=/usr/lib/qemu
              make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" libexecdir="/usr/lib/qemu" install
  rm "${pkgdir}/usr/share/qemu/bios.bin"

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

}
md5sums=('78f13b774814b6b7ebcaf4f9b9204318'
         'b431782f310bfc6af4ef21a8068f866b'
         'b316a066d2f1bb57d8f5b7ea1d0d1caf')
