# Analyze Traffic

## Exam Objectives

Demonstrate the ability to decipher the contents of packet capture headers.

### Five Tips for Decoding Packets

1. Offsets from the beginning of the packet start with 0
2. Four bits = 1 hex character
3. One bytes = 2 hex characters
4. Fields can be any length (one bit, many bytes, fixed length or variable length)
5. Fields in one protocol identify the length and contents of others

Source: 401.1 pg. 152

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

Any of the traffic here could be suspicious, but the 'Data' classification under protocol hierarchy means Wireshark was unable to apply a dissector because it does not a) recognize the port number or b) no heuristic dissector matched the packets. You can right-click on the packets in question and 'apply as filter' for quick and easy analysis.

![Protocol Hierarchy](../screenshots/protocol_hiearchy_data_class.png?raw=true "Protocol Hierarchy - Data")

### Finding a packet

```
Edit > Find Packet ... (or Ctrl + F)
```

It's a good idea to select the radio button "Packet bytes" in order to search for the string or hex value within the payload.

![Find Packet](../screenshots/analyze-traffic-find-packet.PNG?raw=true "Find Packet")

### Following Streams

Right-click -> Follow TCP/UDP Stream is extremely useful for seeing the entire relationship and flow of packets pertaining to conversations of interest.

### Useful Display Filters and other Tips

Looking at the start of all TCP conversations:

```
(tcp.flags.syn == 1) and (tcp.flags.ack == 0)
```

Pro tip: Resulting conversations from the above filter can be color-coded with Wireshark's color feature.

### Carving Files Manually

1. Following the stream in Wireshark
2. Filter the conversation to represent the specific side of the conversation of interest
3. Save the file as raw output
4. Use a file editing tool, like vi on Linux, or WinHex on Windows to carve out any unnecessary bytes

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

### Analyzing User Agent Stings

It's important to correlate host operating systems (OS) versions based on the user-agent strings observed in web traffic.

An example user agent string:
Mozilla/5.0 (Windows NT 6.1; Trident/7.0; rv:11.0) like Gecko

Windows NT 6.1 correlates to Windows 7.

List of Windows NT versions to OS:

6.0	Windows Vista	
6.1 Windows 
6.2	Windows 8
6.3	Windows 8.1
10.0 Windows 10 / Server 2016






