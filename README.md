# Regex snippets


# Overview

* [Linux command outputs](#linux)
    * [ls -l output](#ls--l-output)
    * [cat /etc/passwd](#cat-etcpasswd-output)
* [Security](#security)
    * [Shellcode](#shellcode)
* [Hashes](#hashes)
    * [MD5](#md5)
    * [Drupal 7 (old)](#drupal-7-old)
* [Encodings](#encodings)
    * [Base64](#base64)
* [Filesharing](#filesharing)
    * [TV-Shows](#tv-shows)
* [General stuff](#general-stuff)
    * [Email](#email)
    * [URLs](#urls)
    * [MAC-Address](#mac-address)

---
<br>


# Linux
### `ls -l` output
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

(This pattern can also be used for FTP server listings)

##### Pattern
```
([-|d|l|p|s|b|D])([-|r|w|x|s|t]{9})\s+?(\d+?)\s+?(\w+)\s+(\w+)\s+?(\d+)\s+?(\w{3})\s+(\d+)\s+?(\d{4}|\d{2}\:\d{2})\s(.*)
```

##### Example
This version supports the `ls -l` and `ls -lh` command: https://regex101.com/r/cN5gG2/2

---
<br>

### `cat /etc/passwd` output
The following groups are matched:

1. Username
2. Password (Encrypted password or `x` if it's stored in the shadow file)
3. User ID (UID)
4. Group ID (GID)
5. User ID Info
6. Home directory
7. Command/Shell

##### Pattern
```
(.+)\:(.+?)\:(\d+)\:(\d+)\:(.*?)\:(.*?)\:(.*)
```

##### Example
https://regex101.com/r/dK9pG0/1

---
<br>

# Security
### Shellcode
Finds shellcode, it's not used to match a complete shellcode buffer
but instead to check if there is shellcode in a document.

##### Pattern
```
((?:\\x[a-fA-F0-9]{2})+)
```

##### Example
https://regex101.com/r/kU7cZ8/1

---
<br>

# Hashes
### MD5
Checks for hexadecimal values which must be 32 chars long.

##### Pattern
```
[a-fA-F0-9]{32}
```

##### Example
https://regex101.com/r/tU4fA1/1

---
<br>

### Drupal 7 (old)
Matches old Drupal 7 password hashes.
The following groups are matched:

1. Hash type (always "$S$")
2. Number of log2 rounds (X) based on the position of the char in this list
   './0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz', example "D" -> 15
3. Salt
4. SHA512 hash using 2^X rounds

(Source of the parts of the hash from  [stackoverflow](http://stackoverflow.com/questions/5031662/what-is-drupals-default-password-encryption-method#answer-19274472)

##### Pattern
```
(\$S\$)([0-9A-Za-z\.\/])([0-9A-Za-z\.\/]{8})([0-9A-Za-z\.\/]{43})
```

##### Example
https://regex101.com/r/zA9zK8/1

---
<br>

# Encodings
### Base64
Searches for base64 encoded data.

##### Pattern
```
((?:[a-zA-Z0-9\+\/]{4}){4,}(?:[a-zA-Z0-9\+\/]{0,3}\={1,3})?)
```

##### Example
https://regex101.com/r/vS8wI0/1

---
<br>


# Filesharing
### TV-Shows
Matches the following groups:

1. Name
2. Season
3. Episode
4. Quality (if it exists, e.g. 720p, 1080p, ..)
5. Mixed stuff (if it exists. Might contain the quality, file encoding etc.)
6. Groupname
7. Packager (if it exists [xyz])
8. Fileextension

##### Patterns
Version 1: Less restrictive

```
(.+)(?:[Ss _\.](\d{2,})[Ee _\.](\d{2,}))[\. _](\d{3,4}p)?(.+)?.*?\-(.+?)(?:\[(.+)\])?\.(\w+)
```

Version 2: Restrictive
```
([a-zA-Z0-9\.\- ]+)[\. _](?:[Ss](\d{2,})[Ee](\d{2,}))[\. _](\d{3,4}p)?(.+)\-([a-zA-Z0-9]+)(?:\[(.+)\])?\.(mkv|mp4|avi)
```

##### Examples
Version 1: https://regex101.com/r/eO0lY8/4

Version 2: https://regex101.com/r/eO0lY8/3

---
<br>

# General stuff
### Email
Matches the following groups:

1. Username
2. Domain

##### Pattern
```
([a-zA-Z0-9_\-\.]+)\@(.+\..{2,})
```

##### Example
https://regex101.com/r/kR6yE2/1

---
<br>

### URLs
Matches the following groups:

1. Scheme (http, https, ...)
2. Domain
3. Path (if any)
4. GET-Arguments (if any)
5. Fragment (if any)

##### Pattern
```
(\w{3,})\:\/\/(?:(.+?)(\/.+)?(\?.+)(\#.+)|(.+?)(\/.+)(\?.+)|(.+?)(\/.+)(\#.+)|(.+?)(\/.+)|[^\s\/\#\?]+)
```

##### Example
https://regex101.com/r/cL5kR3/7

---
<br>

### MAC-Address
Matches each value of a MAC-Address.

The matched formats are:
`MM:MM:MM:SS:SS:SS`, `MM-MM-MM-SS-SS-SS` and `MMMM.MMSS.SSSS`

##### Pattern
```
(?<![a-fA-F0-9])(?:([a-fA-F0-9]{2})[\:\-]([a-fA-F0-9]{2})[\:\-]([a-fA-F0-9]{2})[\:\-]([a-fA-F0-9]{2})[\:\-]([a-fA-F0-9]{2})[\:\-]([a-fA-F0-9]{2})|([a-fA-F0-9]{4})\.([a-fA-F0-9]{4})\.([a-fA-F0-9]{4}))(?![a-fA-F0-9])
```

##### Example
https://regex101.com/r/lF5pJ4/2

---
<br>


 
