dcrctl
======

[![Build Status](https://github.com/decred/dcrctl/workflows/Build%20and%20Test/badge.svg)](https://github.com/decred/dcrctl/actions)
[![ISC License](https://img.shields.io/badge/license-ISC-blue.svg)](http://copyfree.org)
[![Go Report Card](https://goreportcard.com/badge/github.com/decred/dcrctl)](https://goreportcard.com/report/github.com/decred/dcrctl)

Dcrctl is a command-line client for interacting with the JSON-RPC servers of
[dcrd](https://github.com/decred/dcrd) and
[dcrwallet](https://github.com/decred/dcrwallet).

## Usage

In its default configuration, dcrctl connects to dcrd's mainnet RPC port on
localhost.  The `--wallet` and `--testnet` flags change these defaults to the
dcrwallet RPC port and/or testnet ports.  The `--rpcserver/-s` flag can be used
to specify other hostnames or IP addresses of the server, and can also be used
to override the port defaults.

Dcrctl will attempt to read dcrd and dcrwallet config files for the
user/password authentication.  If these fields cannot be read, dcrctl must be
manually configured with the correct authentication.  Permanent configuration
changes may be written to a config file in a platform-specific location:

* macOS: `~/Library/Application Support/Dcrctl/dcrctl.conf`
* Windows: `%LOCALAPPDATA%\Dcrctl\dcrctl.conf`
* Linux and other Unix: `~/.dcrctl/dcrctl.conf`

## Build and installation

The latest dcrctl may be built in a single command without cloning this
repository:

```
$ GO111MODULE=on go get decred.org/dcrctl
```

Appending `@master` to this will perform a release build using the latest code
from the master branch.  This may be useful to execute RPC methods not yet found
in the latest Decred release.

Alternatively, a development build can be performed by running `go install` in a
locally checked-out repository.

## Contact

If you have any further questions you can find us at:

https://decred.org/community

## Issue Tracker

The [integrated github issue tracker](https://github.com/decred/dcrctl/issues)
is used for this project.

## License

dcrctl is licensed under the [copyfree](http://copyfree.org) ISC License.
