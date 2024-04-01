# PERMISSIONS


## Regular Permission 

Symbol | Type | 
--- | --- | 
`-` | Regular Type | 
`d` | Directory | 
`l` | Symbolic Link | 
`r` | Read | 
`w` | Write | 
`x` | Execute | 



## Permission - Files vs Directory

Permissions | File | Directory
--- | --- | --- | 
Read (`r`) | Allows a file to be read. | Allows file names in the directory to be read. | 
Write (`w`) | Allows a file to modified. | Allows entries to be modified within the directory. | 
Execute(`x`) | Allows the execution of a file. | Allows access to contents and metadata for entries. 


## Permission Categories

Symbol | Category | 
--- | --- | 
`u` | User | 
`g` | Group | 
`o` | Other | 
`a` | ALl | 

### Groups 

* Every user is in at least one group. 
* Users can belong to many groups. 
* Groups are used to organize users. 
* The ``$ group`` command displays a user's groups. 
* you can also use `$ id -Gn` 


```
$ group 

$ group admin
```

# Changing Permissions

Item | Meaning | 
--- | --- | 
`chmod` | Change mode command |
`ugoa` | User category: user, group, other, all |
`+-=` | Add, substract or set permissions | 
`rwx` | Read, Write, eXecute | 


```
$ chmod g+rwx sales.data # ALl permissions

$ chmod g+w sales.data # Enable Write Mode Only on Group. 

$ chmod g-w sales.data # Remove permission on Group.    

$ chmod g+wx sales.data # Enable Write and Execute mode on Group. 

# Multiple permissions
$ chmod u+rwx,g-x sales.data

# Set permission to all 
$ chmod a=r sales.data

# Empty mean no permissions to Others.
$ chmod u=rwx,g=rx,o= sales.data
```

## Numeric Based Permissions

r | w | x | Values Types |
--- | --- | --- |  --- | 
0 | 0 | 0 | Value for off | 
1 | 1 | 1 | Binary value for on | 
4 | 2 | 1 | Base 10 value for on(Read = 4, Write=2,Execute=1) | 



Octal | Binary | String | Description | 
--- | --- | --- | --- | 
0 | 0 | --- | No permissions | 
1 | 1 | --x | Execute Only | 
2 | 10 | -w- | Write Only | 
3 | 11 | -wx | Write and execute (2+1) | 
4 | 100 | r-- | Read Only | 
5 | 101 | r-x | Read and Execute (4+1) | 
6 | 110 | rw- | Read and Write (4+2) | 
7 | 111 | rwx | All permissions (4+2+1) |


The `755` permission allows everyone on the system to execute the file. 

```
$ chmod 700 file_name.txt
```

**Avoid `777` and `666` permission mode**. 