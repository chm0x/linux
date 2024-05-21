# FILESYSTEM

**ext** = Extended File System. Also ext2, ext3, and ext4 are later releases. Often the default file system type. 

Others file systems: ReiserFS, JFS, XFS, ZFS, Btrfs. 

## CREATE A FILESYSTEM USING `mkfs` COMMAND

```
# Format
$ mkfs -t [TYPE] [DEVICE]

$ mkfs -t ext3 /dev/sdb2

$ mkfs -t ext4 /dev/sdb3

$ mkfs.ext4 /dev/sdb3
```

```
$ ls -1 /sbin/mkfs*
```

## MOUNTING WITH `mount` COMMAND

```
# Format
$ mount [DEVICE] [MOUNT_POINT]

$ mount /dev/sdb3 /opt

# Without argument. The mount will show all devices and virtual files systems. 
$ mount
```

### MANUAL MOUNT DO NOT PERSIST

In order to make mounts persist between reboots, add an entry in the `/etc/fstab` file. 


## UNMOUNT WITH THE `umount` COMMAND

```
# Format
$ unmount [DEVICE_OR_MOUNT_POINT]

$ umount /opt

$ unmount /dev/sdb3
```

## THE `df` COMMAND

Stand for **disk-free**. 

It is the short of `mount` command. 

```
# -h as Human Readable. 
$ df -h
```

## PREPARING SWAP SPACE

```
# Step 1
$ mkswap /dev/sdb1 

# Step 2
$ swapon /dev/sdb1

# Step 3
$ swapon -s
```

## `/etc/fstab` - THE FILE SYSTEM TABLE

Controls what devices get mounted and where on boot. 

Each entry is made up of 6 fields. 
* device
* mount point
* file system type
* mount options
* dump
* fsck order

Sample `/etc/fstab` file
```
# device    mount   point   FS  options     dump    fsck
/dev/sda2   /               xfs defaults     0       1    
/dev/sda1   swap            swap defaults    0       0
```
**UUID** stand for **Universally Unique Identifier**. 

The dump column is used by the dump utility. If it contains a 0, dump will ignore this file system. If it contains 1, dump will backup thus file system.

The fsck is used at boot time to determine if a file system is to be checked and if so, in what order to check them. Valid values are 0,1 and 2. Zero will skip checking the file system, with 1 value will be checked first then the value 2 will be checked next. 

The best practice that the root `/` will be checked first. 

Another example of `fstab` file. 

```
UUID=[keywords]     /   xfs     defaults    0   1
LABEL=opt   /opt    ext4    defaults   1   1   
/dev/sda1   swap    swap    defaults   0   0
```

## VIEWING LABELS AND UUIDS

```
$ lsblk -f

# If you are interested with UUID only. 
$ blkid
```

## LABELING A FILE SYSTEM

Each file system type will have a utility that you can use to create or modify the label for the file system. 

For **ext file system** you can use the **`e2label`** command. 

```
# Format 
$ e2label [device] [label name]

# example
$ e2label /dev/sdb3 opt
```