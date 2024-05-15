# BOOT PROCESS

## BIOS

* BIOS stand for **`Basic Input/Ouput System`**. 
* Its a special **firmware**.
* The first piece of software that is run when a computer is powered on. 
* It's operating system independent. 
* Primary purpose is to find and execute the boot loader. 
* Perform the POST(Power-On Self Test). The POST performs some basic checks of various hardware components such as CPU, memory and storage devices. 

The BIOS contains a list of boot devices such as: 
* Hard Drives
* USB Drives
* DVD Drives


## BOOT LOADERS 

Once a bootable device has been found, the BIOS **will run the boot loader**. 

Types: 
* LILO
    * Linux Loader (OLD)
* GRUB
    * GRand Unified Bootloader (New | Replaced LILO)


The primary purpose of the  **Boot Loaders is start the operating system**. 

Boot loaders can start the operating system with different options. 

### Initial RAM Disk

Also know **`initrd`**, is a temporary filesystem that is loaded from disk and stored in memory. 

This filesystem can contains helpers and modules required to load the permanent OS file system.

### /boot => the boot directory

`/boot` contains the files required to boot Linux: 
* initrf
* kernel
* boot loader configuration

The kernel is typically named "vmlinux" or "vmlinuz". If the kernel is compressed, the name ends in z.

### Kernel Ring Buffer

Contains messages from the Linux Kernel. 
* `dmesg`
* `/var/log/dmesg`

A ring buffer is a data structure that is always the same size. 

### Runlevels 

Runlevels | Description | 
--- | --- | 
0 | Shuts down the system. | 
1,S,s | Single user mode. Used for maintenance. | 
2 | Multi-user mode with graphical interface.(Debian, Ubuntu) | 
3 | Multi-user text mode (RedHat/CentOS) | 
4 | Undefined | 
5 | Multi-user mode with graphical interface (RedHat/CentOS) | 
6 | Reboot | 

Linux uses runlevels to determine what processes and services to start. 

Runlevels were controlled by the init program. 
And the configuration was stored in `etc/inittabl`. 
```
/etc/inittab:

id:3:initdefault:
```

#### Set runlevels

```
$ systemctl set-default graphical.target
```

#### Changing runlevels or targets

1. telinit RUNLEVEL
```
$ telinit 5
```

2. systemctl isolate TARGET
```
$ systemctl isolate graphical.target
```

#### Rebooting

1. 
```
$ telinit 6
```

2. 
```
$ systemctl isolate reboot.target
```

3. 
```
reboot
```

#### shutdown command

```
$ shutdown [options] time [message]
```

1. 
```
$ shutdown -r 15:30 "rebooting!"
```
2. 
```
$ shutdown -r +5 "rebooting soon!"
```
3. 
```
shutdown -r now
```

where the hour format is `HH:MM` and the `+` plus sign represents the number of minutes to wait before performing the action. 

#### poweroff

One of these options. 
```
$ telinit 0

$ systemctl isolate poweroff.target

$ poweroff
```




