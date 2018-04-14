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

