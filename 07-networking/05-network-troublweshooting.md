# NETWORK TROUBLESHOOTING 

Keywords | Commands:
* `ping`
* `traceroute` / `tracepath`
* `netstat`
* `tcpdump`
* `telnet`

Network troubleshooting is a large and complex topic.


## TESTING CONNECTIVITY WITH PING

Format:
```
$ ping HOST

$ ping -c COUNT HOST
```

Examples:
```
$ ping -c 3 www.google.com
```

**rtt** stand for **Round Trip Time**. 

## `traceroute` COMMAND

To examine the route, use the `traceroute` command.
It requires root privileges to performing. 
```
$ traceroute -n google.com
```


## `tracepath` COMMAND

An alternative to `traceroute`.

Does not require root privileges.

Examples:
```
$ tracepath -n google.com
```

## `netstat` COMMAND

OPTIONS | DESCRIPTION | 
--- | --- | 
`-n` | Display numerical addresses and ports. |
`-i` | Display a list of network interfaces. |
`-r` | Display the route table (`netstat -rn`). |
`-p` | Display the PID and program used. |
`-l` | Display listening sockets (`netstat -nlp`). |
`-t` | Limit the output to TCP (`netstat -ntlp`) |
`-u` | Limit the output to UDP (`netstat -nulp`) |

The `netstat` command can be used to collect a wide variety of network information. 


## PACKET SNIFFING WITH `tcpdump` COMMAND

When you need to examine the contents of the network traffic.

`tcpdump` is one of the older and most commonly installed tools. 

Requires root privileges to run. 

OPTIONS | DESCRIPTIONS | 
--- | --- | 
`-n` | Display numerical address and ports. | 
`-A` | Display ASCII(text) output. | 
`-v` | Verbose mode. Produce more output. | 
`-vvv` | Even more verbose output. | 


## `telnet` COMMAND

The `telnet` command is practically obsolete. 

Examples:
```
$ telnet google.com 80
```