# Analyze Traffic

## Exam Outcome

Demonstrate proficiency using common Open Source IDS tools including Snort, tcpdump, and Wireshark

## tcpdump Cheat Sheet

* http://packetlife.net/media/library/12/tcpdump.pdf

## Snort Usage and Common Flags

Example:
```
snort -r cmdexe.pcap -K none -A console -q -c snort.conf1
```

-r reads the specified file
-K logging mode
-A sets alert mode
-q quiet mode, doesn't show banner nor status report
-c specified the rules

## Snort Rule Writing Tips

The generic format for writing rules is:

- Rule Header (Rule Options)
-- Rule Header format: action protocol source-host/net source-port -> dest-host/net dest-port

Example:

```
alert udp $EXTERNAL_NET any -> $HOME_NET 67 (msg:"MISC bootp hardware address length overflow; content:"|01|"; depth:1; byte_test:1,>,6,2; sid:44554455;
```

## Snort Signature Example

![Snort Sig Example](../screenshots/snort-sig-example.PNG?raw=true "Snort Sig Example")

## Bro

### Running Bro in Readback Mode

```
bro -r /path/to/.pcap
```

As a result of running Bro against a pcap (.pcap) file, multiple bro files are created in the working directory:

* conn.log
* dns.log
* dpd.log
* files.log
* http.log
* irc.log
* packet_filter.log
* ssh.log
* ssl.log
* syslog.log
* weird.log
* x509.log

### Bro Command Line Fu

What connection had the largest number of bytes returned? How many bytes were returned?

```
cat conn.log | bro-cut id.org_h id.resp_h id.resp_p resp_bytes | sort -k 4 -rn | head -10
```

### Start Bro

```
broctl [as root]
```

```
install
```

```
start
```

```
status
```




