---
title: "fix major problem"
description: ""
pubDate: "July 19 2023"
heroImage: ""
badge: "linux"
---

### Resize root partition problem

On my laptop 256GB ssd where i already install **fedora** as main os and **Windows 11** now got and idea to install **kali linux** by resize fedora root directory and use easeUS partition master on iso but got big problem it done job slow for 69% takes 2 hours then laptop shutdown oh battery dies then little google it then used **_gparted_** on live **linux mint** for resize vola it works.

### Installation

then proceed to install kali used comman efi partition for three OS, used already swap partition and resize partition as root successfull on install everything works great on kali

### Slow boot

on **fedora** face slow boot about 1 min 15 sec time to boot and check boot time by

```bash
sudo systemd-analyze plot > boot.svg
```

some disk related task takes time about 45s to wait then check gnome disk see swap is not mount at boot it means it has swap partition with _UUID_ but on installation of kali linux swap partition formated and _UUID_ change so it looking for original UUID that make 45sec wait then i ask AI

#### how to mount swap partition at boot ?

it says
To mount a swap partition at boot in Fedora (or any Linux distribution that uses systemd), follow these steps:

1. Identify the Swap Partition:
   First, you need to know the device name or UUID of the swap partition you want to mount at boot. You can use the `lsblk` command to list all available block devices and find your swap partition. Look for a partition with the "swap" filesystem type.

   Run the following command to list the block devices:

   ```bash
   lsblk
   ```

Identify the partition labeled as "swap" (e.g., `/dev/sdXY` where `XY` are letters representing the specific partition).

2. Backup /etc/fstab (optional but recommended):
   Before making any changes to the system, it's a good practice to create a backup of the `/etc/fstab` file. The `fstab` file contains information about the filesystems and partitions that should be mounted at boot.

   ```bash
   sudo cp /etc/fstab /etc/fstab.backup
   ```

3. Edit /etc/fstab:
   Now, you need to edit the `/etc/fstab` file to include your swap partition. Open the file using a text editor such as "nano" or "vim". For example:

   ```bash
   sudo vim /etc/fstab
   ```

   Add the following line to the end of the file, replacing `/dev/sdXY` with the actual device name or UUID of your swap partition:

   ```
   UUID=<swap_partition_UUID> none  swap  defaults  0  0
   ```

   If you prefer to use the device name, the line would look like this:

   ```
   /dev/sdXY none  swap  defaults  0  0
   ```

   Save the file and exit the text editor.

   Note: If you are using a UUID, you can find it by running the following command, replacing `/dev/sdXY` with your actual partition:

   ```bash
   sudo blkid /dev/sdXY
   ```

4. Enable Swapping:
   Once you have edited the `/etc/fstab` file, you can manually enable the swap partition for the current session without rebooting:

   ```bash
   sudo swapon -a
   ```

   This command activates all swap devices listed in `/etc/fstab`. You can check if the swap is active by running:

   ```bash
   sudo swapon --show
   ```

5. Reboot:
   Finally, to ensure that the swap partition is mounted at boot, you should reboot your system:

   ```bash
   sudo reboot
   ```

After the reboot, the swap partition should be mounted automatically at boot, and you can verify its status using the `swapon --show` command
