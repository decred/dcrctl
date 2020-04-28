dcrctl
======

Dcrctl is a command-line client for interacting with the JSON-RPC servers of
dcrd and dcrwallet.

## Usage

In its default configuration, dcrctl connects to dcrd's mainnet RPC port on
localhost.  The `--wallet` and `--testnet` flags change these defaults to the
dcrwallet RPC port and/or testnet ports.  The `--rpcserver/-s` flag can be used
to specify to specify other hostnames or IP addresses of the server, and can
also be used to override the port defaults.

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

## License

Dcrctl is licensed under a permissive ISC license.
