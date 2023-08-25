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

- **Install Go 1.19 or 1.20**

  Installation instructions can be found here: https://golang.org/doc/install.
  Ensure Go was installed properly and is a supported version:
  ```sh
  $ go version
  $ go env GOROOT GOPATH
  ```
  NOTE: `GOROOT` and `GOPATH` must not be on the same path (if these are initialized).

- **Build or Update dcrctl**

  The latest release of dcrctl may be built in a single command without cloning
  this repository:

  ```sh
  $ go install decred.org/dcrctl@release-v1.8.0
  ```

  Using `@master` instead will perform a release build using the latest code
  from the master branch.  This may be useful to execute RPC methods not yet
  found in the latest Decred release:

  ```sh
  $ go install decred.org/dcrctl@master
  ```

  Alternatively, a development build can be performed by running `go install` in
  a locally checked-out repository.

  If you want to easily access dcrctl via `dcrctl` handle on command-line, since
  `go install` will put **dcrctl** binary in `go env GOPATH` you might need to
  ensure the `go env GOPATH` dir (or just **dcrctl** binary) is present in your
  `$PATH` (on Linux you might want to update your
  [~/.bashrc](https://stackoverflow.com/a/21012349) to achieve that).

## Developing

When developing either the `dcrd` or `dcrwallet` RPC servers and making
modifications to the RPC methods, you may want to build a development version of
`dcrctl` supporting these changes.  Due to `dcrctl` being built around
package-global method registrations and reflection, supporting these changes
only requires building with the updated packages.

This can be easily achieved by making use of a local Go workspace that uses the
development versions of `dcrd` and `dcrwallet` as follows:

```
$ go work init .
$ go work use ../dcrd/rpc/jsonrpc/types ../dcrwallet
```

## Contact

If you have any further questions you can find us at:

https://decred.org/community

## Issue Tracker

The [integrated github issue tracker](https://github.com/decred/dcrctl/issues)
is used for this project.

## License

dcrctl is licensed under the [copyfree](http://copyfree.org) ISC License.
