# goatscripts
Bash to basics.

# Example

```shell
run-with-summary ping google.com -c2
```
DEBUG=1 SUMMARY=1  ./src/run-with-summary ping google.com -c2
PING google.com (142.250.81.238): 56 data bytes
64 bytes from 142.250.81.238: icmp_seq=0 ttl=119 time=10.933 ms
64 bytes from 142.250.81.238: icmp_seq=1 ttl=119 time=9.472 ms

--- google.com ping statistics ---
2 packets transmitted, 2 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 9.472/10.203/10.933/0.730 ms
# Command executed
```
ping google.com -c2
```

```
PING google.com (142.250.81.238): 56 data bytes
64 bytes from 142.250.81.238: icmp_seq=0 ttl=119 time=10.933 ms
64 bytes from 142.250.81.238: icmp_seq=1 ttl=119 time=9.472 ms

--- google.com ping statistics ---
2 packets transmitted, 2 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 9.472/10.203/10.933/0.730 ms
```

| Command    | `ping google.com -c2`
|------------|-----------------------
| Exit Code  | `0`
| Start Time | 2025-10-02 21:10:48 EDT
| End Time   | 2025-10-02 21:10:49 EDT
| Duration   | 1s
| User       | jonpugh 
| Host       | macbookpro.lan
| Directory  | /Users/jonpugh/Work/Operations/goatscripts

Markdown report saved to /tmp/summary.md