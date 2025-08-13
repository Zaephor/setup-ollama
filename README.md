# setup-ollama

## About

This GitHub Action sets up Ollama on a runner. It downloads and installs the Ollama binary, making it available for use in your workflows.

It supports installing the latest version, a specific version, or a version matching an ollama endpoint.

> [!WARNING]
> This action is meant to provide the `ollama` binary itself, it does not explicitly install or start any ollama services.

## Usage

To use this action in your workflow, add the following step to install the `ollama` binary:

```yaml
steps:
  - uses: zaephor/setup-ollama@main
```

By default, this will check if the `OLLAMA_HOST` environment variable is present(incase of self-hosted environments), and obtain the matching ollama version.


A specific version of the `ollama` binary can be installed:

```yaml
steps:
  - uses: zaephor/setup-ollama@main
    with:
      ollama_version: 0.11.4
```

Or a remote ollama endpoint can be specified, and this will use the remote's version to obtain the matching binary.

```yaml
steps:
  - uses: zaephor/setup-ollama@main
    with:
      ollama_endpoint: http://ollama-host:11434
```

And even further, if an endpoint is detected/provided and a list of models are provided, the action will pull them all
```yaml
steps:
  - uses: zaephor/setup-ollama@main
    with:
      ollama_endpoint: http://ollama-host:11434
      ollama_pull: |
        qwen3:14b
        qwen2.5-coder:14b
        hf.co/unsloth/Qwen3-Coder-30B-A3B-Instruct-GGUF:Q4_K_M
```
