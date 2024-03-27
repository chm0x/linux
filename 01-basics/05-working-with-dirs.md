# WORKING WITH DIRECTORIES


## Directory Shortcuts

* . -> This directory
* .. -> The parent directory
* cd - Change to the previous directory. 
* $OLDPWD -> Holds the directory that you were previously in.


```
$ echo $OLDPWD
$ cd $OLDPWD
```

## creating and removing dirs. 

* mkdir [-p] directory -> Create a directory.
* rmdir [-p] directory -> Remove a **empty** directory. 
* rm -rf directory -> Recursively removes a directory. 
* -p -> Stands for **parents**. Create dirs inside of the parent. 

There is no **undo** nor in the **trash**. 

```
$ mkdir -p dir1/dir2/dir3

$ rmdir dir3/

$ rm -rf dir1/
```
