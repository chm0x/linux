# Customizing the Shell Prompt 

* Use an environment variable to customize. 
* Bash, ksh, and sh use $PS1. 
* Csh, tcsh, and zsh use $prompt


Format String | Description | 
--- | --- | 
`\d` | Date in "Weekday Month Date" format. "Tue May 26" | 
`\h` | Hostname up to the first period. | 
`\H` | Hostname | 
`\n` | New Line | 
`\t` | Current time in 24-hour HH:MM:SS format. | 
`\T` | Current time in 12-hour HH:MM:SS format. |
`\@` | Current time in 12-hour am/pm format. | 
`\A` | Current time in 24-hour HH:MM format. | 
`\u` | Username of the current user. | 
`\w` | Current working directory. | 
`\W` | Basename of the current working directory. | 
`\$` | If the effective UID is 0, a "#", otherwise a "$" |




## Examples 

```
echo 'export PS1="[\u@\h \w]\$ "' >> ~/.bash_profile
```


```
$ PS1="<\t \u@\h \w>\$"
```