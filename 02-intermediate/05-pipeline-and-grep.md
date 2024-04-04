# Searching files with PIPELINE

## The GREP command

Display lines matching a pattern. 

Syntax : 
```
$ grep [pattern] [file]
```

OPtions | Description | 
--- | --- | 
`-i` | Perform a search, ignoring case. | 
`-c` | Count the number of occurrences in a file. | 
`-n` | Precede output with line numbers. | 
`-v` | Invert Match. Print lines that don't match. | 


Examples : 
```
$ grep world text.txt

$ grep -n world text.txt


# Reverse Match. Also know "Not equals (!=)" 
$ grep -v o text.txt # Search that doesn't match with 'o'
```

## The File Command

Display the **file type**.

```
$ file [filename] 
```

Examples:
```
$ file sales.data
```

## strings Command 

Searching for text in binary files. 

Display printable strings. 

## Pipes 

Pipes takes the standard ouput from the preceding command and **passes** it as the standard input to the following command. 

**If the first command displays error messages, those will not be passed to the second command by default**. 

Syntax:
```
$ command-output | command-input 
```

Common uses: 
```
$ cat file | grep [pattern]
```

## cut Command

Cut out selected portions of file.  If file is omitted, use standard input. 

Options | Description | 
--- | --- | 
-d [delimiter] | use delimiter as the field separator. | 
-f [N] | Display the Nth field.|






## Examples 

```
$ strings a_music_file.mp3 | grep -i Michael

$ strings a_music_file.mp3 | grep -i Michael | head -1 

$ strings a_music_file.mp3 | grep -i Michael | head -1 | cut -d ' ' -f2
```

```
$ cat file.txt | grep michael | cut -d ' ' -f1
```

```
$ grep bob /etc/passwd

$ grep bob /etc/passwd | cut -d: -f1,5

$ grep bob /etc/passwd | cut -d: -f1,5 | sort

# tr as translate, convert the text. 
$ grep bob /etc/passwd | cut -d: -f1,5 | sort | tr ":" " " 

$ grep bob /etc/passwd | cut -d: -f1,5 | sort | tr ":" " "  | column -t
```

## Piping Output to a Pager
* more
* less

```
$ cat /etc/passwd | less

$ grep bin /etc/passwd | less
```
