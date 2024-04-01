# Search Files and Directories

Command that allow you to find files and directories

* `find`
* `locate`

## The Find Command

```
$ find [path] [expression]
```

Recursively finds files in path that match the expression. If no arguments are supplied, it finds all files in the current directory. 


Find files and directories that match patterns:
```
$ find -name [pattern]
```


Like -name, but ignores case. 
```
$ find -iname [pattern]
```

Performs an `ls` on each of the found items. 
```
$ find -ls [pattern]
```

Finds files that are days old. 
```
$ find -mtime [days]

# Find files that are more than ten days old, but less
# than 90 days old. 
$ find /usr -mtime +10 -mtime -90
```

Finds file that are of size num.
```
$ find -size [num]

$ find /usr -size +1M
```

Finds files that are newer than file
```
$ find -newer [filename]

# Find a file that are newer than passwd. 
$ find / -newer /etc/passwd
```

Run command against all the files that are found. 
```
$ find -exec [command] {} \;

$ find . -exec file {} \;
```

Types `d` for DIrectories and `f` for files. 
```
find / -type d -name [pattern]
```

### With Expressions

```
$ find [path] -name "*v"
```


## A Fast Find : locate

```
$ locate [path] [pattern]
```

* List files that match pattern. 
* Faster than the `find` command. 
* Queries an index(only and reboot if there are news files or dirs)
* Results are not in real time. 
