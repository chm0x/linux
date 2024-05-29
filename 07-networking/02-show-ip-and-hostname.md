# DNS AND HOSTNAME

You will learn how to determining your IP address. 

## DETERMINING YOUR IP ADDRESS


### `ip address`
To show your current IP address:

There is a more way to show
```
$ ip address

$ ip addr 

$ ip a

$ ip address show 
# or
$ ip a s
```

Output devices:
```
1. lo

2. eth0
```

The `lo` device is called the loopback device. This is a special virtual network interface that a Linux System uses to *communicate with itself*. 

The `eth0` device is an actual hardware device and his IP address. 


### `ifconfig`

The `ifconfig` command is considered to be deprecated but not yet. 

## HOSTNAME

A **host** is a device connected to a network. A *host* is a device with an IP address. 

And **hostname** is simply a human-readable name that corresponds to an IP address. 

Example:
```
webprod01 = 10.109.155.174
```

