# MIRRORING LOGICAL VOLUME 


Same process, suppose we must have a safe place for the backup.

```
$ pvcreate /dev/sdd /dev/sde

$ vgcreate vg_safe /dev/sdd /dev/sde
```

Now lets mirroring the LV.
```
# Tell it how many additional copies of our data we want
# and we want one additional copy.
# Means that the data will be stored on two disks or two copies. 
$ lvcreate -m 1 -L 5G -n lv_secrets vg_safe

# Then check
$ lvs

$ lvs -a

$ pvdisplay -m


$ mkfs -t ext4 /dev/vg_safe/lv_secrets

$ mkdir /secrets 

$ mount /dev/vg_safe/lv_secrets /secrets 
```