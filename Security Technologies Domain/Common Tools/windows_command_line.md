# Windows Command Line

## Basics

Clear Screen

```
cls
```

Current user

```
whoami
```

## Networking Basics

Listing TCP/IP networking data related to interfaces

```
ipconfig
ipconfig /all
```

Listing DNS information

```
ipconfig /displaydns
```

### netstat

Use netstat to display active TCP connections, information on ports, and other protocol statistics.

```
netstat
```

Active/all connections

```
netstat -a
```

Display top active connections with ownership (PIDs)

```
netstat -no
```

Combining previous steps

```
netstat -ano
```

Analysis tip:

Using something like Task Manager (or WMIC or PowerShell) to correlate the process associated with active PIDs (from netstat) is an extremely beneficial way to correlate and further investigate potentially interesting network connections.

Listing routing table:

```
netstast -r
```

Analysis tip:

Piping the results of netstat to the "find" command is a useful way to hone in on ports of interest:

```
netstat -an | find "80"
```

### Ping Command

Ping is the defacto tool for testing TCP/IP routing and availability from one host to another. Windows' ping utility relies on ICMP packets:

```
ping [IP address]
```

## Filesystem Stuff + Navigation

Switching directories

```
cd
```

List current directory and files

```
dir
```








