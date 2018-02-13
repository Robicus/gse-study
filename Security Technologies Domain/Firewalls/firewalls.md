# Firewalls

## Exam Outcome

Demonstrate competence with firewalls.

### Windows Firewall via the Command Line

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

Source:  http://blog.commandlinekungfu.com/2009/02/episode-2-looking-at-config-of-built-in.html

### Linux Firewall - iptables

Show firewall rules in all chains:

```
# iptables -t nat -nL
# iptables -t mangle -nL
# iptables -t filter -nL
# iptables -t raw -nL
```

