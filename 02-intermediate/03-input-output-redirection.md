# INPUT, OUTPUT and REDIRECTION


There are 3 defualt types of input and output: 

I/O Name | Abbreviation | File Descriptor | 
--- | --- | --- | 
Standard Input (I) | stdin | 0 | 
Standard Output (O) | stdout | 1 |
Standard Error | stderr | 2 |



By default, standard input comes from the keyboard; and standard output and standard error are displayed to the screen.


## Redirection

Symbols | Description | 
--- | --- | 
\> | Redirects standard output to a file. Overwrites(truncating) existing contents. | 
\>\> | Redirects    standard output to a file. Appends to any existing contents. | 
\< | Redirects input from a file to a command. | 
\& | Used with redirection to signal that a file descriptor is being used. |
2\>&1 | Combine stderr and standard ouput. | 
2\>file | Redirects standard error to a file. | 
\>/dev/null | Redirect output to nowhere. 


Examples: 
```
$ ls here not-here 2> /dev/null

$ ls here not-here > /dev/null 2>&1
```

```
$ ls -lF >> ~/Desktop/list_of_files.txt

$ sort < files.txt
```

With **File Descriptor**
```
$ ls -l > files.txt
$ ls -l 1> files.txt
```

**Sort**
```
$ sort < files.txt > sorted_files.txt
```

## Standard Error

```
$ ls files.txt no_exists_data.txt
# Output: ls cannot access no_exists_data: No such file or directory. 

# Redirect only exists to "out"
$ ls files.txt no_exists_data.txt > out

# Redirect errors to "out.err"
$ ls files.txt no_exists_data.txt 2> out.err

# Redirect both with each files. 
$ ls filex.txt no_exists_data.txt 1> out.txt 2> out.err

# Redirect both with one file. 
$ ls files.txt no_exists_data.txt 1> result.txt 2>&1
# With append
$ ls files.txt no_exists_data.txt 1>> result.txt 2>&1


# Redirect to Null
$ ls files.txt no_exists_data.txt 2>/dev/null
$ ls files.txt no_exists_data.txt >/dev/null
$ ls files.txt no_exists_data.txt >/dev/null 2>&1
```
