# WILDCARDS 

Wildcards can be used with most command: 
* ls 
* rm
* cp


## * (asterisk) - Matches Zero or MOre Characters

* \*.txt
* a\*
* a\*.txt

## ? (question mark) - Matches exactly one character. 

* \?.txt
* a\?
* a\?.txt

## [] - A character class. 

Matches any of the characters included between the brackets. Matches exactly one character. 

I.E:
* [aeiou]
* ca[nt]\*
    1. results: 
        * can
        * cat
        * candy
        * catch

## [!] - Not Included

Matches any of the characters NOT INCLUDED  between the brackets. Matches exactly one character. 

I.E 
* [!aeiou]*
    1. Results:
        * baseball
        * cricket

## Ranges

Use two characters separated by a **hyphen** to create a range in a character class. 

IE
```
$ [a-g]*
# Matches all files that start with 
# a,b,c,d,e,f or g.

$ [3-6]*
# Matches all files that start with 
# 3,4,5 or 6.
```

## Named Character Classes

```
# Matches alphabetic letters.
# Both lower and upper cases.
$ [[:alpha:]]

# Matches alphanumeric characters.
# Matches Alpha and digits
$ [[:alnum:]]

# Represent the number and decimal 
# from 0 to 9.
$ [[:digit:]]

# Matches lower case letters. 
$ [[:lower:]]

# Matches wide space.
# Such as spaces, tabs and newline characters. 
$ [[:space:]]

# Matches upper case letters. 
$ [[:upper:]]
```

## \ Escape character 

Use if you want to match a wildcard character. 

i.e : Match all files that end with a question mark:
```
$ *\?
# Results: done?.txt
```





