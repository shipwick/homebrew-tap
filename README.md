# Shipwick Homebrew tap

The [Shipwick](https://shipwick.com) command-line client for macOS and Linux.

```bash
brew install shipwick/tap/shipwick
```

Upgrade with `brew upgrade shipwick`. Shell completions for bash, zsh and fish
are installed along with it.

This installs the CLI only. The server side — the agent, Caddy and the
dashboard — is set up on the server itself:
[Install Shipwick on a server](https://shipwick.com/docs/getting-started/install).

## How the tap is maintained

`Formula/shipwick.rb` is generated, never edited:

```bash
sh scripts/update-formula.sh            # the latest release
sh scripts/update-formula.sh v0.2.0     # a specific one
```

The formula installs the binaries published with each
[release](https://github.com/shipwick/shipwick/releases), and its checksums are
taken from the release's `checksums.txt` — the same file the installer verifies
against. Pre-releases are refused.

The *Update* workflow runs the script once a day, commits the result when a
new release exists and starts *Test* for it; run it by hand to publish a release
to Homebrew at once.
The *Test* workflow installs the formula on macOS and on Linux, and runs
`brew test` and `brew audit --strict`.

GitHub pauses scheduled workflows in a repository without activity for 60
days. If *Update* has stopped, re-enable it on the Actions tab.

Problems with the CLI itself belong in
[shipwick/shipwick](https://github.com/shipwick/shipwick/issues).

## License

[Apache License 2.0](LICENSE).
