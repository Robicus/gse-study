# Analyze Traffic

## Exam Objectives

Demonstrate the ability to decipher the contents of packet capture headers.

## Analyze Traffic w/ Wireshark

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

![Protocol Hierarchy](screenshots/analyze-traffic-wireshark-statistics.PNG?raw=true "Protocol Hierarchy")

### Finding a packet

```
Edit > Find Packet ... (or Ctrl + F)
```

It's a good idea to select the radio button "Packet bytes" in order to search for the string or hex value within the payload.

![Find Packet](screenshots/analyze-traffic-find-packet.PNG?raw=true "Find Packet")

Change...