# IDS Tools

## Exam Outcome

Demonstrate proficiency using common Open Source IDS tools including Snort, tcpdump, and Wireshark

## tcpdump Cheat Sheet

http://packetlife.net/media/library/12/tcpdump.pdf

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

## tcpdump

Reading a capture:

```
tcpdump -r [capture.pcap]
```

Specifying the interface to listen on:

```
tcpdump -i lo
```

Specifying the nmer of packets to capture:

```
tcpdump -i lo -c 5
```

Reading a capture without converting addresses (-n), without printing timestamps, with even more verbose output.

```
tcpdump -n -t -vv -r [capture.pcap]
```

Displaying hex (lowercase "x"):

```
tcpdump -x
```

Displaying hex and ASCII (capitalized "X"):

```
tcpdump -X
```

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

### Running Bro with a signature file

```
bro -r /path/to/.pcap -s /path/to/.sig
```
The Bro signature file allows bro to match, and pattern match, network traffic like:
   - Src and Dst IP Addresses (i.e. 192.168.1.1)
   - Src and Dst Protocol Numbers (i.e. 8080)
   - Protocol Names (i.e. tcp)
   - Event Values (i.e. "Outbound HTTP Traffic")
   - RegEx values (i.e. /^User-Agent:.*/)

The Signature file uses a rather simple format of 'name {<values>}', here is an example using the previous i.e.'s:
```
signature bro.sig {
  src-ip == 192.168.0.0/16
  dst-ip == 192.168.0.0/16
  dst-port == 8080
  ip-proto == tcp
  event "Outbound HTTP Traffic"
  http-request-header /^User-Agent:.*/
}
```

Interestingly, the signature format can also support Hex Queries within passing files, using the following format:
```
Interest Hex in File {
   file-magic /x54x52x55x45x56x49x53x49/
}
```

### Running Bro with a Notification configuration
Bro can write the signatures it detects to the notice.log by using the 'NOTICE' configuration:
```
Bro_Notice_Event {
  local snet == 192.168.0.0/16
  
  if (c$id$orig_h is snet)
  {
    if (c$id$resp_h !in snet)
    {
      if (c$ip$resp_p == 8080 && name == "USER-AGENT")
      {
        NOTICE([$note=Wierd::Activity, $msg=fmt ("Source IP %s, Dest IP/Port %s %s, USER-AGENT content %s",
        c$id$orig_h,c$id$resp_h,c$id$resp_p,value)
        ]);
      }
    }
  }
}
```

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




