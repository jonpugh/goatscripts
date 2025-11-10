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

