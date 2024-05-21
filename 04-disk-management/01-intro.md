# DISK MANAGEMENT

## PARTITIONS

Disk can be divided into parts, called partitions. 

Paritions allow you to separate data. 

Partitioning schemes:
* 1: OS, 2: Application, 3: User, 4: Swap.
* 1: OS, 2: User home directories.
* As a System Administrator, you decide. 

It can protect the overall system.

It keep users from creating outages by using a home directory partition.

Examples:
```
$ df -h
```

## MBR (Master Boot Record) : Registro del Arrance Principal

It can only address 2 TB of disk space. 

It being phased out by **GPT**, stand for ***GUID Partition Table***. 

It has 4 primary Partitions. 

Extended partitions allow you to create logical partitions. 

## GPT also know GUID Partition Table

**`GUID`** = **Global Unique Identifier**

The GPT is deplacing the older  MBR partitioning scheme. 

It is part of UEFI. 

**UEFI** = **Unified Extensible Firmware Interface**. 

And UEFI is replacing BIOS. 

* Support up to 128 partitions. 
* Support up to 9.4 ZB disk sizes. 
* Not supported by older operating systems. 
* May require newer or special tools. 


## MOUNT POINTS 

It is a directory used to access the data on a partition. 

The `/(slash)` is always a mount point. 

Example: 
```
/home 
    /home/user # It is on the partition mounted on /home. 


/export/home
    /export/home/user
```

### MOUNTING OVER EXISTING DATA

```
$ mkdir /home/user2

$ mount /dev/sdb2 /home
# You will not able to see /home/user2 now. 

$ unmount /home
# You can now see /home/user2 again. 
```


## `fdisk`

Alternatives: `gdisk`, `parted`.

Earlier versions of fdisk did not support GPT. 

Syntax:
```
$ fdisk/path/to/device
```