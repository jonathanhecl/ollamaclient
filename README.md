# ollamaclient

This is a Go package for using Ollama.

The default model is `nous-hermes:latest`.

Example programs are in the `cmd` folder.

### Getting started

1. Install `ollama` and start it as a service.
2. Run `ollama pull nous-hermes` to fetch the `nous-hermes` model.
3. Install the summarizer utility: `go install github.com/xyproto/ollamaclient/cmd/summarize@latest`
4. Summarize a README.md file and a source code file: `summarize README.md ollamaclient.go`
5. Write a poem about one or more files: `summarize --prompt "Write a poem about the following files:" README.md`

### Usage of the `summarize` utility

```bash
./summarize [flags] <filename1> [<filename2> ...]
```

#### Flags

- `-m`, `--model`: Specify an Ollama model. The default is `nous-hermes:latest`.

- `-o`, `--output`: Defines an output file to store the summary.

- `-p`, `--prompt`: Specifies a custom prompt header for summary.
  Default: "Write a short summary of what a project that contains the following files is."

- `-V`, `--verbose`: Enables verbose logging.

- `-w`, `--wrap`: Sets the word wrap width. Use -1 to detect the terminal width.

#### Example use

Generate a summary with a custom prompt:

```bash
./summarize -w -1 -p "Summarize these files:" README.md CONFIG.md
```

Generate a summary, saving the output to a file:

```bash
./summarize -o output.txt README.md CONFIG.md
```

Generate a summary with custom word wrap width:

```bash
./summarize -w 100 README.md
```

### Environment variables

These environment variables are supported:

* `OLLAMA_HOST` (`http://localhost:11434` by default)
* `OLLAMA_MODEL` (`nous-hermes:latest` by default)
* `OLLAMA_VERBOSE` (`false` by default)

### General info

* Version: 1.4.0
* License: Apache2
* Author: Alexander F. Rødseth
