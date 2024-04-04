# Copying Files over the Network 

* SCP - Secure copy.
* SFTP - SSH file transfer protocol.

For `Windows`
* PuTTY Secure Copy client - pscp.exe
* PuTTY Secure File Transfer Client - psftp.exe

Graphical SCP/SFTP Clients: 
* Cyberduck
* FileZilla
* WinSCP

Syntax: 
```
# Copy source destination
$ scp [source] [destination]

# sftp = Secure File Transfer Protocol
# Start a secure file transfer session with host. 
$ sftp [host]
# Example sftp john@host

# Start a file transfer session with host. 
# ftp = File Transfer Protocol
$ ftp [host]
```

## Examples
```
$ sftp [hostname]

$ lpwd # local print work directory

$ lls # local list

$ put data.txt # copy 

$ quit
```

```
# Copy the file to tmp dir.
$ scp data.txt [hostname]:/tmp/

# Copy the data to Home
$ scp data.txt [hostname]:~/

$ scp data.txt [username]@[hostnawme]:/home/username/
```