# ADVANCED PERMISSIONS | SPECIAL MODES

1. `setuid`
2. `setguid`
3. `sticky`


## SETUID

* When a process is started, it runs using the starting user's UID and GID permissions. 
* **setuid files are an attack surface**. 

`setuid` stand for **Set User ID**. It forces a process to start as the owner of the file, regardless who execute that file. 

Check if a file has `setuid`. 

```
-rwsr-xr-x 1 root root /usr/bin/passwd
```

The `s` in the **execute field** of the owner section of permissions. The passwd program is one file that has the **`setuid`** permission. 

The reason the passwd commands uses **setuids** root is because it need root privileges to modify the `/etc/passwd` and/or `/etc/shadow` files when a user changes their password. 

Once an attacker gains access to a system they often look for files that are **`suid`** root. *Since these files run as root, they are an attacker surface for privilege escalation attacks*. 

Most Linux distribution do not honor `setuid` on shell scripts, only on binary files. 

### OCTAL PERMISSIONS

`setuid` | `setgid` | `sticky` | Description | 
--- | --- | --- | --- | 
0 | 0 | 0 | Value for `off` | 
1 | 1 | 1 | Binary value for `on` | 
4 | 2 | 1 | Base 10 value for `on` | 


### ADDING THE `setuid` ATTRIBUTE

Examples
```
$ chmod u+s /path/to/file

$ chmod 4755 /path/to/file
```

### REMOVING THE `setuid` ATTRIBUTE

Exampels:
```
$ chmod u-s /path/to/file

$ chmod 0755 /path/to/file
```

### FINDING SETUID FILES

Examples:
```
# The forward slash means to match any of the permission bits. 
$ find / -perm /4000
$ find / -perm /4000 -ls

# Older style
$ find / -perm +4000
$ find / -perm +4000 -ls
```

### ONLY THE ONWER SHOULD EDIT SETUID FILES

Desc | Symbolic | Octal | 
--- | --- | --- | 
GOOD: | -rwsr-xr-x | 4755 | 
BAD: | -rwsrwxr-x | 4775 | 
REALLY BAD: | -rwsrwxrwx | 4775 | 


## SETGID

`setgid` stand for **Set Group ID**. 

setgid is very much like setuid. It causes the program to run with the group privileges of the file, rather than the group privileges of the person executing the file. 

It check if has an *'s' in the execute field of the group selection of the permission*. 

```
-rwxr-sr-x 1 root tty /usr/bin/wall
```
```
crw--w---- 1 bob tty /dev/pts/0
```

The wall command displays a message to the terminal of users that are logged into the system. Since all the files that represent a users terminal are in the `tty` group and the `tty` group has write permission on those files, anyone using the wall command is allowed to write to those terminals because that process is running with `tty` group privileges. 

### FIND **SETGID** FILES

Examples:
```
$ find / -perm /2000 -ls

# Older Style
$ find / -perm +2000 -ls
```

### ADDING THE **SETGID** ATTRIBUTE

Examples:
```
$ chmod g+s /path/to/file

$ chmod 2755 /path/to/file
```


### REMOVING **SETGID** ATTRIBUTE

```
$ chmod g-s /path/to/file


$ chmod 0755 /path/to/file
```

### SETGID ON DIRECTORIES

* `setgid` on a directory causes new files to inherit the group of the directory. 
* `setgid` causes directories to inherit the setgid bit. 
* It is not retroactive. 
* Great working with groups. 

## ADD BOTH **SETUID & SETGID** ATTRIBUTES

Examples:
```
$ chmod ug+s /path/to/file

$ chmod 6755 /path/to/file
```


## USE AN INTEGRITY CHECKER

* Other options to `find`. 
* Tripwire
* AIDE (Advanced Intrusion Detection Environment)
* OSSEC
* Samhain
* Package managers

## THE STICKY BIT

* Used on a directory to only allow the onwer of the file/directory to delete it. 

Used on `/tmp`:
```
drwxrwxrwt 10 root root 4096 date /tmp
```

It's used on a directory to only allow the files owner, the directory owner or the root user to rename or delete the file. 

Without the sticky bit set on a directory, the user could delete another user's file if the permissions on the directory allowed for it. 
