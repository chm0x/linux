# Environment Variables 

* Name/Values pairs. 
* It can change how an application behaves. 

Example:
```
EDITOR=nano
```

Commands
* **printenv**

```
$ printenv
```

## Viewing Variables

```
$ printenv EDITOR

$ echo $USER
```

## Creating environment Variables 

* DO NOT use SPACES around the equals sign(=).
* DO NOT use single quotes('').

Syntax: 
```
export VAR="value"
```

## Removing Environment Variable

* DO NOT use dollar sign ($).
Syntax: 
```
unset VAR_NAME
```

## Persisting Environment Varaibles

As the same as before, using `.bashp[_profile]` files. 

```
export TZ="Mexico/City"
```