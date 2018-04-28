# Linux Command Line

## Basics

Clear Screen

```
CTRL + L
```

Current user

```
whoami
```

Looking up usage of tools, commands, and utilities:

```
man cd
man grep
man [whatever]
```

## Acount Stuff

Adding a new user

```
useradd -d [home] [login]
```

Changing Passwords

```
passwd [login_name]
```

## Filesystem Stuff + Navigation

Display contents of files:

```
cat [file]
less [file]
```

Switching Directories

```
cd
```

List current directory

```
pwd
```

List directory contents:

```
ls
ls -la
```

Copying Files:

```
cp /etc/shadow /tmp/shadow_copy
```

Creating a file:

```
touch [filename]
```

Renaming a file:

```
mv [file1.txt] [file2.txt]
```

## Working w/ Files and Searching, etc.

Finding patterns within files:

### grep

Note: -A and -B specify the amount of lines to show after, or before, the line that matches the supplied pattern.

```
cat [file] | grep "pattern"
cat [file] | grep "pattern" -A [number of lines]
cat [file] | grep "pattern" -B [number of lines]
```

### Viewing and Searching Processes

```
ps -eaf
ps -eaf | grep crypto
```

Show all processes belonging to a user in tree form:

```
ps -u [user] --forest
```

Top command (functions like an interactive ps):

```
top
```

Displaying help in top:

```
h
````

Killing a process in top:

```
k
[enter PID]
```

### Changing IP address and networking data

```
ifconfig [interface] [IP Address] netmask [netmask]
```

### Working with tar and file compression

tar a folder/file:

```
tar -cf [file[s] or folder]
```

untar (extract):

```
tar -xf [file[s] or folder]
```

gzip a folder/file:

```
gzip [folder/file]
```

Unzip a compressed gzip:

```
gunzip [folder/file]
```

bzip2

unbiz2


### Working with vim text editor

Vim (vi improved) is a powerful and popular text editor.

Creating and editing a new file:

```
vim [filename]
```

Begin writing/editing the file:

```
i
```

Typing the letter "i" puts you into "Insert" mode, which will be indicated in the bottom-left of the vim editor (called the status).

Use the ":" (colon) key to enter the command mode that allows your to manipulate vim.

Writing and quiting a file:

```
:wq
```

Substitution in vi (in ESC mode). Find each occurrence of 'foo' (in all lines), and replace it with 'bar'.

```
:%s/foo/bar/g
```
or

```
:1,$s/foo/bar/g
```

Remove ^M characters while in vi (in ESC mode). To enter ^M, type CTRL-V, then CTRL-M. That is, hold down the CTRL key then press V and M in succession.

```
:%s/^M//g
```

### Linux Command Line Analysis Tools

#### cut

-d: specify delimiter
-f: specify field

```
cut -f 3 -d " "
```

```
cut -f 1-4 -d "."
```

#### sort

-n: numeric sort
-r: reverse sort
-u: show only unique lines

```
tcpdump -r capture.pcap -n 'dst port 443' | cut -f3 -d "." | sort -u
```

#### uniq

-c: counts how many unique lines entries

```
[...] | sort -u
```

#### grep

-v: skip if matches pattern
-i: case insensitive

```
grep -i "hacker" fileinput
```

<<<<<<< HEAD
#### Head and Tail

Used to view the beginning or ending entries of files/logs:

```
tail /var/log/messages
```

### Linux Logging

Most logs are contained under "/var/log"

Commong logs:

1. Cron
2. messages (general purpose syslog)
3. secure (security related events, like using su to become root)


=======
#### sed 
>>>>>>> cd947ef9e8dc517e74bc25e03f08ad14de1434ac

Replacement of text in a command or file. Extremely useful when chained together with cut, grep, etc

Delete lines matching pattern
```
sed '/pattern/d' file.txt
```

Replace every occurrence of Nick with John in the report.txt file and dump to STDOUT
```
sed 's/Nick/John/g' report.txt
```

Replace every occurrence of Nick with John from the report.txt file and place the contents in a new file.
```
cat report.txt | sed 's/Nick/John/g' > report_new.txt
```

Use sed to remove the ^M characters. To enter ^M, type CTRL-V, then CTRL-M. That is, hold down the CTRL key then press V and M in succession.

```
sed -e "s/^M//" filename > newfilename
```

# Other Tools to Master

Here are a list of tools that appear in the lab exercises that are not explictly listed in the GIAC GSE exam objectives (https://www.giac.org/certification/security-expert-gse).

## base64

```
base64 -d [file containing base64]
```

## xxd

xxd is used to make a hexdump or to revert hexdumps to something readable.
The following example reverts (-r) hex into something readable. The "-p" specifies postscript, aka plain hexdump style.

```
xxd -r -p
```

