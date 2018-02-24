# Incident Handling Process

## Exam Outcome

Demonstrate mastery of the Incident Handling process.

### 6 Phases of Incident Reponse (IR)

1. Preparation
2. Identification
3. Contaimnment
4. Eradication
5. Recovery
6. Lessons Learned

### Identification - Technical - Windows


```
taskmgr.exe
```

```
tasklist -v
```

```
wmic process list full
```

Unusual Registry Keys:

```
req query [key]
```

```
reg query hklm\software\microsoft\windows\currentversion\run
```

Looking at Scheduled Tasks:

```
schtasks | more
```

Looking at Unusual Accounts:

```
net localgroup administrators
```

### Containment

The goal of containment is to keep the problem from getting worse.  

Containment sub-phases:

1. Short-term containment
2. System back-up
3. Long-term containment









