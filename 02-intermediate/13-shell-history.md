# SHELL HISTORY

Executed commands are added to the history. 

Shell history can be displayed and recalled. 

Shell history is stored in memory and on disk:
* ~/.bash_history
* ~/.history
* ~/.histfile


## Commands

```
# Display the shell history.
$ history

# Controls the number of commands to retain in history. 
# By default=500
$ HISTSIZE

# i.e
$ export HISTSIZE=1000
```

# ! Syntax

```
# Repeat command line number N. 
$ !N

# Repeat the previous command line
$ !!

# Repeat the most recent command starting with "string"
!string
```

More examples:
```
$ !:N <Event> <Separator> <Word>
```

`!` &rarr; Represents a command line(or event).
`!` = &rarr; The most recent command line. 
`!=!!` 

`:N` &rarr; Represents a word on the command line. 
* 0 = command 
* 1 = first argument, etc. 

Examples:
```
$ head files.txt sorted_files.txt notes.txt
<output from head command here>

# Repeated the previos command
$ !! 
<output from head command here>

# Took the 2nd argument, in this case `sorted_files.txt`
$ vi !:2
vi sorted_files.txt
<vi editor start>
```

```
$ ls files.txt sorted_files.txt notes.txt

$ echo alpha bravo charlie

$ echo !^ !l:2 delta !l:0
echo alpha sorted_files.txt delta ls
alpha sorted_files.txt delta ls
``` 

More syntax:
* `!^` &rarr; Represents the first argument. 
    1. `!^` = `!:1`
* `!$` &rarr; Represents the last argument. 

Example:
```
$ head filex.txt sorted_filex.txt notes.txt
```
* `!^` &rarr; files.txt
* `!$` &rarr; notes.txt

# Searching Shell History

* `Ctrl-r` &rarr; Reverse shell history search. And repeat until the desire output.
* `Enter` &rarr; Execute the command.
* `Arrows` &rarr; Change the command.
* `Ctrl-g` &rarr; Cancel the search .

