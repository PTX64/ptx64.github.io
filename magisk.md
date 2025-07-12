### Install Magisk (Root) and/or Custom Recovery
1. Download **Magisk** from [GitHub](https://github.com/topjohnwu/Magisk) and/or the **TWRP (Team Win Recovery Project)**, **PBRP (Pitch Black Recovery Project)**, or  **OrangeFox Recovery** custom recovery from [this location](https://github.com/PTX64/releases_sunny_recoveries/releases/tag/latest).
2. **Disable your screen lock or set it to "swipe."** Otherwise, the custom recovery may be unable to decrypt your data partition.
3. Boot into recovery mode and install the custom recovery first (if required):
   - `adb sideload your_custom_recovery.zip`
4. Flash Magisk:
   - `adb sideload Magisk-version.apk`
   -  In TWRP and PBRP recovery, navigate to the /Magisk/Magisk.zip file and proceed to flash the zip. Additionally, OrangeFox features the latest Magisk support integrated directly into its user interface.
5. Reboot and complete Magisk setup in the app.
