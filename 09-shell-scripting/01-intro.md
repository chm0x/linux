# SHELL SCRIPTING

## SCRIPT 

A Scripts is a command line program that contains a series of commands. 

Commands contained in the script are executed by an interpreter. 

Anything you can execute at the command line, you can put into a shell script. 

Shell scripts are great at automating tasks. 

Example, `script.sh`: 
```
#!/bin/bash

echo "Scripting is fun" 
```

On CLI: 
```
$ chmod 755 script.sh

$ ./script.sh
```

## VARIABLES

* Storage location that have a name. 
* Name-Value pairs
* By convention, variables are uppercase. 
Syntax: 
```
VARIABLE_NAME="Value" 
```

### VARIABLE USAGE

To ways to display a variable's value.
```
#!/bin/bash

MY_SHELL="bash"

echo "I like the $MY_SHELL shell."
```

```
#!/bin/bash

MY_SHELL="bash"

echo "I like the ${MY_SHELL} shell."
```

### ASSIGN COMMAND OUTPUT TO A VARIABLE

There are two ways to assign a command ouput.
```
#!/bin/bash

SERVER_NAME=$(hostname)

echo "Hostname: ${SERVER_NAME}"
```

*This is the older syntax*
```
#!/bin/bash

SERVER_NAME=`hostname`

echo "Hostname: ${SERVER_NAME}"
```


## TEST

Syntax:
```
[ condition-to-test-for ]
```

Example:
```
[ -e /etc/passwd ]
```

### FILE OPERATORS 

Operator | Description | 
--- | --- | 
`d FILE` | True if file is a directory. |
`e FILE` | True if file exists. |
`f FILE` | True if file exists and is a regular file. |
`r FILE` | True if file is readable by you. |
`s FILE` | True if file exists and is not empty. |
`w FILE` | True if file is writable by you. |
`x FILE` | True if file is executable by you. |


### STRING OPERATORS

Operator | Description | 
--- | --- | 
`-z STRING` | True if string is empty. | 
`-n STRING` | True if string is not empty. | 
`STRING1 = STRING2` | True if the strings are equal. | 
`STRING1 != STRING2` | True if the strings are not equal. | 

### ARITHMETIC OPERATORS

Operator | DESCRIPTION | 
--- | --- | 
`arg1 -eq arg2` | True if arg1 is equal to arg2. | 
`arg1 -ne arg2` | True if arg1 is not equal to arg2. | 
`arg1 -lt arg2` | True if arg1 is less than arg2. | 
`arg1 -le arg2` | True if arg1 is less than or equal to arg2. | 
`arg1 -gt arg2` | True if arg1 is greater than arg2. | 
`arg1 -ge arg2` | True if arg1 is greater than or equal to arg2. | 


## DECISIONS (IF STATEMENT)

Syntax:
```
if [ condition-is-true ]
then
    command 1
    command 2
    command N
fi
```

Examples:
```
#!/bin/bash

MY_SHELL="bash"

if [ "$MY_SHELL" = "bash" ]
then 
    echo "You seem to like the bash shell."
fi 
```

### IF-ELSE STATEMENT

Syntax:
```
if [ condition-is-true ]
then
    command N
else 
    command N
fi
```

Example:
```
#!/bin/bash

MY_SHELL="bash"

if [ "${MY_SHELL}" = "bash" ]
then 
    echo "You seem to like Bash"
else
    echo "You don't seem to like bash."
fi
```

### IF-ELIF-ELSE STATEMENT

Syntax:
```
if [ condition-to-true ]
then 
    command N
elif [ condition-to-true ]
then
    command N
else
    command N
fi
```

Examples:
```
#!/bin/bash

MY_SHELL="bash"

if [ "${MY_SHELL}" = "bash"]
then
    echo "You seems like bash shell."
elif [ "${MY_SHELL}" = "csh" ]
then
    echo "You seems like csh shell." 
else
    echo "You like nothing" 
fi
```

## FOR LOOP

Syntax:
```
for VARIABLE_NAME in ITEM_1 ITEM_N
do 
    command 1
    command 2
    command N
done
```

Examples:
```
#!/bin/bash

for COLOR in red green blue
do 
    echo "Color: ${COLOR}"
done
```

```
#!/bin/bash

COLORS="red green blue"

for COLOR in $COLORS
do 
    echo "Color: ${COLOR}"
done
```

```
#!/bin/bash

PICTURES=$(ls *.jpg)
DATE=$(date +%F)

for PICTURE in $PICTURES
do
    echo "Renaming ${PICTURE} to ${DATE}-${PICTURE}"
    mv ${PICTURE} ${DATE}-${PICTURE}
done
```

## POSITIONAL PARAMETERS

Positional parameters are variables that contain the content of the Command Line. The variables are `$0` through `$9`. 
The script itself is store in `$0`.

```
$ script.sh parameter1 parameter2 parameter3
```

Examples:
```
#!/bin/bash

echo "Executing script: $0"
echo "Archiving user: $1"

# Lock the account
passwd -l $1

# Create an archive of the home directory
tar -cf /archives/${1}.tar.gz /home/${1}
```

```
#!/bin/bash

USER=$1

echo "Executing script: $0"
echo "Archiving user: ${USER}"

# Lock the account
passwd -l $1

# Create an archive of the home directory
tar -cf /archives/${USER}.tar.gz /home/${USER}
```

```
#!/bin/bash

echo "Executing script: $0"

for USER in $@
do
    echo "Archiving user: ${USER}"

    # Lock the account
    passwd -l $USER

    # Create an archive of the home directory.
    tar -cf /archives/${USER}.tar.gz /home/${USER}
done
```


## ACCEPTING USER INPUT (STDIN)

The `read` command accepts STDIN

Syntax:
```
read -p "PROMPT" VARIABLE
```

Examples:

```
#!/bin/bash

read -p "Enter a username:" USER

echo "Archiving user: ${USER}"

# Lock the account
passwd -l $USER

# CREATE AN ARCHIVE OF THE HOME DIRECTORY
tar -cf  /archives/${USER}.tar.gz /home/${USER}
```

