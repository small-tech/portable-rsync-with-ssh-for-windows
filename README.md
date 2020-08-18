# Portable Rsync With SSH For Windows

Based on [github: fdcastel/cygrsync](https://github.com/fdcastel/cygrsync), a portable distribution of rsync with SSH for Windows. Uses the binaries from [cygwin](https://www.cygwin.com/). Runs __without__ cygwin installed.

## Reproducing

This was created by following the instructions on [github: fdcastel/cygrsync](https://github.com/fdcastel/cygrsync) to create an up-to-date distribution of rsync and SSH from [cygwin](https://www.cygwin.com/).

The same set of libraries (some of which were newer versions) were copied from the resulting files.

## Usage

When run from the _bin/_ directory, the `rsync` and `ssh` commands believe they are running from `/bin` (so `..` is root).

As such, they will fail unless they find:

  - `/home/{YOUR_ACCOUNT}`
  - `/home/{YOUR_ACCOUNT}/.ssh/id_ed25519` (or id_rsa, etc., if using SSH keys)


## Current versions

The current build has the following versions of the commands:

### Rsync

Version 3.2.0 dev (protocol version 31)

### SSH

  - OpenSSH Version 8.3p1
  - OpenSSL Version 1.1.1f (31 March, 2020)

(In our testing, this is compatible with what is currently installed on our Linux servers: rsync 3.1.3 protocol version 31 and OpenSSH 8.2p1, OpenSSL 1.1.1f 31 March, 2020.)
