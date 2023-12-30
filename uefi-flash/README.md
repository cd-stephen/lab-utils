# uefi-flash #
note: this assumes you are using linux at the CLI

Creating a FreeDOS bootable USB drive in Linux using the command line involves a few straightforward steps. The process generally requires downloading the FreeDOS ISO file and writing it to the USB drive using a tool like dd. Here's how to do it:

## Step 1: Download the FreeDOS ISO ##
Go to the FreeDOS download page. - https://www.freedos.org/download/
Download the latest FreeDOS ISO file.

```shell
###############################################################################
		FreeDOS 1.3 ("FreeDOS 1.3")
###############################################################################

-------------------------------------------------------------------------------
		General system requirements:
-------------------------------------------------------------------------------

  * DOS-compatible system (Intel + BIOS, or UEFI with Legacy support)

  * At least 20MB free disk space:

    20MB  Plain DOS system
    30MB  Plain DOS system, with sources

    275MB  Full installation including applications and games
    375MB  Full installation with sources


-------------------------------------------------------------------------------
		What's in all those zip files?
-------------------------------------------------------------------------------

FD13-LiveCD.zip

  * FD13BOOT.IMG - Basic FreeDOS installation boot floppy image.
    If your computer has a CD-ROM drive, but you cannot boot from the Live CD
    or Legacy CD. Use this diskette image to boot the system. Then insert the
    install CD. The FreeDOS installer should do the rest. This diskette
    image is for installation purposes only and does not provide a Live
    Environment.

  * FD13LIVE.ISO - The FreeDOS 1.3 installer.  Most users should
    use this image to install FreeDOS.

    Depending on your computer system and hardware configuration, you
    can also use the LiveCD to boot and run FreeDOS directly from the
    CD-ROM without installation to your hard drive.
  ```

## Step 2: Identify Your USB Drive ##
1. Insert your USB drive into your Linux machine.
2. Open a terminal.
3. Use the command `lsblk` or `fdisk -l` to list all the storage devices. Identify your USB drive (e.g., `/dev/sdb`). Be very careful with this step to ensure you have the correct drive.

## Step 3: Unmount the USB Drive ##
If your USB drive is automatically mounted, unmount (replacing X with the actual letter) it with:
```shell
sudo umount /dev/sdX
```

## Step 4: Write the ISO to the USB Drive ##
Use the dd command to write the FreeDOS ISO file to the USB drive:
```shell
sudo dd if=/path/to/FD13BOOT.img of=/dev/sdX bs=4M status=progress oflag=sync
```

- Replace /path/to/freedos.iso with the full path to the downloaded FreeDOS ISO file.
- Replace /dev/sdX with your USB drive's device path.
- `bs=4M` sets the block size to 4 MB for faster writing.
- `status=progress` will show the progress of the operation.
- `oflag=sync` ensures data integrity by waiting until write operations are finished.

## Step 5: Eject the USB Drive ##
After the dd command finishes, safely eject the USB drive:
```shell
sudo eject /dev/sdX
```

