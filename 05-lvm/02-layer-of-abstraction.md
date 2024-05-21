# LAYER OF ABSTRACTION

The Logical Volume Manager (LVM) introduces extra layers of abstraction between the storage devices and the file systems placed on those storage devices. 

## THE VERY FIRST LAYER IS STORAGE DEVICES

## FIRST LAYER: PHYSICAL VOLUMES (PV)

The **first layer** of abstraction are **physical volumes (PV)**. These are storage devices that are used by LVM. Also, the name is a bit of legacy. These storage devices do not have to be physical, they just have to be made available to the LInux Operating System.

As long as Linux sees the devices as a block storage device, it can be used as a Physical Volume (PV), also know as a PV physical hard drives. I.E: scuzzy drives, sand disks and so on can be PVS. 

## SECOND LAYER: VOLUME GROUP(VG)

A Volume Group(VG) is made up of one or more physical volumes. Just like a pool of storage. If you want to increase the size of the pool, you simply add more PVs. 

## THIRD LAYER: LOGICAL VOLUMES (LV)

Logical Volumes are created from a volume group. File systems are then created on top of those Logical Volumes.

## LAST LAYER: FILE SYSTEMS



Conclusion: Without LVM , you would create a file system on a disk partition, but with LVM you create a file system on  a logical volume. As long as there is free space in the Volume Group, Logical Volumes can be extended. 

You can also shrink Logical Volumes to reclaim unused space if you want, you'll find yourself extending logical volumes. 