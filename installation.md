---
menubar: menu
---

---

## 🚀 First-Time Flashing Instructions for Xiaomi Redmi Note 10 (Sunny/Mojito) and 11 (Spes/Spesn)

**⚠ Disclaimer:** Flashing a custom ROM carries risks, including data loss, boot loops, or bricked devices. Follow these instructions carefully. By proceeding, you acknowledge that any issues arising from improper flashing are your responsibility.


## 📌 Preparation Steps

### 1. Backup Your Data
Before proceeding, create a complete backup of your device. Flashing for the first time will erase all data and restore factory defaults.

### 2. Download and Flash Stock Firmware
- Download the latest firmware for the Xiaomi Redmi Note 10 ([V14.0.9.0.SKGMIXM](https://mifirm.net/download/12791))
- Or download the latest firmware for the Xiaomi Redmi Note 11 ([OS1.0.8.0.TGCMIXM](https://mifirm.net/download/14675))
- Extract the downloaded firmware package.

### 3. Enter Fastboot Mode
1. Power off your device.
2. Hold **Volume Down + Power** simultaneously to enter Fastboot mode.

### 4. Connect and Flash Stock Firmware
1. Connect your device to a PC via USB-C.
2. Open a terminal or command prompt.
3. Navigate to the extracted firmware folder and run:
   - **Windows:** `flash_all.bat`
   - **Linux/macOS:** `flash_all.sh`

### 5. Verify and Boot
- Ensure the flashing process completes with a "Success" message.
- If it fails, repeat Step 4 or force reboot by holding the Power button.
- Wait for the **MIUI** setup screen to appear after a successful flash.
- **Complete the MIUI setup** until the home screen is fully loaded, thereby finishing the MIUI post-installation process.

---

## 🔧 Flashing a custom ROM for the first time

### 6. Flash Custom ROM
1. Download your desired ROM, its 'boot.img' and 'vendor_boot.img' files
2. Re-enter Fastboot mode (see Step 3).
3. Open a terminal or command prompt.
4. Flash the recovery image using:
   - `fastboot flash boot boot.img`
   - `fastboot flash vendor_boot vendor_boot.img`
   - `fastboot reboot recovery`
5. In recovery mode:
   - Navigate using **Volume buttons** and confirm with the **Power** button.
   - Select **Apply Update > Apply from ADB**.
6. Flash the ROM:
   - `adb sideload your_rom.zip`
7. Once flashing is complete, restart recovery when prompted.

### 7. Factory Reset, Boot and Updating ROM
1. **Perform a factory reset in the custom recovery:**
   - Navigate to **Factory Reset** and confirm the action twice.
2. **Reboot your device** to load the new ROM.
3. **Flashing or updating a ROM** can now be done using the Updater app, or by rebooting the device into recovery mode and flashing a new ZIP image.

---

## 🔓 Optional: Root Access & Custom Recovery

### 8. Install Magisk (Root) and/or Custom Recovery
1. Download **Magisk** from [GitHub](https://github.com/topjohnwu/Magisk) and/or the **TWRP (Team Win Recovery Project)**, **PBRP (Pitch Black Recovery Project)**, or  **OrangeFox Recovery** custom recovery.
2. **Disable your screen lock or set it to "swipe."** Otherwise, the custom recovery may be unable to decrypt your data partition.
3. Boot into recovery mode and install the custom recovery first (if required):
   - `adb sideload your_custom_recovery.zip`
4. Flash Magisk:
   - `adb sideload Magisk-version.apk`
   -  In TWRP and PBRP recovery, navigate to the /Magisk/Magisk.zip file and proceed to flash the zip. Additionally, OrangeFox features the latest Magisk support integrated directly into its user interface.
5. Reboot and complete Magisk setup in the app.

---

## 🏪 Play Store & Alternative App Stores

### 9. Google Play Services (alternatives)
The crDroid and LineageOS ROMs provide a customizable Android experience with MicroG, a free alternative to Google Play Services, allowing users to access essential functionalities without proprietary software.
They also include Aurora Store, which lets users download apps from the Google Play Store without a Google account, and F-Droid, a repository of free and open-source applications.
Together, these tools offer a complete and privacy-focused alternative to GApps.

---

## ⚠️ Common Issues & Fixes

### 1. Black Screen After Booting Custom Recovery
- **Cause:** The ROM uses `vendor_boot`, which can cause issues with custom recoveries.
- **Solution:** 
  1. Use a ROM that supports non-`vendor_boot` recoveries.
  2. Ensure you flash both the `boot` and `vendor_boot` images correctly.

### 2. Screen Hangs in Custom Recovery
- **Cause:** The recovery may not support encryption, or the data partition may be corrupted.

#### Action 1: Disable Screen Lock
- **Solution:** Disable your screen lock for better compatibility.

#### Action 2: Perform Factory Reset or Use a Compatible Recovery
- **Solution:** If the issue persists, perform a factory reset or switch to a recovery that supports decryption.

### 3. Touchscreen/Sideloading Not Working in Recovery
- **Cause:** An outdated ROM or firmware may have loaded old vendor firmware.
- **Solution:** Flash the latest ROM to update the vendor partition.

---

✅ **You're all set!** Enjoy your new custom ROM!


---

## 4.📝 Notes
1. Always use the latest firmware before flashing custom ROMs.
2. Follow the exact steps to avoid boot loops or bricked devices.
3. Utilize **ADB** and **Fastboot** tools for a seamless flashing experience.
4. A custom recovery and Magisk must be flashed after each update, as they are overwritten by the updating process.
5. Updates will be released monthly or quarterly, and unpopular ROMs with fewer than 10 users may be dropped eventually.
6. We welcome your opinions or corrections if they can help improve our work.
    
---
