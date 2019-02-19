# How to create a .tar.gz file by using the Date command
```$ tar -zcvf `date +%Y`-MORE-DESCRIPTION.tar.gz `%Y`*.CHOOSE-FILE-TYPE```

### Options:
`-c` : Creates archive  
`-x` : Extract the archive  
`-f` : Creates archive with given filename  
`-t` : Displays or lists files in archived file  
`-u` : Archives and adds to an existing archive file  
`-v` : Displays verbose information  
`-A` : Concatenates the archive files  
`-z` : Zip, tells tar command that create tar file using gzip  
`-W` : Verify a archive file  
`-r` : Update or add file or directory in already existed .tar file  
`%F` : Full date; same as `%Y-%m-%d`  

CHOOSE-FILE-TYPE (e.g. `jpg`, `json`, `xml` etc)
