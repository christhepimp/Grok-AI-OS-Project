# Rooted Android Emulator Setup Guide

This guide gets you a fully rooted Android Virtual Device so we can start exploring and eventually replacing parts of the Linux-based system with AI components.

## Recommended Path (2026)

### 1. Install Android Studio + SDK

Download from: https://developer.android.com/studio

Make sure these packages are installed via SDK Manager:
- Android SDK Platform-Tools
- Android Emulator
- At least one system image (prefer **Google APIs**, not Google Play, for easiest root)

### 2. Create an AVD (Google APIs image)

1. Open Device Manager in Android Studio.
2. Create Virtual Device.
3. Pick any phone (Pixel 6/7/8 recommended).
4. **Important**: Choose a system image under the **Google APIs** tab (or “Other Images” → google_apis).  
   Avoid images labeled “Google Play”.
5. Finish creation.

### 3. Easy Root (Google APIs images)

```bash
# Start the emulator (or use the play button in Device Manager)
emulator -avd Your_AVD_Name

# In another terminal:
adb root
adb remount
adb shell
# You should now be root (# prompt)
```

If `adb root` works, you already have what you need for early experiments.

### 4. Full Magisk Root (recommended for long-term work)

This gives persistent root + Magisk modules + Zygisk.

**Tool:** [rootAVD](https://github.com/newbit1/rootAVD)

```bash
git clone https://github.com/newbit1/rootAVD.git
cd rootAVD

# List available images
./rootAVD.sh ListAllAVDs   # or rootAVD.bat on Windows

# Patch the ramdisk of your chosen image (example)
./rootAVD.sh system-images/android-34/google_apis/x86_64/ramdisk.img
```

Follow the prompts (choose Magisk version). The script will shut down the emulator.  
Then do a **Cold Boot** of the AVD. Magisk will finish setup on first boot.

After that:
```bash
adb shell
su
# Grant the prompt in Magisk app if it appears
whoami   # should say root
```

### 5. Alternative: On-the-fly root for Google Play images

- [AERoot](https://github.com/quarkslab/AERoot) – modern rewrite
- [android_emuroot](https://github.com/airbus-seclab/android_emuroot) – original

These use QEMU GDB to patch credentials in kernel memory. Useful when you specifically need a Play Store image.

## Next Steps After Root

1. Install Termux (from F-Droid preferred).
2. Inside Termux install `proot-distro` and create a Debian/Ubuntu environment.
3. Start running experiments and logging everything into the `docs/` folder of this repo.

We now have a fully controllable Linux environment inside the emulator. This is our laboratory for the AI-OS.
