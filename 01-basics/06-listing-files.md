# LISTING FILES 


## ALl details

Long Detail List

```
$ ls -l
```

1. Permissions &rarr; -rw-rw-r--
2. Number of links &rarr; 1
3. Owner Name &rarr; admin
4. Group name &rarr; users
5. Number of bytes in the file &rarr; 10400
6. Last modification time &rarr; Sep 27 08:52
7. File name &rarr; sales.data

## Show Hidden Files

* dot files. 
* Hidden files are not displayed by default 

```
$ ls -a
```

## Reveal Files Types

```
$ ls -F
```

* **/** &rarr; As Directory
* **@** &rarr; As Link (Symbolic Links)
* **\*** &rarr; As Executable

## Symbolic Links

A link point to the actual file or directory. 

Use the link as if it were the file. 

A link can be used to create a shortcut. (Use for long file or directory names or indicate the current version of software).


## Time

List files by time

```
$ ls -t
```

## Reverse order

```
$ ls -r
```

## Long listing including all files reverse sorted by time

Including file type. 
```
$ ls -lartF
```

## Listing Files Recursively

```
$ ls -R
```

## List Directories, No content

List directory name, no content
```
$ ls -d
```

## Listing Files with Color

```
$ ls --color
```

## The Tree Command

Similar to `-R`, but creates visual output. 

```
$ tree -d 

$ tree -C
```

Where:

* `-d` &rarr; List directories only. 
* `-C` &rarr; Colorize output. 

## Working with spaces in names

* Not recomended
    * Alternatives : Hyphens(-), Underscores(_) or CamelCase


1. Encapsulate the entire file name in quotes. 
2. use a backslash (\) to escape spaces. 

```
$ ls -l 'my notes.txt'

$ ls -l my\ notes.txt
```


