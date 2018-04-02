# Analyze Traffic

## Exam Objectives

Demonstrate the ability to decipher the contents of packet capture headers.

## Common Protocol Diagrams

### IP Headers

![IP Header](../screenshots/ip-header.PNG?raw=true "IP Header")

## Analyze Traffic w/ Wireshark

### Great tips for organizing views/columns/data in Wireshark

http://www.malware-traffic-analysis.net/tutorials/wireshark/index.html

Introduction to Wireshark: Sample Traffic Analysis - Book 1, Page 49

### Loading Wireshark

```
wireshark
wireshark [pcap file]
```

### Profiling a pcap

Wireshark's "Statistics" menu items serve as a great starting point when jumping into a pcap...

```
Statistics > Protocol Hierarchy
```

![Protocol Hierarchy](../screenshots/analyze-traffic-wireshark-statistics.PNG?raw=true "Protocol Hierarchy")

### Finding a packet

```
Edit > Find Packet ... (or Ctrl + F)
```

It's a good idea to select the radio button "Packet bytes" in order to search for the string or hex value within the payload.

![Find Packet](../screenshots/analyze-traffic-find-packet.PNG?raw=true "Find Packet")

### Following Streams

Right-click -> Follow TCP/UDP Stream is extremely useful for seeing the entire relationship and flow of packets pertaining to conversations of interest.

### Analyzing w/ Tshark

Tshark (terminal wireshark) is a great tool for command-line analysis of packets.

Reading packet captures without name resolutions:

```
tshark -n -r [capture.pcap]
```

Using a display filter (-Y) to narrow down results to a specific IP and protocol:

```
tshark -n -r [capture.pcap] -Y 'ip.addr == 192.168.60.22 and smtp'
```

Specifying certain fields to display (-T fields -e [field]):

```
tshark -n -r [capture.pcap] -Y 'ip.addr == 192.168.60.22 and smtp' -T fields -e tcp.steeam
```

Following streams with tshark:

```
tshark -n -r [capture.pcap] -Y 'tcp.stream == [stream id]' -z follow,tcp,ascii,60
```

### Working with SiLK

Counting the number of records:

```
rwfilter suspicious.silk --proto=0-255 --print-stat
```

Looking for top (5) senders of data (bytes):

```
rwstats --fields sIP --bytes --count=5
```

## Scapy

### Creating a frame with ICMP

![Scapy - Create Frame](../screenshots/scapy-create-frame.PNG?raw=true "Scapy - Create Frame")

Saving a created packet to disk:

```
wrpcap("/tmp/icmp.pcap". frame)
```

Send crafted packet:

```
send(packet_object)
```





