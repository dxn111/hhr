# HHR

HHR (Hyper-Horizon Reasoning) is a terminal coding assistant. It can inspect a codebase, work with local files, run shell commands with approval previews, and use a model through the Kilo Code gateway.

This repository contains installation and usage instructions. HHR's application files are distributed by the HHR installer.

## Requirements

- Linux or macOS
- Node.js 18 or newer, with npm
- `curl` (or Node.js `fetch`, included in Node.js 18+)
- A terminal with interactive input support

## Install

### With npm

```sh
npm install -g hhr-ai@latest
hhr
```

### With the installer

Review the installer before running it:

```sh
curl -fsSL https://hhr-ai.vercel.app/install.sh
```

When ready to install, run:

```sh
curl -fsSL https://hhr-ai.vercel.app/install.sh | sh
```

The installer places the launcher in `~/.local/bin/hhr` and the application in `~/.local/lib/hhr-ai`. It may add `~/.local/bin` to your `.zshrc` and `.bashrc`. Open a new terminal after installation if `hhr` is not found.

Check the installation and start HHR:

```sh
hhr --version
hhr
```

## First run

HHR uses Kilo Code as its model gateway. The default model is `kilo-auto/free`; free models may be rate-limited. To use a model that requires an API key, set a Kilo Code key in your shell before launching HHR:

```sh
export KILOCODE_API_KEY="your-key"
hhr
```

You can also use `HHR_KILOCODE_API_KEY` or `KILO_API_KEY`. Set `HHR_MODEL` to choose a model ID, for example:

```sh
export HHR_MODEL="provider/model-id"
hhr
```

Treat API keys as passwords. Do not commit them to a repository or paste them into shared logs.

## Updating

Run the installer again to install the latest hosted version:

```sh
curl -fsSL https://hhr-ai.vercel.app/install.sh | sh
```

The installer stages the new files and dependencies before activating the update.

## Troubleshooting

### `hhr: command not found`

Confirm `~/.local/bin` is on your `PATH`, then open a new terminal or run:

```sh
export PATH="$HOME/.local/bin:$PATH"
```

### Installer says Node.js or npm is missing

Install Node.js 18 or newer, including npm, then run the installer again. Check with:

```sh
node --version
npm --version
```

### Model requests fail

Check your network connection and model configuration. Free models can be rate-limited. Models that require a key need a valid Kilo Code API key in one of the environment variables listed above.

## Uninstall

Remove the installed launcher and application files:

```sh
rm -f "$HOME/.local/bin/hhr"
rm -rf "$HOME/.local/lib/hhr-ai"
```

HHR stores local settings and session data under `~/.hhr`. Remove that directory separately if you also want to delete those files.

## Links

- [HHR website](https://hhr-ai.vercel.app)
- [Installer](https://hhr-ai.vercel.app/install.sh)
