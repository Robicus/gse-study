# Firewalls

## Exam Outcome

Demonstrate competence with firewalls.

## Firewalls Overview

Reference:  401.2, pg. 110 (Module 15)
Reference:  401.5, Module 27

Built-in and free firewall that has full state dynamic filtering, with per-application and per-service filtering, and entails ingress/egress filtering.  However, no centralized logging and complex to manage.

Three network profiles:

1. Domain
2. Public
3. Private

## Windows Firewall

Good reading sources:
http://www.itsecure.hu/library/file/Biztons%C3%A1gi%20%C3%BAtmutat%C3%B3k/Egy%C3%A9b%20biztons%C3%A1gi%20%C3%BAtmutat%C3%B3k/Windows%20Firewall%20with%20Advanced%20Security%20Step-by-Step%20Guide%20-%20Deploying%20Firewall%20Policies.pdf

Understanding 'netsh firewall' versus 'netsh advfirewall':
https://support.microsoft.com/en-us/help/947709/how-to-use-the-netsh-advfirewall-firewall-context-instead-of-the-netsh

### Windows Firewall via the Command Line

Show current profile:

```
netsh advfirewall show currentprofile
```

Show all open ports allowed through built-in Windows firewall:

```
netsh firewall show portopening
```

Show all programs allowed to communicate through local firewall:

```
netsh firewall show allowedprogram
```

Show configuration options:

```
netsh firewall show config
```

Enabling a port:

```
netsh advfirewall firewall add rule name="Open Port 80" dir=in action=allow protocol=TCP localport=80
```

Disbaling a port:

```
netsh advfirewall firewall delete rule name=rule name protocol=udp localport=500
```

Deleting an existing rule:

```
netsh advfirewall firewall delete rule name="Rule Name"
```


Source:  http://blog.commandlinekungfu.com/2009/02/episode-2-looking-at-config-of-built-in.html

### Linux Firewall - iptables

Show firewall rules in all chains:

```
# iptables -t nat -nL
# iptables -t mangle -nL
# iptables -t filter -nL
# iptables -t raw -nL
```

Turning off Linux firewall:

```
iptables -F
```
