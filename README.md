# arch-pkg-qemu-hdadump
A modified version of `qemu` packaging script on Arch Linux that incorporates [@jcs](https://github.com/jcs)'s patches for QEMU, allowing for capture of communication between the guest OS and audio hardware passed-through via VFIO.

The patches that being applied in `qemu-9.0.0-intel_hda_dma_capture.patch` does not contain my code, they come from [@jcs](https://github.com/jcs)'s [QEMU repository](https://github.com/jcs/qemu). Commits: [1](https://github.com/jcs/qemu/commit/7c1f83b6d700fc2733e0964a1a35383e71ecb838) and [2](https://github.com/jcs/qemu/commit/0d2dd1d0e200f9b71c4fba2767522198630b6796).

Note that the endianness conversions within the patches assume a little-endian host. Don't be surprised when these patches doesn't play nice with QEMU running on, or emulating non-x86_64 architectures!
