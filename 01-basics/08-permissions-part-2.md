# PERMISSIONS PART II

## Working with Groups 

* New files belong to your primary group. 
* the `chgrp` command changes the group. 

Show groups: 
```
$ groups 
```

Change group on a file/dir:
```
$ chgrp [group_name] [filename/dir]
```


## Directory Permissions

* Permission on a Dir can affect the files in the directory. 

## File Creation Mask

* File creation mask determines default permissions. 
* If no mask, the default would be: 
    * 777 for directories. 
    * 666 for Files. 


## The umask Command

```
$ umask [mode]
$ umask [-S] [mode]
$ umask 022
```

* Set the file creation mask to mode, if given. 
* Use -S for symbolic notation. 
* Default umask is -022 for DIrectories and Files.   

Common umask modes:
1. 022
2. 002
3. 077
4. 007


## Special MOdes

The special modes are: 
* setuid
* setgid
* sticky


