# Manipulating Files

## Removing Files

```
$ rm [filename] # Remove file

$ rm -r [dir] # Remove the directory and its content recursively. 

$ rm -f [filename] # Force removal and never prompt for confirmation
```

## Copying Files

```
$ cp [source_file] [destination_file] # Copy the source_file to the destination_file

$ cp [src_file1] [src_fileN...]  [dest_dir] 
# Copy number of source_files to destination directory.

$ cp -i # Run in interactive mode. 

$ cp -r [source_directory] [destination] 
# Copy src_directory recursively to destination.
```

## Moving and Renaming Files. 

```
# Move or rename files and directories.
$ mv 

# Move to destination
$ mv [source] [destination]

# Run in interactive mode
$ mv -i [source] [destination]
```

## Sorting data

```
# Sort text in file.
$ sort [file]

# Sort by key. F is the field number. 
$ sort -k F

# Sort in reverse order 
$ sort -r

# Sort unique
$ sort -u
```

## Creating a Collection of Files. 

Create(c), extract(x) or list(t) contents of a tar archive using pattern, if supplied.
```
$ tar [-] c|x|t f [file(s)_to_compress] [pattern]

# Create a tar file
$ tar -cf mytarname.tar data.txt data2.txt directory_name/

# Create a tar file with compress
$ tar -czf mytarname.tar [files/dirs]

# Check the tar file
$ tar -tf mytarname.tar

# Extract the tar file
$ tar -xvf mytarname.tar
```

option | Definition | 
--- | --- | 
c | Create a tar archive. | 
x | Extract files from the archive. | 
t | Display the table of contents (list). | 
v | Verbose | 
z | Use compression | 
f [filename] | Use this `file` | 


## Compressing Files to Save Space

```
# Compress Files.
$ gzip [files/dir]

# Uncompress Files. 
$ gunzip [file.zip]

# Concatenates compressed files. 
$ gzcat [files]

# Concatenates compressed files.
$ zcat [files]

# Tar with gzip
$ tar -zcf file_name.tgz
```

## Disk Usage

```
# Estimates file usage.
$ du

# Display sizes in Kilobytes
$ du -k

# Display sizes in human readable format 
$ du -h
```

