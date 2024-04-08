# INSTALLING AND MANAGING SOFTWARE 

## PACKAGE

A collection of files. 

Data/Metadata: 
* Package description. 
* Version. 
* Dependencies. 

## PACKAGE MANAGER

installs, upgrades, and removes package. 

manages dependencies. 

Keeps track of what is installed. 

## PACKAGE TYPES

### RPM distro
*RPM* Stand for **Red Hat Package Manager**. 

* RHEL, CentOS, AlmaLinux, Rocky Linux, and Oracle Linux


#### yum command - RHEL 7 / CentOS 7 & earlier

```
# Search for string. 
$ yum search [string]

# Display info. 
$ yum info [package]

# Install package
$ yum install [-y] package_name

# Remove package
$ yum remove package_name

# Update package
$ yum upgrade [package]
```

Examples:
```
$ yum info "bash*" # Use the double quotation mark.
```


#### dnf - RHEL 8 / CentOS 8 & Later

dnf has become the default package management command. 

```
# Search for string. 
$ dnf search [string]

# Display info. 
$ dnf info [package]

# Install package
$ dnf install [-y] package_name

# Remove package
$ dnf remove package_name

# Update package
$ dnf upgrade [package]
```

#### rpm - command

```
# List all installed package
$ rpm -qa

# List the file's package
$ rpm -qf /path/to/file

# List the package's files. 
$ rpm -ql package

# Install the package
$ rpm -ivh package.rpm

# Erase(Uninstall) the package
$ rpm -e package
```


### DEB distro

Debian, Ubuntu, and Linux Mind






