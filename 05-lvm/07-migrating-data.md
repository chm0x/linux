# MIGRATING DATA FROM ONE STORAGE DEVICE TO ANOTHER

Steps:
```
# Create a PV.
$ pvcreate /dev/sde

# Extend a  VG.
$ vgextend vg_app /dev/sde

# Check PV
$ pvs

# Perform a Data Migration
$ pvmove /dev/sdb /dev/sde

# Lets check again. 
$ psv

# Check the Physical Extend (PE)
$ pvdisplay /dev/sdb

# OPtional: Then reduce the  Volume Group
$ vgreduce vg_app /dev/sdb
```