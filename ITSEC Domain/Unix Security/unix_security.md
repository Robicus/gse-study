# Unix Security

## Exam Outcome

Demonstrate knowledge of Unix Security and proficiency in a Unix environment.

## Identifying Listening Ports and Disabling Services

Show listening ports and PID and program name:

```
netstat -nap
```

Disabling services:
1. inetd: comment out lines in /ect/inetd.conf
2. xinetd: delete /etc/xinetd.d or make sure it contains "disable=yes"
3. rc.d:

```
chkconfig --listening
chkconfig [srv_name] off
```