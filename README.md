MultiBoot menu and tools for Odroid XU3/XU4 & C2
===========================================

About
-----

Boot menu for selecting from available OS's<br />
Backup tool for backup operating system(s) from multiboot card or original Odroid card<br />
Universal installer which can install **android**, **linux**, **OpenELEC** or any combinations (**multiboot**) from USB drive.<br />

---

**Multiboot features**

- boot menu for selecting operating system or Multiboot tools
- automaticaly detects installed operating systems on **all** inserted cards (EMMC and/or SD card)
- mimimal changes to original OS images, only fstab is adjusted for multiboot
- on **Odroid C2** both EMMC and SDcard can be inserted and the OS can be booted from EMMC or SDcard
- on **Odroid XU3/XU4** any os on EMMC or SDCard can be booted, regardles of **boot switch** position


**Installer features**

- **interactive** installer
- user can set desired partition sizes and installation destination (SD or EMMC)
- it is possible install to **SD Card** and to **EMMC**
- uses standard Android **update.zip** (XU4) or **daily___.tar.gz** (C2), Linux **image files** and OpenElec **upgrade tar** files as sources
- backup created with **Backup** tool can be used as source
- installation sources must be placed on the **first** USB drive partition
- installation source partition can be formated as **ext4**, **fat32**, **ntfs** or **btrfs**
- supports **multi boot installation** (Android, Linux, OpenELEC)
- tested with latest Android, Linux and OpenELEC versions for XU3/XU4 & C2

**Backup features**

- backup **multiboot** SDCard or EMMC (all installed operating systems) to USB drive
- backup **original Odroid** SDCard or EMMC (Android or Linux) to USB drive
- backup on USB drive can be used as source for **Installer**

**Installer usage**

- use **prepared multiboot installer images**, in **multiboot_install_images.zip**, unzip to some empty directory
- run `sudo dd if=multiboot_install_[c2|xu4].img of=/dev/sdX bs=1MB oflag=direct`
- **or**
- build the installer sdcard/image running `sudo ./prepare_selfinst <destination_card>|<destination_image_name> c2|xu4`
- if the image file is created, you can write the image to SDCard using dd command.
  - copy your installation sources (Android update image **update.zip**, Linux **.img**, OpenELEC **.tar** file) to the first partition of your USB drive
  - **rename** the Linux installation image to **linux.img** !
  - **rename** the OpenELEC installation tar to **oelec.tar** !
  - **rename** the Android installation archive to **update.tar.gz** or **update.zip** !
  - on Odroid UX4/XU3 set the **boot switch** to boot from SDCard
  - connect you USB drive to Odroid, insert SDCard and power on
  - select Install from menu
  - follow the instructions to select desired partition sizes and installation destination (**SDCard** or **EMMC**)

**HINTS**
- select desired Android resolution in **boot.ini.android**, Hardkernel utility does not work
- add **#DESCRIPTION my_os_description** line to **boot.ini.[android|linux|oelec]** files to describe your OS in boot menu
