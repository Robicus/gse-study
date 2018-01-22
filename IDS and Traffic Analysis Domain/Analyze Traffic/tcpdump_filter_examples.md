# tcpdump filters

## Examples

```
tcpdump -nt -r tcpdump.pcap 'src host 127.0.0.1 and tcp[13] = 0x10'
```

