# Portable Rsync With SSH For Windows

Based on [github: fdcastel/cygrsync](https://github.com/fdcastel/cygrsync), a portable distribution of rsync with SSH for Windows. Uses the binaries from [cygwin](https://www.cygwin.com/). Runs __without__ cygwin installed.

## Reproducing

This was created by following the instructions on [github: fdcastel/cygrsync](https://github.com/fdcastel/cygrsync) to create an up-to-date distribution of rsync and SSH from [cygwin](https://www.cygwin.com/).

The same set of libraries (some of which were newer versions) were copied from the resulting files.

## Usage

When run from the `bin/` directory, the `rsync` and `ssh` commands believe that they are running from `/bin/` and that the root is their parent folder.

To access Windows paths, you must specify them in cygwin format with without the `/cygdrive` path prefix (as configured in `etc/fstab`). E.g., `/c/my-folder` points to `C:\my-folder`. 

The exception is the home folder since `etc/nsswitch.conf` tells them to use your Windows home as the home directory.

By default, the command will try to use the keys defined in your `"${env:home}\.ssh"` (using your Windows home). __The keys in here must be in Linux format (with `LF` line endings), not Windows format (with `CRLF` line endings).__

The `ssh` binary that comes with this distribution cannot read keys with Windows line endings and will throw an `invalid format` error while trying to load the key. The OpenSSH version that comes preinstalled on Windows 10, on the other hand, can read keys with Linux line endings properly. So as long as your keys are written out with Linux line endings (e.g., generated from Windows Subsystem for Linux, etc.), then they will work under both Windows and this emulated cygwin rsync.

## Current versions

The current build has the following versions of the commands:

### Rsync

Version 3.2.0 dev (protocol version 31)

### SSH

  - OpenSSH Version 8.3p1
  - OpenSSL Version 1.1.1f (31 March, 2020)

(In our testing, this is compatible with what is currently installed on our Linux servers: rsync 3.1.3 protocol version 31 and OpenSSH 8.2p1, OpenSSL 1.1.1f 31 March, 2020.)
