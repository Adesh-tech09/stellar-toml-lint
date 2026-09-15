# Stellar TOML Lint - Drips Wave Documentation

[![CI](https://github.com/anchor-tools/stellar-toml-lint/actions/workflows/ci.yml/badge.svg)](https://github.com/anchor-tools/stellar-toml-lint/actions/workflows/ci.yml)
[![npm](https://img.shields.io/npm/v/stellar-toml-lint.svg)](https://www.npmjs.com/package/stellar-toml-lint)
[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](./LICENSE)

## Overview

`stellar-toml-lint` is a command-line tool that validates a Stellar Info File (`stellar.toml`) against [SEP-1] offline, before deployment. It catches errors that would otherwise only be found after deploying the file, by checking the file's contents directly.

This document focuses on the project's participation in [Drips Wave][wave], a program that funds open-source software through community support.

## Drips Wave

Drips Wave operates in cycles, with issues categorized by complexity tiers:

- **Trivial** (100 points): Typos, small bug fixes, minor copy changes
- **Medium** (150 points): Standard features or involved bug fixes
- **High** (200 points): Complex features, refactors, new integrations

Contributors can claim wave issues, implement them, and receive funding upon acceptance.

### Current Wave Issues

See [WAVE-ISSUES.md](WAVE-ISSUES.md) for the full backlog of wave issues for this project.

### How to Contribute

1. Pick an issue from the wave backlog that interests you.
2. Implement the changes following the project's contributing guidelines ([CONTRIBUTING.md](../CONTRIBUTING.md)).
3. Submit a pull request referencing the wave issue.
4. Upon approval, the wave issue will be marked as complete and you will receive the associated points.

## Features

This tool offers:

- **Local validation**: Lints a local `stellar.toml` file without requiring a deployed domain.
- **Domain validation**: With `--domain`, checks reachability, CORS headers, and content-type.
- **Multiple output formats**: Text, JSON, SARIF, and GitHub annotations.
- **Configurable rules**: Adjust rule severities with `--off`, `--warn`, `--error`.
- **Pre-commit and CI integration**: Easily integrate into your workflow.

## Recent Enhancements for Drips Wave

The following features have been implemented as part of Drips Wave contributions:

- Added `--no-suggestions` flag to hide diagnostic suggestions in the text reporter (cli.ts, README.md)
- Added warning rule for ORG_LICENSE_NUMBER without ORG_LICENSING_AUTHORITY (documentation.ts)

## Installation

```bash
npm install --save-dev stellar-toml-lint   # project dependency
npx stellar-toml-lint                      # or just run it
```

Requires Node.js 20 or newer.

## Usage

```bash
# Lint a local file (defaults to ./stellar.toml)
stellar-toml-lint public/.well-known/stellar.toml

# Fetch and lint a live site, including CORS and content-type checks
stellar-toml-lint --domain example.com

# Lint a local file *as if* served from a domain, enabling same-domain checks
stellar-toml-lint public/.well-known/stellar.toml --domain example.com

# Read from stdin
cat stellar.toml | stellar-toml-lint -
```

See the [README.md](../README.md) for full usage instructions and options.

## License

[Apache-2.0](./LICENSE)

Not affiliated with or endorsed by the Stellar Development Foundation.

[SEP-1]: https://github.com/stellar/stellar-protocol/blob/master/ecosystem/sep-0001.md
[wave]: https://www.drips.network/wave
