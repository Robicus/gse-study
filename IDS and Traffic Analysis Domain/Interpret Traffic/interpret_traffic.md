# Analyze Traffic

## Exam Objective

Make correct judgments as to the nature of traffic to or from specific hosts in packet captures.

### Supplemtal Resources:

Network Forensics w/ Wireshark video:
https://www.youtube.com/watch?v=UXAHvwouk6Q

### Looking at ICMP tunneling:

![ICMP Tunneling](../screenshots/interpret-traffic-icmp-tunneling.PNG?raw=true "ICMP Tunneling")

"One of the telltale signs of an ICMP tunnel is a mismatch between echo requests and replies." (503 Lab Book, p. 68-B).  Drilling into the payload section of these packets reveal SSH tunneling.

### Looking at DNS poisoning:

![DNS Poisoning](../screenshots/interpret-traffic-dns-poisoning.PNG?raw=true "DNS Poisoning")

Multiple DNS responses to one request with incrementing DNS transaction IDs is a telltale sign of a spoofed DNS server's IP attempting to beat the real DNS server's response (DNS cache poisoning).  Best way to find real response is looking for a response from the true server's MAC address, or by filtering the capture on the DNS transaction ID that appears in the client's DNS request.


