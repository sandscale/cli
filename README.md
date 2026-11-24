# Sandscale CLI

`sandscale` runs your Sandscale sandboxes, cloud workspaces, build hosts, storage and account from the terminal, signed in
with your own Sandscale account. Every command takes `--json` and `--region`.

This repository holds the releases: the binaries, their `SHA256SUMS`, the installer and the Homebrew formula. Download them
from [Releases](https://github.com/sandscale/cli/releases).

## Install

macOS and Linux:

```sh
curl -fsSL https://sandscale.dev/install | sh                 # installs to ~/.sandscale/bin
curl -fsSL https://sandscale.dev/install | sh -s -- --system  # installs to /usr/local/bin
```

The installer picks the binary for your OS and architecture, checks it against the release's `SHA256SUMS` and refuses to
install on a mismatch. It never runs sudo and never edits your shell profile: when the folder is not writable it prints the
one command to run.

Homebrew (macOS and Linux):

```sh
brew install sandscale/tap/sandscale
```

By hand: download `sandscale-<os>-<arch>` and `SHA256SUMS` from the release, then:

```sh
sha256sum -c --ignore-missing SHA256SUMS      # macOS: shasum -a 256 -c --ignore-missing SHA256SUMS
install -m 755 sandscale-linux-x64 ~/.local/bin/sandscale
```

Binaries: `linux-x64`, `linux-arm64`, `linux-x64-musl`, `darwin-arm64`, `darwin-x64`. Windows and npm are coming soon.

## Use

```sh
sandscale login
sandscale sandbox create --template-id builtin:node --yes
sandscale sandbox exec --id sbx_123 --yes -- make test
sandscale workspace list --json --region us1
sandscale workspace ssh my-workspace
sandscale mcp                    # an MCP server for coding tools
sandscale help
```

Documentation: https://sandscale.dev/docs

## Support and security

Questions: support@sandscale.dev. Report a vulnerability to security@sandscale.dev (see
https://sandscale.dev/security/disclosure).

## License

The Sandscale CLI is licensed under the Business Source License 1.1 (see [LICENSE](LICENSE)).
