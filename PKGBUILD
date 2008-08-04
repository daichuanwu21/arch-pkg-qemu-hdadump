# Maintainer: Tobias Powalowski <tpowa@archlinux.org>
pkgname=qemu
pkgver=0.9.1
pkgrel=8
_kvmver=72
pkgdesc="QEMU is a generic and open source processor emulator which achieves a good emulation speed by using dynamic translation."
arch=(i686 x86_64)
license=('GPL')
url="http://fabrice.bellard.free.fr/qemu/"
depends=('sdl' 'alsa-lib' 'zlib' 'e2fsprogs' 'gnutls>=2.4.1')
makedepends=('gcc34')
install=qemu.install
source=(http://bellard.org/${pkgname}/${pkgname}-${pkgver}.tar.gz \
        70-kqemu.rules \
        http://downloads.sourceforge.net/kvm/kvm-$_kvmver.tar.gz\
	kvm-bios.diff)

build()
{
  cd ${startdir}/src/${pkgname}-${pkgver}
  unset CFLAGS

  if [ "${CARCH}" = "x86_64" ]; then
     # any "xxx-user" target seems to not build on x86_64
         ./configure --prefix=/usr --enable-alsa \
                     --target-list="i386-softmmu ppc-softmmu sparc-softmmu x86_64-softmmu arm-softmmu mips-softmmu"
  else 
         ./configure --prefix=/usr --enable-alsa
  fi
  # fix sdl compilation
  sed -i -e 's#-rpath,/usr/lib#-rpath,/usr/lib,-rpath,/lib#g' config-host.mak

  make || return 1
  make DESTDIR=${startdir}/pkg install || return 1
  install -D -m644 ${startdir}/src/70-kqemu.rules \
                   ${startdir}/pkg/etc/udev/rules.d/70-kqemu.rules

  # we add the kvm/qemu version
    cd ${startdir}/src/kvm-$_kvmver
    patch -Np1 -i ../kvm-bios.diff || return 1
    ./configure --prefix=/usr
  # fix sdl compilation, JON: and extboot
    sed -i -e 's#-rpath,/usr/lib#-rpath,/usr/lib,-rpath,/lib#g' qemu/config-host.mak
    for dir in libkvm user qemu extboot; do
      cd ${startdir}/src/kvm-$_kvmver/${dir}
      make || return 1
    done
   # install kvm-qemu
    install -m 755 ${startdir}/src/kvm-$_kvmver/qemu/x86_64-softmmu/qemu-system-x86_64 \
        ${startdir}/pkg/usr/bin/qemu-kvm
    install -D -m644 ${startdir}/src/kvm-$_kvmver/scripts/65-kvm.rules \
    	${startdir}/pkg/etc/udev/rules.d/65-kvm.rules || return 1
   # install kvm bios files
   install -D -m644 ${startdir}/src/kvm-$_kvmver/qemu/pc-bios/bios.bin \
       ${startdir}/pkg/usr/share/qemu/bios-kvm.bin
   install -D -m644 ${startdir}/src/kvm-$_kvmver/qemu/pc-bios/vgabios.bin \
       ${startdir}/pkg/usr/share/qemu/vgabios-kvm.bin
   install -D -m644 ${startdir}/src/kvm-$_kvmver/qemu/pc-bios/vgabios-cirrus.bin \
       ${startdir}/pkg/usr/share/qemu/vgabios-cirrus-kvm.bin
   install -D -m644 ${startdir}/src/kvm-$_kvmver/extboot/extboot.bin \
	${startdir}/pkg/usr/share/qemu/extboot-kvm.bin
}
md5sums=('6591df8e9270eb358c881de4ebea1262'
         'ec06591830b8fcf53913f05f3d66f7e5'
         'e4f99d05dee168200695850165cd760e'
         '1cdfcbd3cc569eec96a36d7557291fd2')
