# PROCESSES AND JOB CONTROL (CRON)

Display process status with this command:
```
$ ps
```

ps | Options | 
--- | --- |
-e | Everything, all process. | 
-f | Full Format List | 
-u [username] | display username's processes. | 
-p [pid] | Display information for PID | 
-H | Display a process tree |



Common `ps` command: 
```
$ ps -f
$ ps -ef 
$ ps -eH
$ ps -e --forest # Display a process tree. 
4 ps -u [username ]
```

## Other commands 

Command | Description |
--- | --- | 
`pstree` | Display processes in a tree format. | 
`top` | Interactive process viewer. | 
`htop` | Interactive process viewer. | 



## Background and Foreground Processes. 

Command | Description | 
--- | --- | 
`[command] &` | Start command in background. | 
`Ctrl-c` | Kill the foreground process. | 
`Ctrl-z` | Suspend the foreground process. | 
`jobs [%num]` | List jobs. | 
`bg [%num]` | Background a suspended process. | 
`fg [%num]` | Foreground a background process. | 
`kill` | Kill a process by job number or PID. | 


## Killing Processes 

Command | Description | 
--- | --- | 
`Ctrl-c` | Kills the foreground process. | 
`kill [-sig] PID` | Send a signal to a process. |
`kill -l` | Display a list of signals. Defualt is 15 | 

```
$ kill -l
```



## Examples

```
$ jobs %% # Show the current process. 

$ jobs %+ # show the current process. 

# Show the previous process. 
$ jobs %- 
```

