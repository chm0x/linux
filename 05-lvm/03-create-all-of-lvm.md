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

# Display PV with Logical Extent(LE)
$ pvdisplay -m
```

3. Create a Volume Group

Use the name convention `vg_app_name`, for best practices. 

```
# Syntax
$ vgcreate [name] [a PV]

$ vgcreate vg_app /dev/sdb

# List the Volume Group
$ vgs 

# Another way to display
$ vgdisplay
```

4. Create a Logical Volume

Again, use the name convention as `lv_app_name`.

```
# create a LV with option (-L) for Human Readable and a name (-n)
$ lvcreate -L 20G -n lv_data vg_app

# Ways to List\view Logical Volumes: 1.
$ lvs

# 2.
$ lvdisplay

# 3. Display the Logical Extent
$ lvdisplay -m
```

And use the remain space with Logical Extent(LE).

```
# It says that use all the remain of the free space. 
$ lvcreate -l 100%FREE -n lv_logs  vg_app
```

5. Create a FILE SYSTEM

```
$ mkfs -t ext4 /dev/vg_app/lv_data

# Next mount point
$ mkdir /data

$ mount /dev/vg_app/lv_data /data
```

6. Persistent Data

```
$ vim /etc/fstab
```

Sample:
```
...

/dev/vg_app/lv_app /app ext4 default 0 0 
```

```
$ mount /app 
```