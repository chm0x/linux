# Examples


## Asterisk

```
$ ls *.txt

$ ls a*.txt
```

## Question mark

```
$ ls ?

$ ls ??

$ ls a?.txt
```

## Character class

```
$ ls c[aeiou]t

$ ls c[aeiou]*
```

## Range

```
$ ls [a-d]*

$ ls [[:digit:]]
```

# With MV 

```
$ mv *.txt destination_dir

$ mv *.mp3 destination_dir

$ mv *[[:digit:]] destination_dir
```

# With RM

```
$ rm ??


```