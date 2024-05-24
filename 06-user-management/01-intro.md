# USER MANAGEMENT

Linux is a multiuser operating system, not only can multiple accounts exist on the system but those accounts can be used at the same time. 

Each account consists of a:
1. username (or login ID)
2. UID (User ID). This is a unique number. 
3. Default Group.
4. Comments. 
5. Shell.
6. Home Directory Location

All this information is stored in the `/etc/passwd` file. 

Sample of the `passwd` file:
```
root:x:0:0:root:/root:/bin/bash
```

Format of the `passwd` file:
```
username:password:UID:GID:comments:home_dir:shell
```


## USERNAME

Linux supports usernames up to 32 characters in length. 
```
$ ps -fu full_username
```

1. usernames are case sensitive.
2. In all lower case by convention. 
3. Numbers are allowed in usernames. 
4. Don't use special characters. 

## PASSWORD

The password is stored at `/etc/shadow` file and its encrypted.

1. Encrypted password used to be stored in `/etc/passwd`.
2. `/etc/passwd` is readable by everyone.
3. Encrypted passwords are stored in `/etc/shadow`.
4. `/etc/shadow` is only readable by root. 
5. Prevent users trying to crack passwords. 

Format:
```
user:encrypted_password:days_from_jan:days_before_pwd:number_of_days:days_to_warn:day_expired:days_disabled:reserved
```
Where:

* **days_from_jan**: It is the number of days since January 1, 1970 since the password has been changed. 
* **days_before_pwd**: It is the number of days before the password can be changed.
* **number_of_days**: Number of days after which the password must be changed. 
* **days_to_warn** : It is the number of days to warn the user that their password will expire.
* **day_expired**: It is the number of days after the password has expired that the account is disabled.
* **days_disabled**: It is the number of days since January 1, 1970 that an account has been disabled.  
* **reserved** : The ninth field is reserved for future use. 

## UIDs (User ID)s

1. The root account is always UID 0.
2. The UIDs are unique numbers. 
3. System account have UIDs < 1000. 
    1. You can configure in `/etc/login.defs`.

## GID (Group ID)

1. The GID listed in the `/etc/passwd/` for is the default group for an account. 
2. New files belong to an user's default group. 
3. Users can switch groups by using the **`newgrp`** command.

## COMMENT Field

1. Typically contains the user's full name. 
2. In the case of a system or application account, it often contains what the account is used for. 
3. May contain additional information like a phone number. 
4. Also called the GECOS field (Historically from UNIX system).

## HOME DIRECTORY

1. Upon login the user is placed in their home directory. 
2. If that directory doesn't exist, they are placed in "`/`'.

## SHELL

1. The shell will be executed when a user logs ins. 
2. A list of available shells are in `/etc/shells` file.
3. The shell doesn't have to be a shell. 
4. To prevent interactive use of an account, use **`/usr/sbin/nologin`** or **`/bin/false`** as the shell. 
5. Shells can be command line applications. 


## `useradd`

Format:
```
$ useradd [options] username
```

Options | Description | 
--- | --- | 
-c "Comment" | Comments for the account. | 
-m | Create the home directory. | 
-s /shell/path | the path to user's shell. | 
-g GROUP | Specify the default group. | 
-G GROUP1, GROUPN | Additional groups. | 
-r | Create a system account (applications). | 
-d /home/dir | Specify the home directory. | 
-d /home/dir | Set the directory where the application settled. | 

Example:
```
$ useradd -c "Grant Steward" -m -s /bin/bash grant 
```

More examples:
```
$ useradd -c "Eddie Harris" -m -s /bin/bash -g sales -G projectx eharris

$ passwd eharris
```

```
$ useradd -c "Apache Web Server User" -d /opt/apache -r -s /usr/sbin/nologin apache


```




### CREATE A PASSWORD USING `passwd`

Syntax:
```
$ passwd [username_that_already_created]
```

Example:
```
# Create a password 
$ passwd grant
```

### ACCOUNT INFO FOR THE RECENT USER

```
$ tail -1 /etc/passwd

$ tail -1 /etc/shadow
```

### `/etc/skel`

* When using the `-m` option the contents of the skeleton directory `/etc/skel` are copied into the user's home directory. 

* When using the `-m` the home directory for the account is created. 
* the contents of `/etc/skel` are copied into the home directory. 
* `/etc/skel` typhically contains shell configuration files (.profile,.bashrc, etc).

### Use `-u` option to specify the UID

```
$ useradd -c "MySQL Server" -d /opt/mysql -u 97 -s /usr/sbin/nologin mysql

$ tail -1 /etc/passwd

```
Output of `tail` command:
```
mysql:x:97:1003:MySQL Server:/opt/mysql:/usr/sbin/nologin
```

## DELETE ACCOUNT WITH `userdel` COMMAND

Syntax:
```
$ userdel [-r] [username]
```

Options | Description | 
-r | Delete the directories in the Home's directory. | 

Example:
```
# Deleting account but not in the home directory
$ userdel grant

# Deleting account and his home directory.
$ userdel -r grant
```

## `usermod` COMMAND

It is used for update or modify an existing account

OPTIONS | DESCRIPTION | 
--- | --- | 
`-c "COMMENT"` | Comments account | 
`g GROUP` | Specify the default group. | 
-G GROUP1, GROUPn | Additional groups. | 
-s /shell/path | Path to the user's shell. | 

Syntax: 
```
$ usermod [options] username
```

Example:
```
$ usermod -c "MYSQL USER" mysql
```
