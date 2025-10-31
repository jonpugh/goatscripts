# goatscripts
## git, operations, and things
Bash to basics.

These scripts are things I've been using in different places over the years.

Help yourself.

## Usage

### Install with GitHub Actions

```yml
jobs:
  example:
    steps:
      - uses: jonpugh/goatscripts@v1

        # OPTIONAL
        with:
          path: .custom-scripts

      - run: run-with-summary curl https://api.github.com/
```

## Run With Summary

`run-with-summary <args>`

Executes a command and prints a markdown summary. 

Useful for CI systems like GitHub Actions. 

## Examples

```shell
  run-with-summary ping w3.org -c5
```

To customize the report header text, show extra info in the table, or print the summary in the command run, use these env vars.

```shell
SUCCESS="Deploy complete" \
ERROR="Deploy failed" \
DEBUG=1 \
SUMMARY=1 \
  run-with-summary deploy.sh
```

To output the results of a command to GitHub Actions summary, add this step to your workflow:

```yaml
- name: Deploy script
  env: 
    SUCCESS: "Deploy complete"
    ERROR: "Deploy failed"
    SUMMARY: |
      - Environment: https://pr${{ github.event.number }}.demo.site
      - Pull Request: ${{github.event.pull_request.html_url }}

      <details><summary>${{ github.event.pull_request.title }}</summary>
        ${{ github.event.pull_request.body }}
      </details>
  run: |
    run-with-summary deploy.sh
```

<details>
<summary>Example Output</summary>

# Command complete

Any markdown at all can be put into the SUMMARY env var.

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

</details>
