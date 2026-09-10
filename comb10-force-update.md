## Factory installation or recovery

Initial installation and full recovery use SD image. Routine updates should use Wi-Fi or the USB bundle instead.

### What you need

- an SD card with at least 2 GB of capacity;
- an SD card reader; and
- a Windows or Linux computer.

> **Warning:** Writing an image erases everything on the selected SD card.
> Check the selected drive carefully before writing the image.

### 1. Download the image

Download `install_rusefi_combo10_rauc_factory_sd.img.7z` from the [combo10 releases page](https://github.com/rusefi/combo10-releases/releases)
instructions and verify it using the accompanying `SHA256SUMS`.

### 2. Write the image to the SD card

On Windows, extract `install_rusefi_combo10_rauc_factory_sd.img`, then use an
image-writing tool such as
[Rufus](https://rufus.ie/) or
[Win32 Disk Imager](https://sourceforge.net/projects/win32diskimager/).
Select the extracted `.img` file and write it to the **whole SD card**, not to a
partition.

On Linux, identify the SD card with `lsblk`, then write the image with:

```sh
7z x -so install_rusefi_combo10_rauc_factory_sd.img.7z | sudo dd of=/dev/sdX bs=4M status=progress conv=fsync
```

Replace `/dev/sdX` with the device for your SD card. Selecting the wrong device
can erase another disk.

### 3. Install combo10

1. Power off combo10.
2. Insert the prepared SD card.
3. Power on the device.
4. Wait while the screen displays **Installing factory image - do not power
   off**. Do not interrupt power while the image is written and verified.
5. When **Factory install complete - remove SD card and reboot** appears, power
   off the device and remove the SD card.
6. Power on the device again without the SD card.

The device now boots the updated system from its internal storage and starts the
dashboard automatically. Do not interrupt power while an update is in progress.

### Confirm the installation

After the dashboard starts, open **ABOUT DEVICE** from the right-side menu and
confirm that **Dash version** and **Subsystem version** contain the expected
values.
