# goatscripts
Bash to basics.

# Run With Summary

`run-with-summary <args>`

## Example

```shell
SUCCESS="Deploy complete" \
ERROR="Deploy failed" \
DEBUG=1 \
SUMMARY=1 \
  run-with-summary ping w3.org -c3
```

## Output
```shell
Executing: ping w3.org -c5
PING w3.org (104.18.22.19): 56 data bytes
64 bytes from 104.18.22.19: icmp_seq=0 ttl=59 time=9.480 ms
64 bytes from 104.18.22.19: icmp_seq=1 ttl=59 time=13.510 ms
64 bytes from 104.18.22.19: icmp_seq=2 ttl=59 time=12.989 ms
64 bytes from 104.18.22.19: icmp_seq=3 ttl=59 time=15.017 ms
64 bytes from 104.18.22.19: icmp_seq=4 ttl=59 time=13.225 ms

--- w3.org ping statistics ---
5 packets transmitted, 5 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 9.480/12.844/15.017/1.825 ms
# Deploy complete
```
ping w3.org -c5
```

```
PING w3.org (104.18.22.19): 56 data bytes
64 bytes from 104.18.22.19: icmp_seq=0 ttl=59 time=9.480 ms
64 bytes from 104.18.22.19: icmp_seq=1 ttl=59 time=13.510 ms
64 bytes from 104.18.22.19: icmp_seq=2 ttl=59 time=12.989 ms
64 bytes from 104.18.22.19: icmp_seq=3 ttl=59 time=15.017 ms
64 bytes from 104.18.22.19: icmp_seq=4 ttl=59 time=13.225 ms

--- w3.org ping statistics ---
5 packets transmitted, 5 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 9.480/12.844/15.017/1.825 ms
```

| Command    | `ping w3.org -c5`
|------------|-----------------------
| Exit Code  | `0`
| Start Time | 2025-10-03 07:24:40 EDT
| End Time   | 2025-10-03 07:24:40 EDT
| Duration   | 4s
| User       | jonpugh 
| Host       | macbookpro.lan
| Directory  | /Users/jonpugh/Work/Operations/goatscripts

Markdown report saved to /tmp/summary.md
```
