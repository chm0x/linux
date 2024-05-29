# NETWORKING

## TCP/IP

* **TCP** stand for *Transmission Control Protocol*. 
* **IP** stand for *Internet Protocol*. 

They are used for network communications. 

Today **TCP/IP** is the de facto standard for transmitting data over networks. 

**TCP** controls data exchange. 


**IP** sends data from one device to another. 

* **HOSTS** are devices on a network that have an IP address. 

### TCP 

It is responsible for establishing and maintaining network conversations, so that two devices can exchange data. 

### IP

The IP is the responsible for sending data from one device to another device on a network. 

Each one of these network devices is known as a host and has at least one IP address. 

For a device on a network to communicate properly, it needs 3 pieces of information:

1. **IP Address**
    * Example: 199.83.131.186
2. **Subnet Mask**
    * Example: 255.255.255.0
3. **Broadcast Address**
    * Example: 199.83.131.255
4. octet.octet.octet.octet

Each one of these numbers is comprised of four octets separated by a dot. An octet represents eight-bits and therefore can have a value starting at 0 and going up to 255. 

#### IP NETWORKING

* Each must be unique for proper routing. 
* Address Class
    * Used to determine the network address and host address. 

IP addresses are comprised of two parts: 
1. The first part of an IP address is the **Network Address**.
2. The second part is the **Host Address**. 

The network portion of the IP address tells routers what network the host belongs to and thus where to route data that is destined for that host. 

The host address tells routers the specific device that the data should be delivered to. 

For routing to work properly, each group of devices, or network, needs to have a unique network address. Also each devices within that network needs to have a unique host address. 

### CLASSFUL NETWORKS

Class | Network | Hosts Allowed | 
--- | --- | --- | 
A | 1.0 &rarr; 127.0 <br/> i.e: 17.24.88.9 | 16,777,216 |
B | 128.0 &rarr; 191.255 <br/> i.e: 183.194.46.31 | 65,536 | 
C | 192.0.0 &rarr; 233.255.255.255 <br/> i.e: 199.83.131.186 | 255 |  


An IP address with a first octet that falss between 1 and 127 is a **Class A** IP address. For example the ip address of `17.24.99.9` belongs to a class A.

**Class B** addresses begin with `128.0` and end at `191.255.` For example, `183.194.46.31` belongs to a **Class B** network. 

**Class C** addresses start with `192.0.0` and end with `233.255.255`. For example IP `199.83.131.186` belongs to **Class C** network.


A class determines the possible number of networks and the addressable space per network. 

For example, A **Class A** can accoommodate about 16 million hosts addresses. 

A **Class B** can have up to 65,536 hosts in it. Finally a **Class C** network can address 255 hosts. 

### SUBNET MASK

This table lists the subnet mask used for each of the network classes. The network portion of an IP address corresponds to the `255`s in the subnet mask. 

Class | Subnet Mask | 
--- | --- | 
A | 255.0.0.0 | 
B | 255.255.0.0 | 
C | 255.255.255.0 | 



For example, the first octet of a Class A network is the network portion while the remaining octets are the **host** portion. 

For **Class B** networks, *the first two octets are for network addresses* while *the last two octets are for host addresses*.

Finally **Class C** networks use the first three octets for the network and just the last octet for the host addresses.  

Example: 
255 | 255 | 0 | 0 | 
--- | --- | --- | --- | 
183 | 194 | 46 | 31 

This IP address is a **Class B** network, the **network port** of the address is `183.194` and the **host portion** is `46.31`. 

The netmask or subnet mask is listed right above the IP address, you can see how the network portion aligns with the 255 values and the host portion aligns with the 0 values of the subnet mask. 

### BROADCAST ADDRESSES

A broadcast address is a special logical address used to send data to all hosts on a given network. 

In addition to their own IP Address all network host receive data sent to the broadcast address. You can quickly determine the broadcast IP address by using the value of 255 in the octets where there are 0's in the subnet mask.

Examples: 

CLASS | NETWORK | SUBNET MASK | BROADCAST | 
--- | --- | --- | --- | 
A | 17.0.0.0 | 255.0.0.0 | 17.255.255.255 | 
B | 183.194.0.0 | 255.255.0.0 | 183.194.255.255 | 
C | 199.83.131.0 | 255.255.255.0 | 199.83.131.255 | 


### CLASSLESS INTER-DOMAIN ROUTING / CIDR (Enrutamiento interdominio sin clases)

**CIDR** stand for Classless Inter-Domain Routing. 

It allows network to be subdivided regardless of their traditional class. These subdivided networks are called subnets. 

Example:

* IP: 121.67.198.94
    * Class A network: 121.0.0.0
    * Class A subnet: 255.0.0.0
    * Class A broadcast: 121.255.255.255
* IP: 121.67.198.94 SUBNET: 255.255.255.0
    * CIDR network: 121.67.198.0
    * CIDR subnet: 255.255.255.0
    * CIDR broadcast: 121.67.198.255



### RESERVED PRIVATE ADDRESS SPACE

There are ranges of IP addresses that are dedicated for use in private networks. 

Common uses: in your company and your home. 

Class | Range | Private Address Space | 
--- | --- | --- | 
A | 1.0.0.0 &rarr; 127.255.255.255 | 10.0.0.0 &rarr; 10.255.255.255 | 
B | 128.0.0.0 &rarr; 191.255.255.255 | 172.16.0.0 &rarr; 172.16.255.255 | 
C | 192.0.0.0 &rarr; 233.255.255.255 | 192.168.0.0 &rarr; 192.168.255.255 | 

These private addresses are also called non-routable IPs since they are not routed through the public internet. 

Referred to as `RFC1918` addresses, which refers to the `RFC1918` standards document where these private ranges were initially defined. 

