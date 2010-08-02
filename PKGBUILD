# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
pkgname=qemu
pkgver=0.12.5
pkgrel=1
pkgdesc="QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation."
arch=('i686' 'x86_64')
license=('GPL2' 'LGPL2.1')
url="http://wiki.qemu.org/Index.html"
makedepends=('texi2html' 'perl')
depends=('sdl' 'alsa-lib' 'esound' 'gnutls>=2.4.1' 'bluez' 'vde2' 'util-linux-ng' 'curl' 'libsasl')
install=qemu.install
source=(http://savannah.nongnu.org/download/${pkgname}/${pkgname}-${pkgver}.tar.gz
        65-kvm.rules)

build()
{
  cd ${srcdir}/${pkgname}-${pkgver}
  sed -i -e 's/lib64/lib/g' x86_64.ld || return 1
  ./configure --prefix=/usr --audio-drv-list=oss,alsa,sdl,esd \
              --audio-card-list=ac97,sb16,es1370,adlib \
              --enable-docs \
              --kerneldir="/usr/src/linux-$(uname -r)"
  make || return 1
  make DESTDIR=${pkgdir} install || return 1
  install -D -m644 ${srcdir}/65-kvm.rules \
                   ${pkgdir}/lib/udev/rules.d/65-kvm.rules
}
md5sums=('1d02ee0a04dfae2894340273372c1de4'
         'b316a066d2f1bb57d8f5b7ea1d0d1caf')
