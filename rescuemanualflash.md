---
layout: page
title: Fortress64 - Securing Your Digital Privacy
menubar: menu
---
This guide shows how to flash the "Android Live Recovery USB" ISO to a USB drive using balenaEtcher (cross‑platform), Rufus (Windows), and dd (Linux/macOS), and how to boot from it. Follow only the section relevant to your OS/tool.

Prerequisites
- Download the Android Live Recovery ISO and optionally verify the checksum.
- USB flash drive ≥4 GB. Back up any data — flashing erases the drive.
- On Windows run tools as Administrator. On Linux/macOS you may need sudo/root.

## balenaEtcher (Windows, macOS, Linux)
1. Download & install  
   - Get balenaEtcher from [balena.io](https://etcher.balena.io/) and install it.
2. Open Etcher.
3. Select image  
   - Click “Flash from file” and choose the Android Live Recovery .iso.
4. Select target  
   - Insert USB; Etcher usually auto-detects. Confirm the correct drive.
5. Flash  
   - Click “Flash!” and wait. Etcher writes and verifies automatically.
6. Eject  
   - When complete, safely eject the USB.

## Rufus (Windows)
1. Download & run  
   - Download Rufus from [rufus.ie](https://rufus.ie/en/). Run the executable (no install).
2. Insert USB.
3. Configure Rufus  
   - Device: select your USB drive.  
   - Boot selection: click SELECT and choose the Android Live Recovery .iso.  
   - Partition scheme: leave default (Rufus will suggest GPT).
   - File system: leave default (Rufus will suggest FAT32/NTFS).  
4. Start  
   - Click START. If prompted to choose ISO or DD mode, use the default (try DD mode if boot issues occur).  
   - Confirm warning about data destruction.
5. Finish & eject.

## dd (Linux or macOS) — careful
Warning: dd will overwrite the selected device. Confirm device path before running.

1. Identify device path  
   - Linux: run lsblk or sudo fdisk -l. The USB is typically /dev/sdX (e.g., /dev/sdb).  
   - macOS: run diskutil list. The USB is /dev/diskN (use raw device /dev/rdiskN for speed).
2. Unmount the USB  
   - Linux: sudo umount /dev/sdXN for mounted partitions.  
   - macOS: diskutil unmountDisk /dev/diskN
3. Write image with dd  
   - Linux example:
     ```
     sudo dd if=/path/to/Android_Live_Recovery_USB-*.iso of=/dev/sdX bs=4M status=progress conv=fsync
     ```
   - macOS example:
     ```
     sudo dd if=/path/to/Android_Live_Recovery_USB-*.iso of=/dev/rdiskN bs=1m status=progress
     ```
   - Replace device path with the whole-device (not a partition like /dev/sdX1).
4. Flush caches and eject  
   - ```
     sudo sync
     ```
   - Linux:
     ```
     sudo eject /dev/sdX
     ```
   - macOS:
     ```
     diskutil eject /dev/diskN
     ```

## How to boot from the USB
1. Insert the prepared USB into the target computer.
2. Open boot menu or firmware settings  
   - Common keys at power on: Esc, F2, F10, F12, Del. Use the Boot Menu or enter BIOS/UEFI.
3. Select USB from boot menu (preferred) — choose the entry labeled UEFI: <USB name> if available.
4. BIOS/UEFI alternative  
   - Set USB/UEFI USB first in boot order. If Secure Boot prevents booting, disable Secure Boot temporarily.
5. UEFI vs Legacy  
   - For UEFI choose the UEFI USB entry. For legacy/CSM choose the legacy USB entry.
6. Boot the Android Live Recovery environment from the menu and proceed.

## Notes
- These methods produce a live USB without persistent storage.
- If the system won’t boot, try switching Rufus to DD mode or use balenaEtcher which handles most hybrid ISOs automatically.  
- If unsure which tool to use: balenaEtcher is simplest; Rufus gives advanced Windows options; dd is for command‑line users.

