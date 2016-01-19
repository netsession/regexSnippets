# Regex snippets


## Overview

* [Linux command outputs](#linux)
    * [ls output](#ls-output)
* [Hashes](#hashes)
    * [md5](#md5)
* [General stuff](#general-stuff)
    * [email](#email)
    * [URLs](#urls)



## Linux
### `ls` output
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


## Hashes
### MD5
Checks for hexadecimal values which must be 32 chars long.

#### Pattern
```
[a-fA-F0-9]{32}
```

#### Example
https://regex101.com/r/tU4fA1/1



## General stuff
### Email
Matches the following groups:

1. Username
2. Domain

#### Pattern
```
([a-zA-Z0-9_\-\.]+)\@(.+\..{2,})
```

#### Example
https://regex101.com/r/kR6yE2/1


### URLs
Matches the following groups:

1. Scheme (http, https, ...)
2. Domain
3. Path (if any)
4. GET-Arguments (if any)
5. Fragment (if any)

#### Pattern
```
(\w{3,})\:\/\/(.+?)(?:(\/.+)?(\?.+)(\#.+)|(\/.+)(\?.+)|(\/.+)(\#.+)|(\/.+)|\s)
```

#### Example
https://regex101.com/r/cL5kR3/5
