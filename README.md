# goatscripts
## good old automation tools

Bash to basics.

These scripts are things I've been using in different places over the years.

Help yourself.

## Usage

### Install with GitHub Actions

```yml
jobs:
  example:
    steps:
      - uses: jonpugh/goatscripts@v1.2
```
## Scripts
- `run-with-summary`: Runs a command and generates a markdown summary with output and execution details.
- `wait-for`: Runs a command repeatedly until it passes.
- `git-ref`: Prints the branch or tag name of a git clone.

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
      - uses: jonpugh/goatscripts@v1.2

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

## `git-ref`

```
git-ref [OPTIONS]

Print the branch or tag of the current git repository.

Options:

  -t, --type    Print the git reference type ('branch' or 'tag').

    If PWD is tracking a branch, print 'branch'.
    If PWD is in a DETACHED HEAD state, and there is a tag for the SHA, print 'tag'.
    If the PWD is in a DETACHED HEAD state, and there is no tag, print 'sha'.
```

## `get-request`

```
get-request METRIC URL [OPTIONS]

Get specific information from a web request.

Possible METRICs:

  time
  The total time the request took in milliseconds.

  server-time
  The server response time (time to first byte) in milliseconds.

  size [FORMAT]
  The response body size. FORMAT can be: byte (default), KB, MB

  http-code
  The HTTP status code returned by the server.

  body
  The response body content.

  headers
  The response headers.

  @TODO: more options

Examples

  get-request time https://www.google.com
  get-request server-time https://www.google.com
  get-request size https://www.google.com
  get-request size https://www.google.com KB
  get-request http-code https://www.google.com
  get-request body https://www.google.com
  get-request headers https://www.google.com

```

## History

Originally developed during the course of building opendevshop.

Moved to `operations/scripts` https://github.com/operations-project/scripts 

Bringing it back to me. It's always been a personal project.
