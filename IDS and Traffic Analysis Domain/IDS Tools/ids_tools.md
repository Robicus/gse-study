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

## Snort Signature Example

![Snort Sig Example](../screenshots/snort-sig-example.PNG?raw=true "Snort Sig Example")


