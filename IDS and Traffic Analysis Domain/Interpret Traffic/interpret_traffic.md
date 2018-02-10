# Analyze Traffic

## Exam Objective

Make correct judgments as to the nature of traffic to or from specific hosts in packet captures.

### Looking at ICMP tunneling:

![Protocol Hierarchy](../screenshots/interpret-traffic-icmp-tunneling.PNG?raw=true "Protocol Hierarchy")

"One of the telltale signs of an ICMP tunnel is a mismatch between echo requests and replies." (503 Lab Book, p. 68-B).  Drilling into the payload section of these packets reveal SSH tunneling.

### Looking at DNS poisoning:

![Protocol Hierarchy](../screenshots/interpret-traffic-dns-poisoning.PNG?raw=true "Protocol Hierarchy")

Multiple DNS responses to one request with incrementing DNS transaction IDs is a telltale sign of a spoofed DNS server's IP attempting to beat the real DNS server's response (DNS cache poisoning).  Best way to find real response is looking for a response from the true server's MAC address, or by filtering the capture on the DNS transaction ID that appears in the client's DNS request.


