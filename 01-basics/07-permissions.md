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

r | w | x | 
--- | --- | --- | 
0 | 0 | 0 |
1 | 1 | 1 | 