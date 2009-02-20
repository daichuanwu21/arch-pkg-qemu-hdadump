# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
pkgname=qemu
pkgver=0.9.1
pkgrel=16
_kvmver=84
pkgdesc="QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation."
arch=(i686 x86_64)
license=('GPL')
url="http://bellard.org/qemu/"
depends=('sdl' 'alsa-lib' 'zlib' 'e2fsprogs' 'gnutls>=2.4.1' 'bluez')
makedepends=('gcc34')
install=qemu.install
source=(http://bellard.org/${pkgname}/${pkgname}-${pkgver}.tar.gz
        70-kqemu.rules
        http://downloads.sourceforge.net/kvm/kvm-$_kvmver.tar.gz
        dirent.patch
        kvm-bios.diff)

build()
{
  cd ${srcdir}/${pkgname}-${pkgver}
  unset CFLAGS
  if [ "${CARCH}" = "x86_64" ]; then
	sed -i -e 's/lib64/lib/g' x86_64.ld || return 1
        # any "xxx-user" target seems to not build on x86_64
         ./configure --prefix=/usr --enable-alsa \
                     --target-list="i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu arm-softmmu mips-softmmu"
  else 
         ./configure --prefix=/usr --enable-alsa
  fi
  # fix compiling
  patch -Np0 -i ../dirent.patch || return 1
  make || return 1
  make DESTDIR=${startdir}/pkg install || return 1
  install -D -m644 ${srcdir}/70-kqemu.rules \
                   ${pkgdir}/etc/udev/rules.d/70-kqemu.rules

  # we add the kvm/qemu version
    cd ${srcdir}/kvm-$_kvmver
    # fix bios versions
    patch -Np1 -i ../kvm-bios.diff || return 1
    ./configure --prefix=/usr
  # fix sdl compilation, JON: and extboot
    sed -i -e 's#-rpath,/usr/lib#-rpath,/usr/lib,-rpath,/lib#g' qemu/config-host.mak
    for dir in libkvm user qemu extboot; do
      cd ${srcdir}/kvm-$_kvmver/${dir}
      make || return 1
    done
   # install kvm-qemu
    install -m 755 ${srcdir}/kvm-$_kvmver/qemu/x86_64-softmmu/qemu-system-x86_64 \
        ${pkgdir}/usr/bin/qemu-kvm
    install -D -m644 ${srcdir}/kvm-$_kvmver/scripts/65-kvm.rules \
    	${pkgdir}/etc/udev/rules.d/65-kvm.rules || return 1
   # install kvm bios files
   install -D -m644 ${srcdir}/kvm-$_kvmver/qemu/pc-bios/bios.bin \
       ${pkgdir}/usr/share/qemu/bios-kvm.bin
   install -D -m644 ${srcdir}/kvm-$_kvmver/qemu/pc-bios/vgabios.bin \
       ${pkgdir}/usr/share/qemu/vgabios-kvm.bin
   install -D -m644 ${srcdir}/kvm-$_kvmver/qemu/pc-bios/vgabios-cirrus.bin \
       ${pkgdir}/usr/share/qemu/vgabios-cirrus-kvm.bin
   install -D -m644 ${srcdir}/kvm-$_kvmver/extboot/extboot.bin \
	${pkgdir}/usr/share/qemu/extboot-kvm.bin
}
md5sums=('6591df8e9270eb358c881de4ebea1262'
         'ec06591830b8fcf53913f05f3d66f7e5'
         '39b7206ef400845800f081a5b901f757'
         '4ea5d2609edcca10f927d7ddd233e8d2'
         '1cdfcbd3cc569eec96a36d7557291fd2')
