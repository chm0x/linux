# DHCP, DYNAMIC AND STATIC ADDRESSING

* Network ports 
* DHCP 
* Static IP addresses
* ifup/ifdown
* GUI/TUI tools


## NETWORK PORTS 

Just like IP addresses identify hosts on a network ports. Identify the services on a host. 

When a service start on a system, it binds itself to a port and listens for traffic destined for its port. 

**Ports range from 1 to 65535**

And the ports from 1 to 1,023 are well-known ports. 

* 22  - SSH
* 25  - SMPT
* 80  - HTTP
* 143 - IMAP
* 389 - LDAP
* 443 - HTTPS

These ports, **range from 1 to 1,023**, are pre-assigned ports and are used for common system services. These port are also called privileged ports, *since it requires superuser privileges to open these ports*.

Ports above 1,024 can be opened and used by normal users on a system and are called unprivileged ports. 

When you type `https:www.mybank.com`, the computer translates `www.mycompany.com` into an *IP Address*. Then your web browser initiates a request to that IP address on **port 443** since you specified the HTTPS protocol. 


## `/etc/services`

The `/etc/services` file translates human readable names into port numbers. 

## DHCP

**DHCP** stand for **Dynamic Host Configuration Protocol**. 

*DHCP is primarly used to assign IP addresses to host on a network*.

When a DHCP client wants to request an IP address, it sends a broadcast message looking for a DHCP server. *The DHCP server then responds to the client and provides it with an IP address and other additional information such as the netmask, the gateway and the DNS servers to use for name resolution*. 

* DHCP servers assign IP address to DHCP clients:
    * IP Address
    * Netmask
    * gateway 
    * DNS servers 

The IP address is signed to a DHCP client is **leased** from the DHCP server.

The client will be able to use that IP address for the lease expiration time configured by the DHCP server.

If the DHCP client wants to continue using the IP address beyond the lease expiration time, it must send a renewal request to the DHCP server. If no renewal received by the DHCP server, it will place this IP address back into the pool of available addresses. 

### CONFIGURING A DHCP CLIENT - RHEL

Only Red Hat Enterprise Linux's commands:
```
$ ifconfig -a

# Or. Ubuntu too. 
$ ip link
```

Files:
```
/etc/sysconfig/network-scripts/ifcfg-DEVICE
/etc/sysconfig/network-scripts/ifcfg-eth0
/etc/sysconfig/network-scripts/ifcfg-enp5s2
BOOTPROTO=dhcp
```

### CONFIGURING A DHCP CLIENT - UBUNTU

File:
```
# OLD
/etc/network/interfaces

# MOdern
/etc/network/
/etc/netplan/
/etc/netconfig 
```

### ASSIGNING A STATIC IP ADDRESS - RHEL

Only RHEL.
File:
```
/etc/sysconfig/networks-scripts/ifcfg-eth0
```

Content:
```
DEVICE=eth0
BOOTPROTO=static
IPADDR=10.109.155.174
NETMASK=255.255.255.0
NETWORK=10.109.155.0
BROADCAST=10.109.155.155
GATEWAY=10.109.155.1
ONBOOT=yes
```

To set permanent, set `yes` on `ONBOOT`. 


### ASSIGNING A STATIC IP ADDRESS - UBUNTU

File:
```
/etc/network/interfaces
```

Content:
```
auto eth0
iface eth0 inet statuc
        address 10.109.155.174
        netmask 255.255.255.0
        gateway 10.109.155.1
```

### MANUALLY ASSIGNING AN IP ADDRESS WITH `ip` COMMAND

Format:
```
$ ip address add IP[/NETMASK] dev NETWORK_DEVICE
```

Examples:
```
$ ip address add 10.11.12.13 dev eth0

$ ip address add 10.11.12.13/255.255.255.0 dev eth0 

# When you finized to add an IP, the NEXT is:
$ ip link set eth0 up
```

#### WITH `ifconfig` COMMAND

Format:
```
ifconfig NETWORK_DEVICE addr netmask SUBNET_MASK
```

Example:
```
$ ifconfig eth0 10.11.12.13
$ ifconfig eth0 10.11.12.13 netmask 255.255.255.0

# next:
$ ifconfig eth0 up
```

### `ifup` / `ifdown` COMMANDS

Examples:
```
$ ifup eth0
$ ifup enp5s2

$ ifdown eth0
$ ifdown enp5s2
```

### GUI/TUI(Textual User Interface) TOOLS

* Red Hat:
    * nmtui
    * system-config-network
* SUSE:
    * YaST
* Ubuntu:
    * No official tool available