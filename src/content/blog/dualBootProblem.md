---
title: "fix slow boot"
description: ""
pubDate: "July 19 2023"
heroImage: ""
badge: "linux"
---

### Resize root partition problem

On my laptop 256GB SSD where I already installed **Fedora** as main OS and **Windows 11**, I got an idea to install **Kali Linux** by resizing Fedora root directory and using easeUS partition master on iso but there was a problem, it took 2 hours to do it and then the laptop battery died. Using Gparted on Linux Mint Live, I finally resized the volume.

### Installation

Afterwards, proceed to install Kali using the common efi partition for three operating systems i.e 512MB,swap partition that already using by fedora and resize  30GB as root which is successfull on install everything works great on kali.

### Slow boot

on **fedora** face slow boot about 1 min 15 sec time to boot and check boot time by

```bash
sudo systemd-analyze plot > boot.svg
```

Some disk related task takes time about 45s to wait then check *gnome disk* see **swap** is not mount at boot it means it has swap partition with _UUID_ looking for is not avaiable because installation of kali linux formated and change _UUID_ of *swap*  so it looking for original UUID that make *45sec* wait.

#### how to mount swap partition at boot ?

To mount a swap partition at boot in Fedora (or any Linux distribution that uses systemd), follow these steps:

1. Identify the Swap Partition:
   First, you need to know the device name or UUID of the swap partition you want to mount at boot. You can use the `lsblk` command to list all available block devices and find your swap partition. Look for a partition with the "swap" filesystem type.

   Run the following command to list the block devices:

   ```bash
   lsblk
   ```

Identify the partition labeled as "swap"
2. Backup /etc/fstab (optional but recommended):
   ```bash
   sudo cp /etc/fstab /etc/fstab.backup
   ```

3. Edit /etc/fstab:
   Now, you need to edit the `/etc/fstab` file to include your swap partition. Open the file using a text editor such as "nano" or "vim". For example:

   ```bash
   sudo vim /etc/fstab
   ```

   Add the following line to the end of the file, replacing `/dev/nvme0n1pX` with the actual device name or *UUID* of your swap partition:

   ```
   UUID=<swap_partition_UUID> none  swap  defaults  0  0
   ```
   Note: If you are using a UUID, you can find it by running the following command, replacing `/dev/nvme0n1pX` with your actual partition:

   ```bash
   sudo blkid /dev/nvme0n1pX
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
