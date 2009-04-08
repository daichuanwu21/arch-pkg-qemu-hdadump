# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
pkgname=qemu
pkgver=0.10.2
pkgrel=1
pkgdesc="QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation."
arch=(i686 x86_64)
license=('GPL2' 'LGPL2')
url="http://www.nongnu.org/qemu/"
depends=('sdl' 'alsa-lib' 'esound' 'zlib' 'e2fsprogs' 'gnutls>=2.4.1' 'bluez')
install=qemu.install
source=(http://savannah.nongnu.org/download/${pkgname}/${pkgname}-${pkgver}.tar.gz
        70-kqemu.rules)

build()
{
  cd ${srcdir}/${pkgname}-${pkgver}
  sed -i -e 's/lib64/lib/g' x86_64.ld || return 1
  ./configure --prefix=/usr --audio-drv-list=oss,alsa,sdl,esd \
              --kerneldir="/usr/src/linux-$(uname -r)"
  make || return 1
  make DESTDIR=${startdir}/pkg install || return 1
  install -D -m644 ${srcdir}/70-kqemu.rules \
                   ${pkgdir}/lib/udev/rules.d/70-kqemu.rules

}
md5sums=('85a323cdf620687f39c5328f450a547d'
         'ec06591830b8fcf53913f05f3d66f7e5')
