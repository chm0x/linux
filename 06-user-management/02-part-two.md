# MANAGING USERS AND GROUPS 

## GROUPS

### `/etc/group` FILE

Group details are stored in the `/etc/group` file. 

Format: 
```
group_name:password:GID:account1,accountN
```

Example:
```
root:x:0
sales:x:1001:john,mary
```
Root's default is always 0(zero) for GID.

The password field is used for privileged groups, rarely ever used. 

That information of password is stored in the `/etc/gshadow` file. 


### DISPLAY THE GROUPS THAT AN ACCOUNT BELONGS

```
$ groups root
```

### CREATE A NEW GROUP

```
# Format
$ groupadd [options] [new_group_name]

# Example
$ groupadd web

$ groupadd -g 2500 db
```

OPTIONS | DESCRIPTION | 
--- | --- |
`-g` | Allows you to specify the GID. |


### DELETE A GROUP

```
# Format:
$ groupdel [group_name]

# Example:
$ groupdel db
```

### MODIFY AN EXISTING GROUP

```
# Format:
$ groupmod [options] group_name

# Rename
$ groupmod -n [new_name] [old_name]
```

OPTIONS | DESCRIPTION | 
--- | --- | 
`-g GID` | Change the group ID to GID. | 
`-n GROUP` | Rename the group to GROUP. | 


Examples:
```
$ groupmod -g 1234 web

$ groupmod -n http web
```


Examples to Add User and Groups and Assignment: 
```
$ groupadd writers
$ groupadd tv
$ groupadd movie

$ useradd -c "Ethan Whinters" -g writers -G tv -m -s /bin/bash ethan

# create a password for ethan
$ passwd ethan

# Assing a user to two groups.
$ useradd -c "Ben Affleck" -g writers -G tv,movie -m -s /bin/bash baffleck


```

