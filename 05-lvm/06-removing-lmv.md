# REMOVING LV, PV, AND VG.

## UMOUNT 

In order:"
```
# Unmount
$ umount /secrets

# Remove Logical Volume
$ lvremove /dev/vg_safe/lv_secrets 

# Discard or quit or unpatch from Volume Group
$ vgreduce vg_safe /dev/sde 

# Remove Physical Volume
$ pvremove /dev/sde

# Then check
$ pvs

# Now finally remove Volume Group
$ vgremove vg_safe


```