# WORKING WITH DIRECTORIES


## Directory Shortcuts

* . &rarr; This directory
* .. &rarr; The parent directory
* cd - &rarr; Change to the previous directory. 
* $OLDPWD &rarr; Holds the directory that you were previously in.


```
$ echo $OLDPWD
$ cd $OLDPWD
```

## creating and removing dirs. 

* mkdir [-p] directory &rarr; Create a directory.
* rmdir [-p] directory &rarr; Remove a **empty** directory. 
* rm -rf directory &rarr; Recursively removes a directory. 
* -p &rarr; Stands for **parents**. Create dirs inside of the parent. 

There is no **undo** nor in the **trash**. 

```
$ mkdir -p dir1/dir2/dir3

$ rmdir dir3/

$ rm -rf dir1/
```
