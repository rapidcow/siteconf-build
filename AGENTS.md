# Working on siteconf-build

Keep the smoke test scoped to siteconf’s package test suites. Put test
commands in `smoke` so local runs and CI exercise the same code. Use
siteconf’s `env.pl` to resolve dependencies between packages.

Keep GitHub-specific setup in the workflow. Run `./smoke` against a local
siteconf checkout after changing the harness.
