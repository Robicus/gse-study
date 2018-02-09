# Analyze Traffic

## Exam Objective

Make correct judgments as to the nature of traffic to or from specific hosts in packet captures.

### Looking at ICMP tunneling:

![Protocol Hierarchy](../screenshots/interpret-traffic-icmp-tunneling.PNG?raw=true "Protocol Hierarchy")

"One of the telltale signs of an ICMP tunnel is a mismatch between echo requests and replies." (503 Lab Book, p. 68-B).  Drilling into the payload section of these packets reveal SSH tunneling.



