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








