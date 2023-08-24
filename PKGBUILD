# Maintainer: David Runge <dvzrv@archlinux.org>
# Contributor: Tobias Powalowski <tpowa@archlinux.org>
# Contributor: Sébastien "Seblu" Luttringer <seblu@seblu.net>

pkgbase=qemu
pkgname=(
  qemu-common
  qemu-audio-{alsa,dbus,jack,oss,pa,pipewire,sdl,spice}
  qemu-block-{curl,dmg,gluster,iscsi,nfs,ssh}
  qemu-chardev-{baum,spice}
  qemu-docs
  qemu-guest-agent
  qemu-hw-display-{qxl,virtio-{gpu{,-{gl,pci,pci-gl}},vga{,-gl}}}
  qemu-hw-s390x-virtio-gpu-ccw
  qemu-hw-usb-{host,redirect,smartcard}
  qemu-img
  qemu-pr-helper
  qemu-system-{aarch64,alpha,arm,avr,cris,hppa,loongarch64,m68k,microblaze,mips,nios2,or1k,ppc,riscv,rx,s390x,sh4,sparc,tricore,x86,xtensa}
  qemu-system-{alpha,arm,hppa,microblaze,ppc,riscv,s390x,sparc,x86}-firmware
  qemu-tests
  qemu-tools
  qemu-ui-{curses,dbus,egl-headless,gtk,opengl,sdl,spice-{app,core}}
  qemu-user{,-static}{,-binfmt}
  qemu-vhost-user-gpu
  qemu-{base,desktop,emulators-full,full}
)
pkgver=8.1.0
pkgrel=2
pkgdesc="A generic and open source machine emulator and virtualizer"
arch=(x86_64)
url="https://www.qemu.org/"
license=(
  Apache-2.0
  BSD-2-Clause
  BSD-3-Clause
  FSFAP
  GPL-1.0-or-later
  GPL-2.0-only
  GPL-2.0-or-later
  'GPL-2.0-or-later with GCC-exception-2.0 exception'
  LGPL-2.0-only
  LGPL-2.0-or-later
  LGPL-2.1-only
  LGPL-2.1-or-later
  MIT
  public-domain
  CC-BY-3.0
)
# TODO: consider providing rdma-core
# TODO: consider providing lzfse
# TODO: package systemtap
# TODO: package openbios for qemu-system-{ppc,sparc}
# TODO: package /usr/share/qemu/{efi,pxe}-* for qemu (ipxe)
# TODO: package /usr/share/qemu/slof.bin for qemu-system-ppc (slof)
makedepends=(
  alsa-lib
  brltty
  bzip2
  cairo
  capstone
  curl
  dtc
  fuse3
  gcc-libs
  gdk-pixbuf2
  glib2
  glusterfs
  gnutls
  gtk3
  jack
  keyutils
  libaio
  libbpf
  libcacard
  libcap-ng
  libepoxy
  libiscsi
  libnfs
  libpipewire
  libpng
  libpulse
  libsasl
  libseccomp
  libslirp
  libssh
  liburing
  libusb
  libx11
  libxml2
  libxkbcommon
  lzo
  mesa
  meson
  multipath-tools
  ncurses
  ndctl
  numactl
  pam
  pcre2
  python
  python-distlib
  python-setuptools
  python-pip
  python-sphinx
  python-sphinx_rtd_theme
  sdl2
  sdl2_image
  snappy
  spice-protocol
  spice
  systemd
  usbredir
  vde2
  virglrenderer
  vte3
  zlib
  zstd
)
source=(
  https://download.qemu.org/qemu-$pkgver.tar.xz{,.sig}
  bridge.conf
  qemu-ga.conf
  qemu-sysusers.conf
  65-kvm.rules
  99-qemu-guest-agent.rules
  $pkgbase-8.1.0-keyutils.patch
)
sha512sums=('c5f5e7ce2d8e3c93a02012b136c866e8577df07da4705a0045916c71caeaa21fa1b2d59a4b22a660789a4159b192e12a443e7cbb0724ee85fea258251731724c'
            'SKIP'
            '7b412ffa5dcda47b0a4ec9e2c5e5e1d9eaaaf0a087b7ea3ead3e706ba4c9cafb919beadd088a0299b6f7aab753b81a5eafb545b4842ee5f26646d16544dd02a7'
            '6e838773d63ae0ffdffe2b891bf611d8f5f3c67a9bc4cbbedf8363c150c2c9971c8e44d92270bc581af40eb0ece02192760bcdd6aee229fff55635f3a4825afa'
            '985c2c7a6b5217c87a15b45368089ee91b2f9027b070f9eafa448a18b27ae0d9edd964d52e134b9c1f4aeef4d6aae88afd3f454551ca898affef7f9d28b99b8f'
            'bdf05f99407491e27a03aaf845b7cc8acfa2e0e59968236f10ffc905e5e3d5e8569df496fd71c887da2b5b8d1902494520c7da2d3a8258f7fd93a881dd610c99'
            '93b905046fcea8a0a89513b9259c222494ab3b91319dde23baebcb40dc17376a56661b159b99785d6e816831974a0f3cbd7b2f7d89e5fc3c258f88f4492f3839'
            '400cca1177bd72ac1dfe646a2197754a1829116ade02cb4b0dea817f62a62ff3324675f772cdacd58ae74cff6147bf04a249dabb9729df6678500d47f7e728a8')
b2sums=('b0fd87a19b13d4bbc6526caa46533073cb4dee6004df5d4fbbef204ee3bc8c2f10ec1eaff554adbb25c9f3143dd68abd09d4a0519c4766299a3ff261d03c73f2'
        'SKIP'
        'b1eca364aa60f130ff5e649f5d004d3fcb75356d3421a4542efdfc410d39b40d9434d15e1dd7bbdbd315cb72b5290d3ea5f77f9c41961a5601cd28ef7bbe72e8'
        '2102e4a34e11e406e9606c97e026e7b92e887e296a7f77b9cede1b37119d0df33735f3588628167b2b8e32244c196c491bfab623e2caddac9014d445aa2a6d98'
        '69177b962d2fda20cafdbc6226fd017b5ca5a0f69f866d055dc1c744b7b2955059f47c693cfb5b4c863ec159569fdabd4327ab4b8a95566a68cd8ce38e339c7a'
        '3559fe9c4f744194939770047a0a02d07ff791c845a80726d0bc7b8c4801ed5f11150e7d5adab813844b3dab1cf38c3a5a87fb6efbb8fc9dccdda9fa56409ed8'
        'a9a2bdfeeb44eb86cbe88ac7c65f72800bdb2fd5cecb02f3a258cf9470b52832180aab43c89d481f7fd4d067342a9a27dd6c8a94d625b95d6e2b912e47d274e7'
        '3608b43b4751554a7f1ff74ecdb161625bb565b083b471df4e13be0f98b556992f4c707760610b87d02cb5bd11cec5b59a3b4c59024c4a791acfb80f720c2c0e')
validpgpkeys=('CEACC9E15534EBABB82D3FA03353C9CEF108B584') # Michael Roth <flukshun@gmail.com>

_qemu_system_deps=(
  capstone
  dtc
  fuse3
  gcc-libs
  glibc
  glib2 libgio-2.0.so libglib-2.0.so libgmodule-2.0.so
  gnutls
  keyutils
  libaio
  libelf
  libbpf libbpf.so
  libjpeg-turbo libjpeg.so
  libpng
  libsasl
  libseccomp libseccomp.so
  libslirp libslirp.so
  liburing liburing.so
  lzo
  ndctl
  numactl libnuma.so
  pam libpam.so
  pixman libpixman-1.so
  qemu-common=$pkgver-$pkgrel
  snappy
  vde2
  zlib
  zstd libzstd.so
)

_qemu_full_optdepends=(
  'qemu-user-static: for static user mode emulation of QEMU targets'
  'samba: for SMB/CIFS server support'
)

_qemu_desktop_optdepends=(
  "${_qemu_full_optdepends[@]}"
  'qemu-block-gluster: for Gluster block driver'
  'qemu-block-iscsi: for iSCSI block driver'
  'qemu-chardev-baum: for Baum chardev driver'
  'qemu-docs: for documentation'
  'qemu-emulators-full: for all system emulators'
  'qemu-full: for a full QEMU installation'
  'qemu-hw-s390x-virtio-gpu-ccw: for s390x-virtio-gpu-ccw display device'
  'qemu-pr-helper: for persistent reservation utility'
  'qemu-system-aarch64: for AARCH64 system emulator'
  'qemu-system-alpha: for Alpha system emulator'
  'qemu-system-arm: for ARM system emulator'
  'qemu-system-avr: for AVR system emulator'
  'qemu-system-cris: for CRIS system emulator'
  'qemu-system-hppa: for HPPA system emulator'
  'qemu-system-m68k: for ColdFire (m68k) system emulator'
  'qemu-system-microblaze: for Microblaze system emulator'
  'qemu-system-mips: for MIPS system emulator'
  'qemu-system-nios2: for nios2 system emulator'
  'qemu-system-or1k: for OpenRisc32 system emulator'
  'qemu-system-ppc: for PPC system emulator'
  'qemu-system-riscv: for RISC-V system emulator'
  'qemu-system-rx: for RX system emulator'
  'qemu-system-s390x: for S390 system emulator'
  'qemu-system-sh4: for SH4 system emulator'
  'qemu-system-sparc: for SPARC system emulator'
  'qemu-system-tricore: for tricore system emulator'
  'qemu-system-xtensa: for Xtensa system emulator'
  'qemu-tests: for QEMU tests'
  'qemu-tools: for QEMU tools'
  'qemu-user: for user mode emulation of QEMU targets'
)

_qemu_base_optdepends=(
  "${_qemu_desktop_optdepends[@]}"
  'qemu-audio-alsa: for ALSA audio driver'
  'qemu-audio-dbus: for D-Bus audio driver'
  'qemu-audio-jack: for JACK audio driver'
  'qemu-audio-oss: for OSS audio driver'
  'qemu-audio-pa: for PulseAudio audio driver'
  'qemu-audio-pipewire: for PipeWire audio driver'
  'qemu-audio-sdl: for SDL audio driver'
  'qemu-audio-spice: for spice audio driver'
  'qemu-block-curl: for curl block driver'
  'qemu-block-dmg: for DMG block driver'
  'qemu-block-nfs: for NFS block driver'
  'qemu-block-ssh: for SSH block driver'
  'qemu-chardev-spice: for the spice chardev driver'
  'qemu-desktop: for dependencies commonly used on a desktop'
  'qemu-hw-display-qxl: for the QXL display device'
  'qemu-hw-display-virtio-vga: for the virtio-vga display device'
  'qemu-hw-display-virtio-vga-gl: for the virtio-vga-gl display device'
  'qemu-hw-display-virtio-gpu: for the virtio-gpu display device'
  'qemu-hw-display-virtio-gpu-gl: for the virtio-gpu-gl display device'
  'qemu-hw-display-virtio-gpu-pci: for the virtio-gpu-pci display device'
  'qemu-hw-display-virtio-gpu-pci-gl: for the virtio-gpu-pci-gl display device'
  'qemu-hw-usb-host: for host USB support'
  'qemu-hw-usb-redirect: for USB redirect support'
  'qemu-hw-usb-smartcard: for USB smartcard support'
  'qemu-ui-curses: for ncurses UI driver'
  'qemu-ui-dbus: for D-Bus UI driver'
  'qemu-ui-egl-headless: for EGL headless UI driver'
  'qemu-ui-gtk: for GTK UI driver'
  'qemu-ui-opengl: for OpenGL UI driver'
  'qemu-ui-sdl: for SDL UI driver'
  'qemu-ui-spice-app: for spice app UI driver'
  'qemu-ui-spice-core: for spice core UI driver'
  'qemu-user: for user mode emulation of QEMU targets'
  'qemu-vhost-user-gpu: for vhost-user-gpu display device'
)

_pick() {
  local p="$1" f d; shift
  for f; do
    d="$srcdir/$p/${f#$pkgdir/}"
    mkdir -vp "$(dirname "$d")"
    mv -v "$f" "$d"
    rmdir -vp --ignore-fail-on-non-empty "$(dirname "$f")"
  done
}

prepare() {

  # fix detection of keyutils: https://gitlab.com/qemu-project/qemu/-/issues/1842
  patch -Np1 -d $pkgbase-$pkgver -i ../$pkgbase-8.1.0-keyutils.patch

  # extract licenses for TCG
  sed -n '1,23p' $pkgbase-$pkgver/tcg/tcg-internal.h > tcg.LICENSE.MIT
  sed -n '1,23p' $pkgbase-$pkgver/tcg/arm/tcg-target.c.inc > tcg-arm.LICENSE.MIT
  sed -n '1,23p' $pkgbase-$pkgver/tcg/tci/tcg-target.h > tci.LICENSE.MIT

  # install qemu-pr-helper.socket to sockets.target
  sed -e 's/multi-user.target/sockets.target/g' -i $pkgbase-$pkgver/contrib/systemd/qemu-pr-helper.socket

  # create build dir
  mkdir -vp build
  mkdir -vp build-static
}

build() {
  local common_configure_options=(
    --prefix=/usr
    --sysconfdir=/etc
    --libexecdir=/usr/lib/qemu
    --localstatedir=/var
    --docdir=/usr/share/doc/qemu
  )
  local configure_options=(
    "${common_configure_options[@]}"
    --enable-modules
    --enable-sdl
    --enable-slirp
    --enable-tpm
    --smbd=/usr/bin/smbd
    --with-coroutine=ucontext
  )
  local configure_static_options=(
    "${common_configure_options[@]}"
    --enable-attr
    --enable-linux-user
    --enable-tcg
    --disable-bpf
    --disable-bsd-user
    --disable-capstone
    --disable-docs
    --disable-fdt
    --disable-gcrypt
    --disable-glusterfs
    --disable-gnutls
    --disable-gtk
    --disable-install-blobs
    --disable-kvm
    --disable-libiscsi
    --disable-libnfs
    --disable-libssh
    --disable-linux-io-uring
    --disable-nettle
    --disable-opengl
    --disable-qom-cast-debug
    --disable-sdl
    --disable-system
    --disable-tools
    --disable-tpm
    --disable-vde
    --disable-vhost-crypto
    --disable-vhost-kernel
    --disable-vhost-net
    --disable-vhost-user
    --disable-vnc
    --disable-werror
    --disable-xen
    --disable-zstd
    --static
  )

  (
    cd build-static
    ../$pkgbase-$pkgver/configure "${configure_static_options[@]}"
    ninja
  )

  # Build only minimal debug info to reduce size
  CFLAGS+=' -g1'
  CXXFLAGS+=' -g1'

  (
    cd build
    ../$pkgbase-$pkgver/configure "${configure_options[@]}"
    ninja
  )

}

package_qemu-common() {
  local binfmt_conf_options=(
    --systemd ALL
    --exportdir "$pkgdir/usr/lib/binfmt.d/"
    --qemu-path "/usr/bin"
    --persistent yes
    --preserve-argv0 yes
  )

  depends=(gcc-libs glibc glib2 libglib-2.0.so libgmodule-2.0.so hicolor-icon-theme libcap-ng libcap-ng.so numactl libnuma.so)
  backup=(
    etc/$pkgbase/bridge.conf
    etc/sasl2/$pkgbase.conf
  )
  install=$pkgname.install

  # install static binaries
  meson install -C build-static --destdir "$pkgdir"
  install -vdm 755 "$pkgdir/usr/lib/binfmt.d/"
  $pkgbase-$pkgver/scripts/qemu-binfmt-conf.sh "${binfmt_conf_options[@]}"

  # rename static binaries to prevent name conflicts
  for _src in "$pkgdir/usr/bin/qemu-"*; do
    mv -v "$_src" "$pkgdir/usr/bin/$(basename "$_src")-static"
  done
  # modify and rename binfmt.d configs to prevent name conflicts
  for _conf in "$pkgdir/usr/lib/binfmt.d/"*; do
    _exe_name="$(basename "${_conf/.conf/}")"
    _new_exe_name="${_exe_name}-static"
    _new_conf_name="${_conf/.conf/-static.conf}"
    sed -e "s|usr/bin/${_exe_name}|usr/bin/${_new_exe_name}|" "$_conf" > "${_new_conf_name}"
  done

  # install default binaries
  meson install -C build --destdir "$pkgdir"

  install -vdm 755 "$pkgdir/usr/lib/binfmt.d/"
  $pkgbase-$pkgver/scripts/qemu-binfmt-conf.sh "${binfmt_conf_options[@]}"

  install -vDm 644 bridge.conf -t "$pkgdir/etc/$pkgbase/"
  install -vDm 644 $pkgbase-$pkgver/$pkgbase.sasl "$pkgdir/etc/sasl2/$pkgbase.conf"
  install -vDm 644 $pkgbase-$pkgver/LICENSE *LICENSE* -t "$pkgdir/usr/share/licenses/$pkgbase/"
  install -vDm 644 $pkgbase-sysusers.conf "$pkgdir/usr/lib/sysusers.d/$pkgbase.conf"

  # bridge_helper needs suid: https://bugs.archlinux.org/task/32565
  chmod u+s "$pkgdir/usr/lib/qemu/qemu-bridge-helper"

  # remoe invalid directory
  rm -frv "$pkgdir/var"

  # remove unneeded files
  find "$pkgdir" -name .buildinfo -delete

  # remove files provided by seabios
  rm -fv "$pkgdir/usr/share/$pkgbase/"{bios,vgabios}*

  # remove files provided by edk2-{aarch64,arm,ovmf}
  rm -fv "$pkgdir/usr/share/$pkgbase/"edk2-*
  rm -frv "$pkgdir/usr/share/$pkgbase/firmware"

  (
    # create man page symlinks for all system emulators
    cd "$pkgdir/usr/share/man/man1"
    for _name in qemu-system-{aarch64,alpha,arm,avr,cris,hppa,i386,loongarch64,m68k,microblaze{,el},mips{,64,64el,el},nios2,or1k,ppc{,64},riscv{32,64},rx,s390x,sh4{,eb},sparc{,64},tricore,x86_64,xtensa{,eb}}; do
      ln -sv $pkgbase.1.gz "$pkgdir/usr/share/man/man1/$_name.1.gz"
    done
  )

  (
    # pick files for all split packages
    cd "$pkgdir"

    _pick qemu-guest-agent usr/bin/qemu-ga
    _pick qemu-guest-agent usr/share/man/man8/qemu-ga.8*

    _pick qemu-audio-alsa usr/lib/qemu/audio-alsa.so
    _pick qemu-audio-dbus usr/lib/qemu/audio-dbus.so
    _pick qemu-audio-jack usr/lib/qemu/audio-jack.so
    _pick qemu-audio-oss usr/lib/qemu/audio-oss.so
    _pick qemu-audio-pa usr/lib/qemu/audio-pa.so
    _pick qemu-audio-pipewire usr/lib/qemu/audio-pipewire.so
    _pick qemu-audio-sdl usr/lib/qemu/audio-sdl.so
    _pick qemu-audio-spice usr/lib/qemu/audio-spice.so

    _pick qemu-block-curl usr/lib/qemu/block-curl.so
    _pick qemu-block-dmg usr/lib/qemu/block-dmg*.so
    _pick qemu-block-gluster usr/lib/qemu/block-gluster.so
    _pick qemu-block-iscsi usr/lib/qemu/block-iscsi.so
    _pick qemu-block-nfs usr/lib/qemu/block-nfs.so
    _pick qemu-block-ssh usr/lib/qemu/block-ssh.so

    _pick qemu-chardev-baum usr/lib/qemu/chardev-baum.so
    _pick qemu-chardev-spice usr/lib/qemu/chardev-spice.so

    _pick qemu-docs usr/share/doc/qemu

    _pick qemu-hw-display-qxl usr/lib/qemu/hw-display-qxl.so
    _pick qemu-hw-display-virtio-gpu usr/lib/qemu/hw-display-virtio-gpu.so
    _pick qemu-hw-display-virtio-gpu-gl usr/lib/qemu/hw-display-virtio-gpu-gl.so
    _pick qemu-hw-display-virtio-gpu-pci usr/lib/qemu/hw-display-virtio-gpu-pci.so
    _pick qemu-hw-display-virtio-gpu-pci-gl usr/lib/qemu/hw-display-virtio-gpu-pci-gl.so
    _pick qemu-hw-display-virtio-vga usr/lib/qemu/hw-display-virtio-vga.so
    _pick qemu-hw-display-virtio-vga-gl usr/lib/qemu/hw-display-virtio-vga-gl.so

    _pick qemu-hw-usb-host usr/lib/qemu/hw-usb-host.so
    _pick qemu-hw-usb-redirect usr/lib/qemu/hw-usb-redirect.so
    _pick qemu-hw-usb-smartcard usr/lib/qemu/hw-usb-smartcard.so

    _pick qemu-img usr/bin/qemu-{img,io,nbd,storage-daemon}
    _pick qemu-img usr/share/man/man1/qemu-{img,storage-daemon}.1*
    _pick qemu-img usr/share/man/man7/qemu-storage-daemon-qmp-ref.7*
    _pick qemu-img usr/share/man/man8/qemu-nbd.8*

    _pick qemu-pr-helper usr/bin/qemu-pr-helper
    _pick qemu-pr-helper usr/share/man/man8/qemu-pr-helper.8*

    _pick qemu-hw-s390x-virtio-gpu-ccw usr/lib/qemu/hw-s390x-virtio-gpu-ccw.so

    _pick qemu-system-aarch64 usr/bin/qemu-system-aarch64
    _pick qemu-system-aarch64 usr/share/man/man1/qemu-system-aarch64.1*

    _pick qemu-system-alpha usr/bin/qemu-system-alpha
    _pick qemu-system-alpha usr/share/man/man1/qemu-system-alpha.1*

    _pick qemu-system-alpha-firmware usr/share/qemu/palcode-clipper

    _pick qemu-system-arm usr/bin/qemu-system-arm
    _pick qemu-system-arm usr/share/man/man1/qemu-system-arm.1*

    _pick qemu-system-arm-firmware usr/share/qemu/npcm7xx_bootrom.bin

    _pick qemu-system-avr usr/bin/qemu-system-avr
    _pick qemu-system-avr usr/share/man/man1/qemu-system-avr.1*

    _pick qemu-system-cris usr/bin/qemu-system-cris
    _pick qemu-system-cris usr/share/man/man1/qemu-system-cris.1*

    _pick qemu-system-hppa usr/bin/qemu-system-hppa
    _pick qemu-system-hppa usr/share/man/man1/qemu-system-hppa.1*

    _pick qemu-system-hppa-firmware usr/share/qemu/hppa-firmware.img

    _pick qemu-system-loongarch64 usr/bin/qemu-system-loongarch64
    _pick qemu-system-loongarch64 usr/share/man/man1/qemu-system-loongarch64.1*

    _pick qemu-system-m68k usr/bin/qemu-system-m68k
    _pick qemu-system-m68k usr/share/man/man1/qemu-system-m68k.1*

    _pick qemu-system-microblaze usr/bin/qemu-system-microblaze{,el}
    _pick qemu-system-microblaze usr/share/man/man1/qemu-system-microblaze{,el}.1*

    _pick qemu-system-microblaze-firmware usr/share/qemu/petalogix-*.dtb

    _pick qemu-system-mips usr/bin/qemu-system-mips{,64,64el,el}
    _pick qemu-system-mips usr/share/man/man1/qemu-system-mips{,64,64el,el}.1*

    _pick qemu-system-nios2 usr/bin/qemu-system-nios2
    _pick qemu-system-nios2 usr/share/man/man1/qemu-system-nios2.1*

    _pick qemu-system-or1k usr/bin/qemu-system-or1k
    _pick qemu-system-or1k usr/share/man/man1/qemu-system-or1k.1*

    _pick qemu-system-ppc usr/bin/qemu-system-ppc{,64}
    _pick qemu-system-ppc usr/share/man/man1/qemu-system-ppc{,64}.1*

    _pick qemu-system-ppc-firmware usr/share/qemu/{bamboo,canyonlands}.dtb
    # NOTE: needs to be replaced by openbios
    _pick qemu-system-ppc-firmware usr/share/qemu/openbios-ppc
    _pick qemu-system-ppc-firmware usr/share/qemu/qemu_vga.ndrv
    _pick qemu-system-ppc-firmware usr/share/qemu/skiboot.lid
    # NOTE: needs to be replaced by slof
    _pick qemu-system-ppc-firmware usr/share/qemu/slof.bin
    _pick qemu-system-ppc-firmware usr/share/qemu/u-boot.e500
    _pick qemu-system-ppc-firmware usr/share/qemu/u-boot-sam460-20100605.bin

    _pick qemu-system-riscv usr/bin/qemu-system-riscv{32,64}
    _pick qemu-system-riscv usr/share/man/man1/qemu-system-riscv{32,64}.1*

    _pick qemu-system-riscv-firmware usr/share/qemu/opensbi-riscv{32,64}*.bin

    _pick qemu-system-rx usr/bin/qemu-system-rx
    _pick qemu-system-rx usr/share/man/man1/qemu-system-rx.1*

    _pick qemu-system-s390x usr/bin/qemu-system-s390x
    _pick qemu-system-s390x usr/share/man/man1/qemu-system-s390x.1*

    _pick qemu-system-s390x-firmware usr/share/qemu/s390-{ccw,netboot}.img

    _pick qemu-system-sh4 usr/bin/qemu-system-sh4{,eb}
    _pick qemu-system-sh4 usr/share/man/man1/qemu-system-sh4{,eb}.1*

    _pick qemu-system-sparc usr/bin/qemu-system-sparc{,64}
    _pick qemu-system-sparc usr/share/man/man1/qemu-system-sparc{,64}.1*

    # NOTE: needs to be replaced by openbios
    _pick qemu-system-sparc-firmware usr/share/qemu/openbios-sparc{32,64}
    _pick qemu-system-sparc-firmware usr/share/qemu/QEMU,{cgthree,tcx}.bin

    _pick qemu-system-tricore usr/bin/qemu-system-tricore
    _pick qemu-system-tricore usr/share/man/man1/qemu-system-tricore.1*

    _pick qemu-system-x86 usr/bin/qemu-system-{i386,x86_64}
    _pick qemu-system-x86 usr/lib/qemu/accel-tcg-{i386,x86_64}.so
    _pick qemu-system-x86 usr/share/man/man1/qemu-system-{i386,x86_64}.1*

    _pick qemu-system-x86-firmware usr/share/qemu/{kvmvapic,linuxboot,multiboot{,_dma},pvh}.bin
    _pick qemu-system-x86-firmware usr/share/qemu/qboot.rom

    _pick qemu-system-xtensa usr/bin/qemu-system-xtensa{,eb}
    _pick qemu-system-xtensa usr/share/man/man1/qemu-system-xtensa{,eb}.1*

    _pick qemu-tests usr/lib/qemu/accel-qtest-*.so

    _pick qemu-tools usr/bin/{elf2dmp,qemu-{edid,keymap}}
    _pick qemu-tools usr/share/qemu/trace-events-all

    _pick qemu-ui-curses usr/lib/qemu/ui-curses.so
    _pick qemu-ui-dbus usr/lib/qemu/ui-dbus.so
    _pick qemu-ui-egl-headless usr/lib/qemu/ui-egl-headless.so
    _pick qemu-ui-gtk usr/lib/qemu/ui-gtk.so
    _pick qemu-ui-opengl usr/lib/qemu/ui-opengl.so
    _pick qemu-ui-sdl usr/lib/qemu/ui-sdl.so
    _pick qemu-ui-spice-app usr/lib/qemu/ui-spice-app.so
    _pick qemu-ui-spice-core usr/lib/qemu/ui-spice-core.so

    _pick qemu-user-static usr/bin/qemu-*-static
    _pick qemu-user-static-binfmt usr/lib/binfmt.d/*-static.conf

    _pick qemu-user usr/bin/qemu-{aarch64{,_be},alpha,arm{,eb},cris,hexagon,hppa,i386,loongarch64,m68k,microblaze{,el},mips{,64,64el,el,n32,n32el},nios2,or1k,ppc{,64,64le},riscv{32,64},s390x,sh4{,eb},sparc{,32plus,64},x86_64,xtensa{,eb}}
    _pick qemu-user-binfmt usr/lib/binfmt.d/*.conf

    _pick qemu-vhost-user-gpu usr/lib/qemu/vhost-user-gpu
    _pick qemu-vhost-user-gpu usr/share/qemu/vhost-user/50-qemu-gpu.json
  )
}

package_qemu-audio-alsa() {
  pkgdesc="QEMU ALSA audio driver"
  depends=(alsa-lib libasound.so glibc qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-audio-dbus() {
  pkgdesc="QEMU D-Bus audio driver"
  depends=(gcc-libs glib2 libgio-2.0.so libgobject-2.0.so libglib-2.0.so glibc qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-audio-jack() {
  pkgdesc="QEMU JACK audio driver"
  depends=(glibc jack libjack.so qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-audio-oss() {
  pkgdesc="QEMU OSS audio driver"
  depends=(glibc qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-audio-pa() {
  pkgdesc="QEMU PulseAudio audio driver"
  depends=(glibc libpulse libpulse.so qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-audio-pipewire() {
  pkgdesc="QEMU PipeWire audio driver"
  depends=(gcc-libs glibc libpipewire libpipewire-0.3.so qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-audio-sdl() {
  pkgdesc="QEMU SDL audio driver"
  depends=(glibc qemu-common=$pkgver-$pkgrel sdl2)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-audio-spice() {
  pkgdesc="QEMU spice audio driver"
  depends=(glibc qemu-common=$pkgver-$pkgrel qemu-ui-spice-core=$pkgver-$pkgrel spice libspice-server.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-block-curl() {
  pkgdesc="QEMU curl block driver"
  depends=(curl libcurl.so gcc-libs glibc qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-block-dmg() {
  pkgdesc="QEMU DMG block driver"
  depends=(bzip2 libbz2.so glibc qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-block-gluster() {
  pkgdesc="QEMU Gluster block driver"
  depends=(glibc glusterfs qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-block-iscsi() {
  pkgdesc="QEMU iSCSI block driver"
  depends=(gcc-libs glibc libiscsi qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-block-nfs() {
  pkgdesc="QEMU NFS block driver"
  depends=(gcc-libs glibc libnfs qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-block-ssh() {
  pkgdesc="QEMU SSH block driver"
  depends=(gcc-libs glibc libssh libssh.so qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-chardev-baum() {
  pkgdesc="QEMU Baum chardev driver"
  depends=(brltty libbrlapi.so gcc-libs glibc qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-chardev-spice() {
  pkgdesc="QEMU spice chardev driver"
  depends=(glibc qemu-common=$pkgver-$pkgrel qemu-ui-spice-core=$pkgver-$pkgrel spice libspice-server.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-docs() {
  pkgdesc+=" - documentation"
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-guest-agent() {
  pkgdesc="QEMU Guest Agent"
  depends=(gcc-libs glib2 libglib-2.0.so libgmodule-2.0.so glibc liburing liburing.so numactl libnuma.so sh systemd-libs libudev.so)
  backup=(
    etc/$pkgbase/$pkgbase-ga.conf
    etc/$pkgbase/fsfreeze-hook
  )
  install=$pkgname.install
  mv -v $pkgname/* "$pkgdir"
  install -vDm 644 $pkgbase-$pkgver/contrib/systemd/$pkgname.service -t "$pkgdir/usr/lib/systemd/system/"
  install -vDm 644 99-$pkgname.rules -t "$pkgdir/usr/lib/udev/rules.d/"
  install -vDm 644 $pkgbase-ga.conf -t "$pkgdir/etc/$pkgbase/"
  install -vDm 755 $pkgbase-$pkgver/scripts/$pkgname/fsfreeze-hook -t "$pkgdir/etc/$pkgbase/"
  install -vdm 755 "$pkgdir/etc/$pkgbase/fsfreeze-hook.d"
}

package_qemu-hw-display-qxl() {
  pkgdesc="QEMU QXL display device"
  depends=(gcc-libs glibc pixman libpixman-1.so qemu-common=$pkgver-$pkgrel qemu-ui-spice-core=$pkgver-$pkgrel spice libspice-server.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-display-virtio-gpu() {
  pkgdesc="QEMU virtio-gpu display device"
  depends=(glibc pixman libpixman-1.so qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-display-virtio-gpu-gl() {
  pkgdesc="QEMU virtio-gpu-gl display device"
  depends=(glibc qemu-common=$pkgver-$pkgrel virglrenderer)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-display-virtio-gpu-pci() {
  pkgdesc="QEMU virtio-gpu-pci display device"
  depends=(qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-display-virtio-gpu-pci-gl() {
  pkgdesc="QEMU virtio-gpu-pci-gl display device"
  depends=(qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-display-virtio-vga() {
  pkgdesc="QEMU virtio-vga display device"
  depends=(qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-display-virtio-vga-gl() {
  pkgdesc="QEMU virtio-vga-gl display device"
  depends=(qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-s390x-virtio-gpu-ccw() {
  pkgdesc="QEMU s390x-virtio-gpu-ccw display device"
  depends=(qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-aarch64() {
  pkgdesc="QEMU system emulator for AARCH64"
  depends=("${_qemu_system_deps[@]}" edk2-aarch64 systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-alpha() {
  pkgdesc="QEMU system emulator for Alpha"
  depends=("${_qemu_system_deps[@]}" qemu-system-alpha-firmware=$pkgver-$pkgrel systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-alpha-firmware() {
  pkgdesc="Firmware for QEMU system emulator for Alpha"
  options=(!strip)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-arm() {
  pkgdesc="QEMU system emulator for ARM"
  depends=("${_qemu_system_deps[@]}" edk2-arm qemu-system-arm-firmware=$pkgver-$pkgrel systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-arm-firmware() {
  pkgdesc="Firmware for QEMU system emulator for ARM"
  options=(!strip)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-avr() {
  pkgdesc="QEMU system emulator for AVR"
  depends=("${_qemu_system_deps[@]}")
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-cris() {
  pkgdesc="QEMU system emulator for CRIS"
  depends=("${_qemu_system_deps[@]}")
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-hppa() {
  pkgdesc="QEMU system emulator for HPPA"
  depends=("${_qemu_system_deps[@]}" qemu-system-hppa-firmware=$pkgver-$pkgrel systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-hppa-firmware() {
  pkgdesc="Firmware for QEMU system emulator for HPPA"
  options=(!strip)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-loongarch64() {
  pkgdesc="QEMU system emulator for LoongArch64"
  depends=("${_qemu_system_deps[@]}" systemd-libs)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-m68k() {
  pkgdesc="QEMU system emulator for ColdFire (m68k)"
  depends=("${_qemu_system_deps[@]}")
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-microblaze() {
  pkgdesc="QEMU system emulator for Microblaze"
  depends=("${_qemu_system_deps[@]}" qemu-system-microblaze-firmware=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-microblaze-firmware() {
  pkgdesc="Firmware for QEMU system emulator for Microblaze"
  options=(!strip)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-mips() {
  pkgdesc="QEMU system emulator for MIPS"
  depends=("${_qemu_system_deps[@]}" systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-nios2() {
  pkgdesc="QEMU system emulator for nios2"
  depends=("${_qemu_system_deps[@]}")
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-or1k() {
  pkgdesc="QEMU system emulator for OpenRisc32"
  depends=("${_qemu_system_deps[@]}" systemd-libs)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-ppc() {
  pkgdesc="QEMU system emulator for PPC"
  depends=("${_qemu_system_deps[@]}" qemu-system-ppc-firmware=$pkgver-$pkgrel systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-ppc-firmware() {
  pkgdesc="Firmware for QEMU system emulator for PPC"
  options=(!strip)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-riscv() {
  pkgdesc="QEMU system emulator for RISC-V"
  depends=("${_qemu_system_deps[@]}" qemu-system-riscv-firmware=$pkgver-$pkgrel systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-riscv-firmware() {
  pkgdesc="Firmware for QEMU system emulator for RISC-V"
  options=(!strip)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-rx() {
  pkgdesc="QEMU system emulator for RX"
  depends=("${_qemu_system_deps[@]}")
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-s390x() {
  pkgdesc="QEMU system emulator for S390"
  depends=("${_qemu_system_deps[@]}" qemu-system-s390x-firmware=$pkgver-$pkgrel systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-s390x-firmware() {
  pkgdesc="Firmware for QEMU system emulator for S390"
  options=(!strip)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-sh4() {
  pkgdesc="QEMU system emulator for SH4"
  depends=("${_qemu_system_deps[@]}" systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-sparc() {
  pkgdesc="QEMU system emulator for SPARC"
  depends=("${_qemu_system_deps[@]}" qemu-system-sparc-firmware=$pkgver-$pkgrel systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-sparc-firmware() {
  pkgdesc="Firmware for QEMU system emulator for SPARC"
  options=(!strip)
  # NOTE: will require openbios
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-tricore() {
  pkgdesc="QEMU system emulator for tricore"
  depends=("${_qemu_system_deps[@]}")
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-x86() {
  pkgdesc="QEMU system emulator for x86"
  depends=("${_qemu_system_deps[@]}" edk2-ovmf qemu-system-x86-firmware=$pkgver-$pkgrel seabios systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-x86-firmware() {
  pkgdesc="Firmware for QEMU system emulator for x86"
  options=(!strip)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-system-xtensa() {
  pkgdesc="QEMU system emulator for Xtensa"
  depends=("${_qemu_system_deps[@]}" systemd-libs libudev.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-usb-host() {
  pkgdesc="QEMU USB host device"
  depends=(glibc libusb libusb-1.0.so qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-usb-redirect() {
  pkgdesc="QEMU usbredir device"
  depends=(gcc-libs glibc qemu-common=$pkgver-$pkgrel usbredir)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-hw-usb-smartcard() {
  pkgdesc="QEMU USB smartcard device"
  depends=(gcc-libs libcacard glib2 libglib-2.0.so glibc qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-img() {
  pkgdesc="QEMU tooling for manipulating disk images"
  depends=(fuse3 gcc-libs glib2 libglib-2.0.so libgmodule-2.0.so glibc gnutls libaio liburing liburing.so numactl libnuma.so pam libpam.so zlib zstd libzstd.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-pr-helper() {
  pkgdesc="QEMU persistent reservation utility"
  depends=(gcc-libs glib2 libglib-2.0.so libgmodule-2.0.so glibc gnutls libcap-ng libcap-ng.so liburing liburing.so multipath-tools numactl libnuma.so pam libpam.so qemu-common=$pkgver-$pkgrel systemd-libs)
  mv -v $pkgname/* "$pkgdir"
  install -vDm 644 $pkgbase-$pkgver/contrib/systemd/$pkgname.{service,socket} -t "$pkgdir/usr/lib/systemd/system/"
}

package_qemu-tests() {
  pkgdesc="QEMU tests"
  depends=(qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-tools() {
  pkgdesc="QEMU tools"
  depends=(curl libcurl.so gcc-libs glib2 libglib-2.0.so libgmodule-2.0.so glibc libxkbcommon libxkbcommon.so numactl libnuma.so python qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
  install -vDm 644 $pkgbase-$pkgver/scripts/dump-guest-memory.py -t "$pkgdir/usr/share/$pkgbase/"
  install -vDm 755 $pkgbase-$pkgver/scripts/simpletrace.py -t "$pkgdir/usr/share/$pkgbase/"
  install -vDm 644 $pkgbase-$pkgver/scripts/tracetool/*.py -t "$pkgdir/usr/share/$pkgbase/tracetool/"
  install -vDm 644 $pkgbase-$pkgver/scripts/tracetool/backend/*.py -t "$pkgdir/usr/share/$pkgbase/tracetool/backend/"
  install -vDm 644 $pkgbase-$pkgver/scripts/tracetool/format/*.py -t "$pkgdir/usr/share/$pkgbase/tracetool/format/"
}

package_qemu-ui-curses() {
  pkgdesc="QEMU curses UI driver"
  depends=(gcc-libs glib2 libglib-2.0.so glibc ncurses libncursesw.so qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-ui-dbus() {
  pkgdesc="QEMU D-Bus UI driver"
  depends=(gcc-libs glib2 libgio-2.0.so libgobject-2.0.so libglib-2.0.so glibc libepoxy pixman libpixman-1.so qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-ui-egl-headless() {
  pkgdesc="QEMU EGL headless UI driver"
  depends=(glibc libepoxy qemu-common=$pkgver-$pkgrel qemu-ui-opengl=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-ui-gtk() {
  pkgdesc="QEMU GTK UI driver"
  depends=(
    cairo
    gdk-pixbuf2 libgdk_pixbuf-2.0.so
    glib2 libgobject-2.0.so libglib-2.0.so
    glibc
    gtk3 libgdk-3.so libgtk-3.so
    libepoxy
    libx11
    pixman libpixman-1.so
    qemu-common=$pkgver-$pkgrel
    qemu-ui-opengl
    vte3 libvte-2.91.so
  )
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-ui-opengl() {
  pkgdesc="QEMU OpenGL UI driver"
  depends=(gcc-libs glibc libepoxy mesa pixman libpixman-1.so qemu-common=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-ui-sdl() {
  pkgdesc="QEMU SDL UI driver"
  depends=(glib2 libglib-2.0.so glibc libx11 pixman libpixman-1.so qemu-common=$pkgver-$pkgrel sdl2_image sdl2)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-ui-spice-app() {
  pkgdesc="QEMU spice app UI driver"
  depends=(glib2 libgio-2.0.so libglib-2.0.so glibc qemu-common=$pkgver-$pkgrel qemu-chardev-spice=$pkgver-$pkgrel qemu-ui-spice-core=$pkgver-$pkgrel)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-ui-spice-core() {
  pkgdesc="QEMU spice core UI driver"
  depends=(gcc-libs glibc pixman libpixman-1.so qemu-common=$pkgver-$pkgrel qemu-ui-opengl=$pkgver-$pkgrel spice libspice-server.so)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-user() {
  pkgdesc="QEMU user mode emulation"
  depends=(capstone gcc-libs glib2 libglib-2.0.so libgmodule-2.0.so glibc gnutls libelf liburing liburing.so numactl libnuma.so qemu-common=$pkgver-$pkgrel zlib)
  optdepends=('qemu-user-binfmt: for binary format rules')
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-user-binfmt() {
  pkgdesc="Binary format rules for QEMU user mode emulation"
  depends=(qemu-user=$pkgver-$pkgrel)
  provides=(qemu-user-binfmt-provider)
  conflicts=(qemu-user-binfmt-provider)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-user-static() {
  pkgdesc="QEMU static user mode emulation"
  optdepends=('qemu-user-static-binfmt: for binary format rules')
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-user-static-binfmt() {
  pkgdesc="Binary format rules for QEMU static user mode emulation"
  depends=(qemu-user-static=$pkgver-$pkgrel)
  provides=(qemu-user-binfmt-provider)
  conflicts=(qemu-user-binfmt-provider)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-vhost-user-gpu() {
  pkgdesc="QEMU vhost-user-gpu display device"
  depends=(gcc-libs glib2 libglib-2.0.so libgmodule-2.0.so glibc pixman libepoxy libpixman-1.so mesa numactl libnuma.so qemu-common=$pkgver-$pkgrel virglrenderer)
  mv -v $pkgname/* "$pkgdir"
}

package_qemu-base() {
  pkgdesc="A basic QEMU setup for headless environments"
  depends=(
    qemu-common=$pkgver-$pkgrel
    qemu-img=$pkgver-$pkgrel
    qemu-system-x86=$pkgver-$pkgrel
    virtiofsd
  )
  optdepends=("${_qemu_base_optdepends[@]}")
  provides=(qemu=$pkgver)
}

package_qemu-desktop() {
  pkgdesc="A QEMU setup for desktop environments"
  depends=(
    qemu-base=$pkgver-$pkgrel
    qemu-audio-{alsa,dbus,jack,oss,pa,pipewire,sdl,spice}=$pkgver-$pkgrel
    qemu-block-{curl,dmg,nfs,ssh}=$pkgver-$pkgrel
    qemu-chardev-spice=$pkgver-$pkgrel
    qemu-hw-display-{qxl,virtio-gpu{,-{gl,pci,pci-gl}}}=$pkgver-$pkgrel
    qemu-hw-display-virtio-vga{,-gl}=$pkgver-$pkgrel
    qemu-hw-usb-{host,redirect,smartcard}=$pkgver-$pkgrel
    qemu-ui-{curses,dbus,egl-headless,gtk,opengl,sdl,spice-{app,core}}=$pkgver-$pkgrel
    qemu-vhost-user-gpu=$pkgver-$pkgrel
  )
  optdepends=("${_qemu_desktop_optdepends[@]}")
  provides=(qemu=$pkgver)
}

package_qemu-emulators-full() {
  pkgdesc="All QEMU user mode and system emulators"
  depends=(
    qemu-system-{aarch64,alpha,arm,avr,cris,hppa,loongarch64,m68k,microblaze,mips,nios2,or1k,ppc,riscv,rx,s390x,sh4,sparc,tricore,x86,xtensa}=$pkgver-$pkgrel
    qemu-user=$pkgver-$pkgrel
  )
}

package_qemu-full() {
  pkgdesc="A full QEMU setup"
  depends=(
    qemu-audio-{alsa,dbus,jack,oss,pa,sdl,spice}=$pkgver-$pkgrel
    qemu-block-{gluster,iscsi}=$pkgver-$pkgrel
    qemu-chardev-baum=$pkgver-$pkgrel
    qemu-desktop=$pkgver-$pkgrel
    qemu-docs=$pkgver-$pkgrel
    qemu-emulators-full=$pkgver-$pkgrel
    qemu-hw-s390x-virtio-gpu-ccw=$pkgver-$pkgrel
    qemu-pr-helper=$pkgver-$pkgrel
    qemu-tests=$pkgver-$pkgrel
    qemu-tools=$pkgver-$pkgrel
    qemu-user=$pkgver-$pkgrel
  )
  optdepends=("${_qemu_full_optdepends[@]}")
  provides=(qemu=$pkgver)
}

# vim:set ts=2 sw=2 et:
