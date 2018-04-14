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









