# tcpdump filters

## Examples

### Example 1: Showing only packets with the source IP of 127.0.0.1 with only the ACK bit set.

```
tcpdump -nt -r tcpdump.pcap 'src host 127.0.0.1 and tcp[13] = 0x10'
```

### Example 2:  Showing only packets with the destination IP of 127.0.0.1 with either the ACK or RST flags set.

```
tcpdump -nt -r tcpdump.pcap 'src host 127.0.0.1 and tcp[13] = 0x10'
tcpdump -nt -r tcpdump.pcap 'dst host 127.0.0.1 and tcp[13] & 0x14 != 0
```

