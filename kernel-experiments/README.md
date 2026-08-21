# Kernel Experiments

Android runs on a modified Linux kernel (Goldfish / Ranchu for the emulator).

This folder is for:

- Notes on the current kernel version used by our AVDs
- Exploring `/proc`, `/sys`, kernel modules
- Building custom emulator kernels (advanced)
- Research into AI-driven scheduling, memory management, or security modules
- Long-term ideas for a minimal AI-aware kernel or unikernel

**Important:** Kernel work is high-risk. Always keep clean AVD snapshots. Never experiment on a system you cannot restore.

Useful starting points:
- AOSP kernel source: https://android.googlesource.com/kernel/
- Emulator kernel (goldfish): https://android.googlesource.com/kernel/goldfish
