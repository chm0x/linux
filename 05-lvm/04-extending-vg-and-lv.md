# EXTENDING VOLUMES GROUPS AND LOGICAL VOLUME

First let check the spaces. 

```
$ vgs 
$ vgdisplay

$ lvmdiskscan

# Lets create another PV on other path
$ pvcreate /dev/sdc

# Now extends the group 
$ vgextend vg_app /dev/sdc

# Extends the space to LOGICAL VOLUME
# -r performs the resize of the file system
$ lvextends -L +5G -r /dev/vg_app/lv_data

# And show 
$ lvs

$ df -h /data
```

To fix the size issue. 

```
$ resize2fs /dev/vg_app/lv_data 
```