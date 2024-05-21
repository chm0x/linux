# CREATE PV, VG AND LV. 

## LOGICAL VOLUME CREATION PROCESS

At a hight level, the process for creating a LV is this **First you create** one or more physical volumes.  

Then you create a Volume Group from those of one or more Physical Volumes.

And then finally you can create one or more Logical Volumes from that Volume Group. 


## COMMANDS

1. Check the disk and his storage
With ROOT
```
$ sudo su -

# Before you can create a PV. You need to know what storage devices are available using lvmdiskscan command. 

$ lvmdiskscan

# Lets find some info about out bloc devices with lsblk command
$ lsblk
$ lsblk -p

# Lets check with df
$ df -h

# See the storage  that's attached to your Linux System. 
$ fdisk -l
```

2. Create a PV. 
```
$ pvcreate /dev/sdb

# List of PV
$ pvs 
```

3. Create a Volume Group

Use the convention name `vg_app_name`, for best practices. 

```
# Syntax
$ vgcreate [name] [a PV]

$ vgcreate vg_app /dev/sdb

# List the Volume Group
$ vgs 
```