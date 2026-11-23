# siteconf-build

[![siteconf smoke test](https://github.com/rapidcow/siteconf-build/actions/workflows/smoke.yml/badge.svg?branch=master)](https://github.com/rapidcow/siteconf-build/actions/workflows/smoke.yml?query=branch%3Amaster)

Run `make test` for all seven Perl packages in siteconf.

## Run locally

Run `./smoke` to test the committed HEAD of `../siteconf`, or pass the path
to another clone with `./smoke /path/to/siteconf`. The script extracts that
commit into a temporary directory and uses siteconf’s `env.pl` to load the
packages built there. It exits on the first failure.

You need Git, tar, make, Perl and gettext. The workflow lists the system and
Perl dependencies for each platform. Once those are available, the test runs
offline. [Build dependencies](.github/workflows/smoke.yml)

## Run on GitHub

Each run tests the same seven packages on Ubuntu 24.04, macOS 15, Alpine
Linux 3.23, and rolling Arch Linux. Alpine and Arch each run inside their
own distribution’s container on an Ubuntu runner. Click the badge above
to see the result for each platform.

Pushes and pull requests here test upstream `master`. A weekly run on Monday
at 06:23 UTC picks up changes made in the separate siteconf repository.
For an earlier result, use **Run workflow** and enter a branch, tag or commit
from rapidcow/siteconf that contains the seven package directories.
The job needs only read access and uses no deployment credentials.

## Reading a failure

The log shows the siteconf commit and prints each package name before running
its tests. To reproduce a failure, check out that commit in a local clone
and pass the clone’s path to `./smoke`.
