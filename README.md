# Regex snippets


## Overview

[FTP](#FTP)


## FTP
### ls output
The pattern below matches the following match groups:
1. Type of element: File, directory, symlink, named pipe, socket, block device or door.
2. Permission
3. Number of nodes (?)
4. User
5. Group
6. Filesize
7. Month (3 chars)
8. Day
9. Year (or in some cases a time in the format HH:MM)
10. Filename

#### Pattern
```
([-|d|l|p|s|b|D])([-|r|w|x|s|t]{9})\s+?(\d+?)\s+?(\w+)\s+(\w+)\s+?(\d+)\s+?(\w{3})\s(\d+)\s+?(\d{4}|\d{2}\:\d{2})\s(.*)
```

#### Example
https://regex101.com/r/cN5gG2/1
