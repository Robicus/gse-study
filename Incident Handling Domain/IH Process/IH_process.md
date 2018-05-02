# Incident Handling Process

## Exam Outcome

Demonstrate mastery of the Incident Handling process.

## Incident Handling Fundamentals

What is an "incident"?

An adverse event in an information system, and/or network, or the threat of the occurence of such an event.

What is an "event"?

An event is any observable occurrence in a system and/or network.

## 6 Phases of Incident Response (IR)

1. Preparation
2. Identification
3. Containment
4. Eradication
5. Recovery
6. Lessons Learned

## 1. Preparation

The goal of the preparation phase is to get our team ready to handle incidents.

The main components of preparation include people, policy, data, software/hardware, communications, supplies, transportation, space, power and environmental conrtols, and documentation.

A few tips to remember when conducting incident response:

- Stay calm
- Don't move too fast
- Maintain excellent notes - always think about the "who, what, when, where, and how".
- "If you are going too fast to take notes, you are going too fast!"

## 2. Identification - Technical - Windows

Unusual network usage - looking at file shares, open sessions, and NetBIOS activity:

```
net view \\127.0.0.1
net session
net use
nbtstat -S
```

Look for unusual listening TCP and UDP ports:

```
netstat -nao
```

Looking for unusual processes:

```
taskmgr.exe
```

```
tasklist -v
```

```
Get-Process
```

```
wmic process list full
```

Looking for unusual services:

```
services.msc
```

```
net start
```

```
sq query | more
```

```
tasklist /svc
```

```
Get-Service
```

Loooking for unusual Registry Keys:

```
req query [key]
```

```
reg query hklm\software\microsoft\windows\currentversion\run
reg query hklm\software\microsoft\windows\currentversion\run\runonce
reg query hklm\software\microsoft\windows\currentversion\run\runonceEx
```

Looking at Scheduled Tasks:

```
schtasks | more
```

Looking at Unusual Accounts:

```
net localgroup administrators
```

## 2. Identification - Technical - *Linux

Running processes:

```
ps aux
```

Show all filesd and ports:

```
lsof -p [pid]
```

Unusual files:

```
find / -uid 0 -perm -4000 -print
find / -size +10000k -print
find / -name " " -print
```

```
netstat -nap
```

Unusual scheduled tasks:

```
crontab -u rooot -l
cat /etc/cronttab
ls /etc/cron.*
```

Unusual accounts:

```
sort -nk3 -t: /etc/passwd | less
```

Others:

```
uptime
free
df
```

## Containment

The goal of containment is to stop the bleeding - prevent the attacker from getting any deeper into the impacted system, or spreading to other systems.

Containment sub-phases:

1. Short-term containment
2. System back-up
3. Long-term containment

### Containment - Short term:

Possible actions for short-term:

- Disconnect network cable
- Pull the power cable (note: will lose volatile memory)
- Isolate the switch port / VLAN

### Containment - Long term:

Possible actions for long-term:

- Patching
- Null routing
- Changing passwords
- Apply trust relationships
- Remove accounts used by the attacker
- etc.

## Eradication

The goal of eradication is to get rid of the attacker's artificats on the machine.

- Restoring from backups
- Removing malicious software
- Improving defenses

## Recovery

The goal of the recovery phase is to put the impacted systems back into production in a safe manner.

## Lessons Learned

The goal of Lessons Learned is to document what happened and improve capabilities.

## Reporting

### 503 Reporting Tips

"Your report should include what happened, what you believe occurred, who - what IP addresses were involved and perhaps why they attacked and what made it possible for the attack to be successful. Details should be include the IP addresses involved, the services that were attacked, and the time of the attack to include Wireshark packet numbers. Finally, to the best of your ability and knowledge, describe exactly what you believed occurred. The more details that you can supply, the better you support your case, especially if it ends up in prosecution."













