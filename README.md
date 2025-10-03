# goatscripts
Bash to basics.

# Example

```shell
run-with-summary ping google.com -c2
```

# Command executed
```
ping google.com -c2
```

```
PING google.com (142.250.81.238): 56 data bytes
64 bytes from 142.250.81.238: icmp_seq=0 ttl=119 time=11.650 ms
64 bytes from 142.250.81.238: icmp_seq=1 ttl=119 time=9.998 ms

--- google.com ping statistics ---
2 packets transmitted, 2 packets received, 0.0% packet loss
round-trip min/avg/max/stddev = 9.998/10.824/11.650/0.826 ms
```

| Command | `ping google.com -c2`   |
|--------|--------|
| Exit Code | `0` |
| Start Time | 1759452910 |
| End Time | 1759452911 |
| Duration | 1s |
| User | jonpugh |
| Host | macbookpro.lan |
| Directory | /Users/jonpugh/Work/Operations/goatscripts |
