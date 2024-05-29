# DNS HOSTNAMES
 
**DNS** stand for **Domain Name System**.

The primary purpose of DNS is to translate human-readable names into IP addresses and viceversa, means translate IP to human-readable.

## FQDN = Fully Qualified Domain Name

The Fully QUalified Domain Name (FQDN) of a host also contains a **domain name** and a **top-level domain name**.

Each section of FQDN is separated by a period or dot(.).

Example:
```
webprod01.mycompany.com
```

## TLD = Top-Level Domain

It is the rightmost portion of a DNS name.

Common Top-level Domain include **`.com`, `.net`, and `.org`**.


## DOMAIN

* Below(to the left of) TLD

A domain appears just to the left of a top-level domain. 

This is often a company name, an organization name, or even a brand name. 

## SUB-DOMAIN

* Below (to the left of) the domain. 

However, Domains can be further divided into sub-domains

Example:
```
webprod01.ny.us.my.company.com
```

The sub-domains is used to identify where a server is located. 

I.e: Country, state.

Sub-domains do not have to correspond to geographical regions; they can be anything the DNS administrator has configured. 

## DISPLAY THE CURRENT HOSTNAME

Ways to display a hostname:
```
$ hostname

$ uname -n

# FQDN
$ hostname -f
```

### TEMPORARLY CHANGE THE HOSTNAME

```
$ hostname webprod01

$ echo 'webprod01' > /etc/hostname

# To Persistent the Hostname
# Red Hat
$ vi /etc/sysconfig/network
HOSTNAME=webprod02
```

## Resolving or Look up DNS Name

* `host`
* `dig`

Examples:
```
$ host www.mycompany.com
# Output: webprod01.mycompany.com has address 1.2.1.6

$ host 1.2.1.6 
# Output: 6.1.2.1 in-addr.arpa domain name pointer www.company.com
```

## THE `/etc/hosts` FILE

```
# Format 
IP FQDN alias(es)
10.11.12.13 webprod02.mycorp.com webprod02
```

Now you can refer to the host by name.
```
webprod02.mycorp.com OR webprod02
```

`/etc/hosts` is local to your linux system. It doesn't propagate the rest of the network. 

This can be useful if you want to access computers that do not have DNS hostnames for example. 

Also, it's common to use `/etc/hosts` entries to override the DNS entry of a system. 

Adding an entry to the `/etc/hosts` file does not add an entry into DNS. 

Examples in the `/etc/hosts` file:
```
127.0.0.1       localhost
1.2.1.6         webprod01.mycompany.com webprod01
10.11.12.14     webprod02.mycompany.com webprod02
10.11.12.15     webprod03.mycompany.com webprod03
10.11.13.7      dbcluster
```

## THE `/etc/nsswitch.con` FILE

**NSS** stand for **Name Service Switch**


Typically the `/etc/hosts` file is checked first before a DNS server is queried, and you can change the behavior by editing the `/etc/nsswitch.conf` file. It controls the order in which lookups are performed.

The hosts line determines the order for name resolution. 

Sample:
```
hosts: files dns

hosts: files nis dns
```
For example, if you have `hosts: files dns`, the `/etc/hosts` will be searched first, and then **dns**. 

If you have `hosts: files nis dns`, the `/etc/hosts` will be searched first, if an IP address is found there, that IP address is used and the searchs stops; if not, then DNS is required. 