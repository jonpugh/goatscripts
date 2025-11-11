# goatscripts
## good old automation tools
## general operations administrator tricks
## git operations and things

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
```
## Scripts
- `run-with-summary`: Runs a command and generates a markdown summary with output and execution details.
- `wait-for`: Runs a command repeatedly until it passes.

## Run With Summary

```
run-with-summary my-long-command
```

Executes a command, prints logs, and saves a markdown summary. 

### Usage

```
jobs:
  example:
    name: "Test GitHub Actions"
    steps:
      - uses: jonpugh/goatscripts@v1

      - name: Install helper scripts
        uses: jonpugh/goatscripts@main

      # NOTE: You do NOT have to echo to $GITHUB_STEP_SUMMARY! The run-with-summary script does it automatically 👏
      - run: run-with-summary ls -la goatscripts
```

The script was designed to be most useful on GitHub, but you can use it anywhere.

### Results

GitHub step summaries are saved permanently. Here is [an example](https://github.com/jonpugh/goatscripts/actions/runs/18971608723/attempts/1#summary-54180476943): 

<img width="1151" height="744" alt="GitHub Step Summary Example" src="https://github.com/user-attachments/assets/818e630c-788f-4e13-8ead-0fde0fc19956" />


### Options

Customize the output with environment variables. See the [run-with-summary script](https://github.com/jonpugh/goatscripts/blob/main/src/run-with-summary) for more details.

```
jobs:
  deploy:
    steps:
      - uses: jonpugh/goatscripts@v1
      - run: run-with-summary deploy.sh
        env:
          SUCCESS: "Deploy complete! :rocket:"
          ERROR: "Deploy failed! :boom:"
          SUMMARY: |
            Set SUMMARY env var to add *any* markdown **you want** to the report file.
```

## wait-for

runs a command until it passes or timeout is reached.

### Use cases:

- Docker containers that have to wait for a database server to start
- Test scripts that have to wait for your project to initialize.
- Better than "sleep": Sometimes you need to wait. Instead of sleeping a fixed number of seconds, run a command that will pass once the thing you need is ready.

```
wait-for mysql-ready
wait-for curl https://deploy-url/ready
```

### Options

```
# SLEEP: Length of time to wait in-between running the command.
# CHAR: The character to print after every command run.
# OUTPUT: Set to 'all' to print all output, set to 'out' to print just stdOut, set to "err" to print just stdErr.
# TIMEOUT: Default: 30. Exit with an error if process doesn't pass within this time.
# SILENT: Set to 1 to not print any output except the timeout exceeded error. Useful when running from other scripts. See wait-mysql
```
