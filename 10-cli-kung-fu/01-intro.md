# COMMAND LINE KUNG FU

* Tabs
* `sudo !!`
* ![previous command]

Examples:
```
$ whoami 

$ uptime

$ df -hT /boot

$ !u
# output: uptime

$ sudo !w
# output: whoami
```

## RERUN A COMMAND STARTING WITH STRING

Syntax:
```
!<STRING>
```

Examples:
```
!d
!du
!df
```

Great for rechecking status:
* Determine status.
* Perform work. 
* Recheck Status.

Examples:
```
$ cd /mnt/data/restore

$ df -h .

$ tar xf ~/backup.tar

$ !d
```

## REUSE ARGUMENTS

Helpful when working on a series of items. 
    * Files 
    * Directories 
    * Etc. 

Helpful for correcting command typos. 

To use the arguments from the previous command line in your current command, type `!*`. 

Examples:
```
$ touch file1 file2 file3 

# It mean, all previous arguments. 
$ ls !*

# Move the previous arguments to this directory.
$ mv !* /tmp/
```

```
$ mkdir one two three

$ chmod 700 !*
```

When you mispelling a command:
```
$ grpe -i error /var/log/syslog
# output: error

# With this '!*', you dont need to type again! 
$ grep !*
```


## STRIP OUT COMMENTS AND BLANK LINE

Use this:
```
$ grep -Ev '^#|^$' file.txt

$ grep -Ev '^#|^$' file.txt | wc -l
```


## REUSE THE LAST ITEM FROM THE PREVIOUS COMMAND

Syntax: `!$`

Examples:
```
$ mkdir restore

$ cd !$
```

```
$ unzip /home/user/download/backup.zip

$ remove !$
```

```
$ mkdir mispel

$ rm !$

$ mkdir !$ling
```

```
$ sudo useradd -m -s /bin/bash user1

$ sudo passwd !$
```


