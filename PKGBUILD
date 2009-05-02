# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
pkgname=qemu
pkgver=0.10.3
pkgrel=1
pkgdesc="QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation."
arch=(i686 x86_64)
license=('GPL2' 'LGPL2')
url="http://www.nongnu.org/qemu/"
depends=('sdl' 'alsa-lib' 'esound' 'zlib' 'e2fsprogs' 'gnutls>=2.4.1' 'bluez')
install=qemu.install
source=(http://savannah.nongnu.org/download/${pkgname}/${pkgname}-${pkgver}.tar.gz
        65-kvm.rules
        70-kqemu.rules)

build()
{
  cd ${srcdir}/${pkgname}-${pkgver}
  sed -i -e 's/lib64/lib/g' x86_64.ld || return 1
  ./configure --prefix=/usr --audio-drv-list=oss,alsa,sdl,esd \
              --kerneldir="/usr/src/linux-$(uname -r)"
  make || return 1
  make DESTDIR=${pkgdir} install || return 1
  install -D -m644 ${srcdir}/70-kqemu.rules \
                   ${pkgdir}/lib/udev/rules.d/70-kqemu.rules
  install -D -m644 ${srcdir}/65-kvm.rules \
                   ${pkgdir}/lib/udev/rules.d/65-kvm.rules
}
