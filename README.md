# arch-pkg-qemu-hdadump
A modified version of the `qemu` packaging script from Arch Linux that incorporates [@jcs](https://github.com/jcs)'s patches for QEMU, allowing for the intercept of communication between the guest OS and VFIO pass-through audio hardware via the [CORB and RIRB mechanisms](https://wiki.osdev.org/Intel_High_Definition_Audio). Useful for understanding the initialization of audio devices with close-sourced Windows-only drivers.

Code adapted from [@jcs](https://github.com/jcs)'s [QEMU fork](https://github.com/jcs/qemu) are inside `qemu-9.0.0-intel_hda_dma_capture.patch`. Based on the following commits:
- [VFIO: recognize CORB/RIRB registers and dump DMA values](https://github.com/jcs/qemu/commit/7c1f83b6d700fc2733e0964a1a35383e71ecb838)
- [VFIO: accept 64-bit CORB/RIRB addresses written as two words](https://github.com/jcs/qemu/commit/0d2dd1d0e200f9b71c4fba2767522198630b6796)

## Notes
- [Ryan Prescott has a great tutorial](https://github.com/ryanprescott/realtek-verb-tools/wiki/How-to-sniff-verbs-from-a-Windows-sound-driver) on how to use @jcs's QEMU fork to capture HDA verbs, which is what you'll likely use this packaging script for.
- If you're using libvirtd, you **must** to define the vfio-pci devices manually through [QEMU command-line passthrough](https://libvirt.org/kbase/qemu-passthrough-security.html), and specify **"x-no-mmap": true** on all devices you're passing into the VM! Otherwise, you won't get any intercepted HDA communication from your VM in `/var/logs/libvirt/*.log`.
- The endianness conversions within the patch assume a little-endian host. Don't be surprised when these patches doesn't play nice with QEMU running on, or emulating non-x86_64 architectures!
