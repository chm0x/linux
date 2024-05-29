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

The clientt will be able to use that IP address for the lease expiration time configured by the DHCP