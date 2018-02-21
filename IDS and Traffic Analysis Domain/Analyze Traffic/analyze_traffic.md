# Analyze Traffic

## Exam Objectives

Demonstrate the ability to decipher the contents of packet capture headers.

## Common Protocol Diagrams

### IP Headers

![IP Header](../screenshots/ip-header.PNG?raw=true "IP Header")

## Analyze Traffic w/ Wireshark

### Great tips for organizing views/columns/data in Wireshark

http://www.malware-traffic-analysis.net/tutorials/wireshark/index.html

* Introduction to Wireshark: Sample Traffic Analysis - Book 1, Page 49

### Loading Wireshark

```
wireshark
wireshark [pcap file]
```

### Profiling a pcap

Wireshark's "Statistics" menu items serve as a great starting point when jumping into a pcap.  

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

![Scapy - Create Frame(../screenshots/scapy-create-frame.PNG?raw=true "Scapy - Create Frame")


