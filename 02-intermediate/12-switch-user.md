# Switch user 

Using the **su** command. 
```
# Change user ID or become superuser. 
$ su [username]
```

Options | Description | 
--- | --- | 
\- | A hyphen is used to provide an environment similar to what the user would expected had the user logged in directly. | 
-c [command] | Specify a command to be executed. | 


## whoami

```
# Display the username.
$ whoami
```

## sudo - super user do 

Execute a command as another user, typically the superuser. 

```
# List available commands. 
$ sudo -l

# Run command as Root. 
$ sudo [command]

# Same as above
$ sudo -u root [command]

# Run as user 
$ sudo -u user [command]

# Switch to the superuser account. 
$ sudo su

# Switch to the superuser account with root's environment 
$ sudo su -

# Switch to the username account. 
$ sudo su - [username]
```

Examples 2:
```
# Start a shell 
$ sudo -s 

# Same as "sudo -s"
$ sudo -u root -s

# Start a shell as user
$ sudo -u user -s
```

## Changing the `sudo` configuration

**visudo** &rarr; Edit the /etc/sudoers file. 

## Sudoers Format

```
user host=(users)[NOPASSWD:]commands

adminuser ALL=(ALL) NOPASSWD:ALL

bob linuxsvr=(root) /etc/init.d/oracle
```