# Analyze Traffic

## Exam Objective

Make correct judgments as to the nature of traffic to or from specific hosts in packet captures.

## Supplemental Resources:

Network Forensics w/ Wireshark video:
https://www.youtube.com/watch?v=UXAHvwouk6Q

## Interpret Traffic, Tools and Tricks

### How to Gain More Info About Expected Victim

#### Determine Top Destination IPs by Traffic

Use rwstats on flow data to determine the distribution of traffic. For example, the following will show the top 10 destination IPs by traffic:

```
rwstats capture.silk --fields 2 --count 10
```

#### Determine which Services are Open w/ tcpdump

The following uses a BPF filter to hone in on the 13th byte offset of all TCP traffic, i.e., TCP transmission control bits. The bitmask is looking for all SYN-ACK traffic. Then, awk is used to look at the 3rd field (source IP) and cut is used to pull out the port:

```
tcpdump -n -r capture.pcap 'host [IP address] and tcp[13] = 0x12' | awk '{print $3}' | cut -f 5 -d '.' | sort -n -u
```

#### Determine which TCP connections were initiated by the victim

```
tcpdump -n -r capture.pcap 'src host [victim IP] and tcp[13] = 0x2' | awk '{print $3 $4 $5 $6}' | more
```

### Identifying Attacks

#### Extracting Alerts from Traffic

```
snort -c /etc/snort.conf -K ascii -l log -r /path/to/capture.pcap
```

Using grep to hone in on alerts and sorting the unique entries found:

```
grep '\[\*\* alert' | sort | uniq -c | sort -rn
```

### Analyzing Possible Compromise

#### Getting a Feel w/ Chaosreader

```
chaosreader -eq capture.pcap -D /path/to/output
```


### Examples of Attack Traffic:

## Looking at ICMP tunneling:

![ICMP Tunneling](../screenshots/interpret-traffic-icmp-tunneling.PNG?raw=true "ICMP Tunneling")

"One of the telltale signs of an ICMP tunnel is a mismatch between echo requests and replies." (503 Lab Book, p. 68-B).  Drilling into the payload section of these packets reveal SSH tunneling.

## Looking at DNS poisoning:

![DNS Poisoning](../screenshots/interpret-traffic-dns-poisoning.PNG?raw=true "DNS Poisoning")

Multiple DNS responses to one request with incrementing DNS transaction IDs is a telltale sign of a spoofed DNS server's IP attempting to beat the real DNS server's response (DNS cache poisoning).  Best way to find real response is looking for a response from the true server's MAC address, or by filtering the capture on the DNS transaction ID that appears in the client's DNS request.


