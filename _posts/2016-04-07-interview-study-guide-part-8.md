---
inFeed: true
hasPage: true
inNav: false
inLanguage: null
starred: false
keywords: []
description: 'Understanding this process provides a solid foundation for future learning, and it also shows me that somebody has taken the initiative in wanting to learn how things work under the hood.'
datePublished: '2016-04-07T14:52:36.263Z'
dateModified: '2016-04-07T14:52:33.273Z'
title: Interview Study Guide - Part 8
author: []
sourcePath: _posts/2016-04-07-interview-study-guide-part-8.md
published: true
authors: []
publisher:
  name: null
  domain: null
  url: null
  favicon: null
url: interview-study-guide-part-8/index.html
_type: Article

---
![](https://the-grid-user-content.s3-us-west-2.amazonaws.com/e2af30dd-596e-4dbe-93ea-089443120460.png)

## 8\. Understanding What Takes Place When a Computer or Server Boots

**Understanding this process provides a solid foundation for future learning, and it also shows me that somebody has taken the initiative in wanting to learn how things work under the hood.**

### What is a bootloader?

A bootloader is what tells the system to load OS

The primary boot loader that resides in the MBR is a 512-byte image containing both program code and a small partition table. The first 446 bytes are the primary boot loader, which contains both executable code and error message text. The next sixty-four bytes are the partition table, which contains a record for each of four partitions (sixteen bytes each). The MBR ends with two bytes that are defined as the magic number (0xAA55). The magic number serves as a validation check of the MBR. The job of the primary boot loader is to find and load the secondary boot loader. It does this by looking through the partition table for an active partition. When it finds an active partition, it scans the remaining partitions in the table to ensure that they're all inactive. When this is verified, the active partition's boot record is read from the device into RAM and executed.

Stage 2 boot loader The secondary, or second-stage, boot loader could be more aptly called the kernel loader. The task at this stage is to load the Linux kernel and optional initial RAM disk. The first- and second-stage boot loaders combined are called Linux Loader (LILO) or GRand Unified Bootloader (GRUB) in the x86 PC environment. Because LILO has some disadvantages that were corrected in GRUB, let's look into GRUB...

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is the boot process?

READ THE INFO AT THIS LINK!!!

[http://www.ibm.com/developerworks/library/l-linuxboot/][0]

When a system is first booted, or is reset, the processor executes code at a well-known location. In a personal computer (PC), this location is in the basic input/output system (BIOS), which is stored in flash memory on the motherboard. The central processing unit (CPU) in an embedded system invokes the reset vector to start a program at a known address in flash/ROM. In either case, the result is the same. Because PCs offer so much flexibility, the BIOS must determine which devices are candidates for boot. We'll look at this in more detail later.

When a boot device is found, the first-stage boot loader is loaded into RAM and executed. This boot loader is less than 512 bytes in length (a single sector), and its job is to load the second-stage boot loader. When the second-stage boot loader is in RAM and executing, a splash screen is commonly displayed, and Linux and an optional initial RAM disk (initrd, temporary root file system) are loaded into memory. When the images are loaded, the second-stage boot loader passes control to the kernel image and the kernel is decompressed and initialized. At this stage, the second-stage boot loader checks the system hardware, enumerates the attached hardware devices, mounts the root device, and then loads the necessary kernel modules. When complete, the first user-space program (init) starts, and high-level system initialization is performed.

In a PC, booting Linux begins in the BIOS at address 0xFFFF0\. The first step of the BIOS is the power-on self test (POST). The job of the POST is to perform a check of the hardware. The second step of the BIOS is local device enumeration and initialization.

#### SIX STEP PROCESS

1. **BIOS**
> 
>   * Performs system integrity checks
>   * **Searches, loads, and executes the Boot Loader program**
> > 
> >     * **Searches for the Boot Loader in the:**
> > > 
> > >       * Disk Drive
> > >       * SD Card Reader
> > >       * CD/DVD ROM
> > >       * Hard Drive
> > >       * USB
> > >       * Network
> > 
> >     * You can configure which order the boot devices are checked in the BIOS (typically by pressing F2 or F12 in the boot screen)
> 
>   * BIOS gives control over to the Boot Loader program once it is detected and loaded into memory (RAM?)
>   * In short, the BIOS loads, and executes the MBR Boot Loader

2. **MBR**
> 
>   * It is located in the first sector of the bootable disk (the first 512 bytes)
>   * The MBR is less than 512 bytes in size
>   * **The Primary Boot Loader info contains three components:**
> > 
> > 1\. The first 446 bytes contains the Partition Table info 1\. In the next 64 bytes, the MBR Validation Check 1\. In the last 2 bytes, it contains information about GRUB
> 
>   * In short, the MBR loads and executes GRUB

3. **GRUB**
> 
>   * If you have multiple kernel images installed, then you can choose which one to be executed
>   * It displays a splash screen, then waits a few seconds
>   * If nothing is entered it loads the default kernel image, as specified in the grub configuration file (/boot/grub/grub.conf)
>   * GRUB has the knowledge of the file system
>   * In short, GRUB loads the kernel and initial ramdisk images (init rd 
>   * Initial ramdisk is used by the kernel as a temporary root filesystem, until the kernel is booted and the real root filesystem is mounted

4. **KERNEL**
> 
>   * It mounts the root filesystem, as specified in the GRUB configuration file (/boot/grub/grub.conf)
>   * The kernel executes the init program located in the/sbin/initdirectory
>   * Theinitprogram becomes the first program to be executed, it has a process id of1
>   * You can runps-ef| grep initto verify
>   * For example:user@xubuntu:~$ ps -ef | grep init
> root 1 0 0 Sep01 ? 00:00:03 /sbin/initipatino 1152 1075 0 Sep01 ? 00:00:00 /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrcipatino 26413 1594 0 06:09 pts/1 00:00:00 grep --color init
>   * In short, the kernel loads the filesystem and runs theinitprogram

5. **INIT**
> 
>   * It looks for the/etc/inittabfile to decide the correct runlevel
>   * The runlevel decides what initial programs will be loaded at startup

6. **RUNLEVEL**
> 
>   * The system now executes the programs based on the currect runlevel
>   * **Here are the directories for each runlevel:**
> > 
> >     * Runlevel 0 -/etc/rc.d/rc0.d/OR/etc/rc0.d/
> >     * Runlevel 1 -/etc/rc.d/rc1.d/OR/etc/rc1.d/
> >     * Runlevel 2 -/etc/rc.d/rc2.d/OR/etc/rc2.d/
> >     * Runlevel 3 -/etc/rc.d/rc3.d/OR/etc/rc3.d/
> >     * Runlevel 4 -/etc/rc.d/rc4.d/OR/etc/rc4.d/
> >     * Runlevel 5 -/etc/rc.d/rc5.d/OR/etc/rc5.d/
> >     * Runlevel 6 -/etc/rc.d/rc6.d/OR/etc/rc6.d/
> 
>   * For example:user@xubuntu:~$ sudo ls -lah /etc/ | grep rc.\*
> -rw-r--r-- 1 root root 2.1K Apr 3 2012 bash.bashrc-rw-r--r-- 1 root root 1.7K Nov 22 2011 inputrc-rw-r--r-- 1 root root 8.3K Dec 3 2010 nanorcdrwxr-xr-x 2 root root 4.0K May 28 00:50 rc0.ddrwxr-xr-x 2 root root 4.0K May 28 00:50 rc1.ddrwxr-xr-x 2 root root 4.0K May 28 00:50 rc2.ddrwxr-xr-x 2 root root 4.0K May 28 00:50 rc3.ddrwxr-xr-x 2 root root 4.0K May 28 00:50 rc4.ddrwxr-xr-x 2 root root 4.0K May 28 00:50 rc5.ddrwxr-xr-x 2 root root 4.0K May 28 00:50 rc6.d-rwxr-xr-x 1 root root 306 Feb 5 2014 rc.localdrwxr-xr-x 2 root root 4.0K Feb 5 2014 rcS.d-rw-r--r-- 1 root root 4.4K Feb 10 2012 wgetrc
>   * Programs that start with "S" ('s' for startup), in the runlevel directories, are used during startup
>   * Programs that start with "K" ('k' for kill), in the runlevel directories, are used during shutdown
>   * You will notice that the programs have numbers (S20, S30, S60, S90, etc.) after the 'S' or 'K' designation in their filenames. This is the sequence in which they should be started or killed
>   * For example:user@xubuntu:~$ sudo ls -lah /etc/rc6.d/
> total 20Kdrwxr-xr-x 2 root root 4.0K May 28 00:50 .drwxr-xr-x 134 root root 12K Sep 13 02:45 ..lrwxrwxrwx 1 root root 29 May 6 10:48 K10unattended-upgrades - ../init.d/unattended-upgradeslrwxrwxrwx 1 root root 17 May 6 12:33 K20autokey - ../init.d/autokeylrwxrwxrwx 1 root root 27 May 6 10:48 K20speech-dispatcher - ../init.d/speech-dispatcherlrwxrwxrwx 1 root root 17 May 28 00:50 K80openvpn - ../init.d/openvpn-rw-r--r-- 1 root root 351 Jul 26 2012 READMElrwxrwxrwx 1 root root 18 May 6 10:48 S20sendsigs - ../init.d/sendsigslrwxrwxrwx 1 root root 17 May 6 10:48 S30urandom - ../init.d/urandomlrwxrwxrwx 1 root root 22 May 6 10:48 S31umountnfs.sh - ../init.d/umountnfs.shlrwxrwxrwx 1 root root 20 May 6 10:48 S35networking - ../init.d/networkinglrwxrwxrwx 1 root root 18 May 6 10:48 S40umountfs - ../init.d/umountfslrwxrwxrwx 1 root root 20 May 6 10:48 S60umountroot - ../init.d/umountrootlrwxrwxrwx 1 root root 16 May 6 10:48 S90reboot - ../init.d/reboot

**BACKGROUND INFORMATION/FURTHER STUDY**

### What are run levels?

are they different types tasks that will be run on a server when it boots. there are 0-6

**0 - halt**

**1 - single user mode**This allows you to login as root and have very basic system functions running. This allows you to reset your root password if you had lost that. This is also has no networking ability while is runlevel 1\. You enter this mode if the server is having severe issues and crashing.

**2 - single user mode with networking**This allows the user to continue troubleshooting issues but with networking enabled.

**3**- is a default gui-less interface with the server, aka command line.

**4**- is usually undefined and or wildcard

**5**- is a gui interface for the server allowing you to run gnome, or your choice of desktop environment.

**6 - reboot**This will reboot the system.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is an initial ramdisk img?

Initial RAM disk (initrd) is a temporary root file system that is mounted during system boot to support the two-state boot process. The initrd contains various executables and drivers that permit the real root file system to be mounted, after which the initrd RAM disk is unmounted and its memory freed.

**BACKGROUND INFORMATION/FURTHER STUDY**

### What is an initial ramfs img?

???

**BACKGROUND INFORMATION/FURTHER STUDY**

### What are the differences between LILO and GRUB?

LILO has no interactive command interface, whereas GRUB does.

LILO does not support booting from a network, whereas GRUB does.

LILO stores information regarding the location of the operating systems it can to load physically on the MBR. If you change your LILO config file, you have to rewrite the LILO stage one boot loader to the MBR. Compared with GRUB, this is a much more risky option since a misconfigured MBR could leave the system unbootable. With GRUB, if the configuration file is configured incorrectly, it will simply default to the GRUB command-line interface.

LILO only loads linux and other boot loaders. and GRUB loads a large number of OS's.

LILO works by loading itself into a space that will fit on the MBR. Grub has two stages (because it's too overcomplicated to work as well, err I mean as easily as lilo). It loads stage 1 off the MBR (usually) and stage 2 out of /boot, along with it's config.

[0]: https://web.archive.org/web/20150320081753/http://www.ibm.com/developerworks/library/l-linuxboot/