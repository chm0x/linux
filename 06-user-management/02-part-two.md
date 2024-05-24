# MANAGING USERS AND GROUPS 

## GROUPS

### `/etc/group` FILE

Group details are stored in the `/etc/group` file. 

Format: 
```
group_name:password:GID:account1,accountN
```

Example:
```
root:x:0
sales:x:1001:john,mary
```
Root's default is always 0(zero) for GID.

The password field is used for privileged groups, rarely ever used. 

That information of password is stored in the `/etc/gshadow` file. 


### DISPLAY THE GROUPS THAT AN ACCOUNT BELONGS

```
$ groups root
```
