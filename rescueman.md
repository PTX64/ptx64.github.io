---
layout: page
title: Fortress64 - Securing Your Digital Privacy
menubar: menu
---
## Usage

1. **Create a Live USB**: Use a tool like `dd`, Rufus, or Etcher to write the `Android Live Recovery USB` image to a USB drive.
2. **Boot from USB**: Insert the USB drive into your computer and boot from it. You may need to adjust your BIOS/UEFI settings to enable USB booting.
3. **Access Recovery Tools**: Once booted, you will have access to the recovery tools and desktop applications included in the image.

### Example EDL Usage for the Redmi Note 10:

1. Mount a partition on your PC to the live USB image.
2. Download the official firmware `mojito_global_images_V14.0.9.0.SKGMIXM_20240616.0000.00_12.0_global_eb0446ec87.tgz` to this partition and extract the files.
3. Locate the file `prog_ufs_firehose_sm6150_ddr.elf` in the extracted directory.
4. Connect the USB cable and reboot the device into EDL mode using `fastboot oem edl`. Alternatively, you can reboot into EDL mode by short-circuiting the pins, as demonstrated in this [video](https://www.youtube.com/shorts/z5qW0LZfpB4). Make sure to dismantle the phone first as shown in this [video](https://www.youtube.com/watch?v=-S2478EQZsU).

The `dmesg` command should report something like 'Qualcomm HS-USB QDLoader 9008' (more information is available online if you encounter issues booting to EDL using this method).
5. Execute `edl nop --loader="prog_ufs_firehose_sm6150_ddr.elf"`; it should show up as authorized, as illustrated in the screenshot below:

   ![sunny-unlock-edl](https://github.com/user-attachments/assets/cc97f9da-15e3-4c6c-8f4a-0ac4f3dbc898)

6. To back up the device before flashing, create a new directory on your mounted partition, navigate to that directory, and run `edl rf flash.bin --memory=ufs` to dump the complete phone. If this completes successfully, proceed to the next step.
7. Now, flash and restore the entire phone using the following commands:
   ```bash
   edl qfil rawprogram0 patch0.xml
   edl qfil rawprogram1 patch1.xml
   edl qfil rawprogram2 patch2.xml
   edl qfil rawprogram3 patch3.xml
   edl qfil rawprogram4 patch4.xml
   edl qfil rawprogram5 patch5.xml

8. Since it is a serial connection, the process may take a long time to complete. Reboot the device afterward and check if it works.
9. It is recommended to reflash the official firmware with Fastboot afterward to ensure stability.

We welcome contributions to this project! If you would like to help, please feel free to submit issues or pull requests. Your feedback and contributions are greatly appreciated. You can share your thoughts in the topic: [Android Live Recovery USB](https://xdaforums.com/t/android-live-recovery-usb-bootable-toolkit-for-flashing-recovering-and-de-bricking-xiaomi-motorola-oneplus-and-samsung-devices-20-august-2025.4755466/).
# Supported and Verified Xiaomi Devices
- **sunny/mojito**: Xiaomi Redmi Note 10  
- **spes/spesn**: Xiaomi Redmi Note 11  
- **alioth**: Xiaomi POCO F3  

# Supported and Verified Other Devices
- OnePlus 3T  
- OnePlus 5  
- OnePlus 6T  
- OnePlus 7T  
- OnePlus 8  
- OnePlus 8T  
- OnePlus 9  
- OnePlus Nord CE  
- OnePlus N10  
- OnePlus N100  
- BQ X  
- BQ X5  
- BQ X2  
- Gigaset ME Pure  
- ZTE MF210  
- ZTE MF920V  
- Sierra Wireless EM7455  
- Netgear MR1100-10EUS  
- Netgear MR5100  

# Unsupported Devices (SDM660 Chipset)
- **clover**: MI PAD 4 / 4 Plus  
- **jason**: Redmi Note 3  
- **jasmine_sprout**: MI A2  
- **lavender**: Redmi Note 7  
- **platina**: Mi 8 Lite  
- **tulip**: Redmi Note 6 Pro  
- **wayne**: MI 6X  
- **whyred**: Redmi Note 5 

## License

This project is licensed under the [MIT License](link-to-license).

## EDL Source

For more information on EDL, visit the [EDL GitHub Repository](https://github.com/PTX64/android_xiaomi_edl).

