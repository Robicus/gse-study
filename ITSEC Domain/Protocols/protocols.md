# Protocols

## Exam Outcome

Demonstrate a solid understanding of TCP/IP, UDP, ICMP, DNS, and other common protocols.

### TCP/IP

![IP Header](../screenshots/ip-header.PNG?raw=true "IP Header")

![TCP Header](../screenshots/tcp-header.PNG?raw=true "TCP Header")

Most commonly used transport protocol today.  Connection-oriented and provides assurances around packet delivery.

Source:  401.1 pg. 106

Common TCP ports:

- 20: FTP Data
- 21: FTP
- 23: Telnet
- 25: SMTP
- 53: DNS
- 80: HTTP
- 110: POP
- 443: HTTPS

### UDP

![UDP Header](../screenshots/udp-header.PNG?raw=true "UDP Header")

Connectionless communications. Sends packets out with no guarentee of delivery. Much less "overhead". Good protocol if a small amount of packet loss is acceptable.

Source: 401.1 pg. 117

### ICMP

![ICMP Header](../screenshots/icmp-header.PNG?raw=true "ICMP Header")

Used to report errors or troubleshooting and to provide network information.

Source:  401.1 pg. 124.

Common Types and Codes:

- 0: Echo reply
- 3: Destination unreachable
- 5: Redirect
- 8: Echo request
- 11: Time exceeded

### DNS

![DNS Header](../screenshots/dns-header.PNG?raw=true "DNS Header")






