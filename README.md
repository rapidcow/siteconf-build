# siteconf-build

[![Ubuntu](https://github.com/rapidcow/siteconf-build/actions/workflows/ubuntu.yml/badge.svg?branch=master)](https://github.com/rapidcow/siteconf-build/actions/workflows/ubuntu.yml?query=branch%3Amaster)
[![macOS (Intel)](https://github.com/rapidcow/siteconf-build/actions/workflows/macos.yml/badge.svg?branch=master)](https://github.com/rapidcow/siteconf-build/actions/workflows/macos.yml?query=branch%3Amaster)
[![Alpine](https://github.com/rapidcow/siteconf-build/actions/workflows/alpine.yml/badge.svg?branch=master)](https://github.com/rapidcow/siteconf-build/actions/workflows/alpine.yml?query=branch%3Amaster)
[![Arch Linux](https://github.com/rapidcow/siteconf-build/actions/workflows/arch.yml/badge.svg?branch=master)](https://github.com/rapidcow/siteconf-build/actions/workflows/arch.yml?query=branch%3Amaster)
[![FreeBSD](https://github.com/rapidcow/siteconf-build/actions/workflows/freebsd.yml/badge.svg?branch=master)](https://github.com/rapidcow/siteconf-build/actions/workflows/freebsd.yml?query=branch%3Amaster)
[![NetBSD](https://github.com/rapidcow/siteconf-build/actions/workflows/netbsd.yml/badge.svg?branch=master)](https://github.com/rapidcow/siteconf-build/actions/workflows/netbsd.yml?query=branch%3Amaster)
[![Solaris](https://github.com/rapidcow/siteconf-build/actions/workflows/solaris.yml/badge.svg?branch=master)](https://github.com/rapidcow/siteconf-build/actions/workflows/solaris.yml?query=branch%3Amaster)

Run `make test` for all seven Perl packages in siteconf.

## Run locally

Run `./smoke` to test the committed HEAD of `../siteconf`, or pass the path
to another clone with `./smoke /path/to/siteconf`. The script extracts that
commit into a temporary directory and uses siteconf’s `env.pl` to load the
packages built there. It exits on the first failure.

You need Git, tar, make, Perl and gettext. Install Ninja to exercise the Ninja backend.
The workflows list the system and
Perl dependencies for each platform. Once those are available, the test runs
offline. [Build dependencies](.github/workflows/)

## Run on GitHub

Separate workflows test the same seven packages on Ubuntu 24.04, macOS 15 (Intel), Alpine
Linux 3.23, rolling Arch Linux, FreeBSD, NetBSD, and Solaris. Alpine and Arch each run inside their
own distribution’s container on an Ubuntu runner. The BSD and Solaris jobs boot guest VMs and cache their installed dependencies.
Click a platform’s badge to see its runs.

Pushes and pull requests here test upstream `master`. A weekly run on Monday
at 06:23 UTC picks up changes made in the separate siteconf repository.
For an earlier result, use **Run workflow** and enter a branch, tag or commit
from rapidcow/siteconf that contains the seven package directories.
The job needs only read access and uses no deployment credentials.

## Reading a failure

The log shows the siteconf commit and prints each package name before running
its tests. To reproduce a failure, check out that commit in a local clone
and pass the clone’s path to `./smoke`.
