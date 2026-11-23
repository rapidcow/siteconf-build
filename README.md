# siteconf-build

Run `make test` for all seven Perl packages in siteconf.

## Run locally

Run `./smoke` to test the committed HEAD of `../siteconf`, or pass the path
to another clone with `./smoke /path/to/siteconf`. The script extracts that
commit into a temporary directory and uses siteconf’s `env.pl` to load the
packages built there. It exits on the first failure.

You need Git, tar, make, Perl and gettext. The workflow lists the Ubuntu
packages and Perl dependencies. Once those are available, the test runs
offline. [Build dependencies](.github/workflows/smoke.yml)

## Run on GitHub

1. Create an empty GitHub repository for this harness. A public repository
   can run this workflow's standard Ubuntu runner for free. Private repositories
   draw on the account's included usage. [GitHub Actions billing](https://docs.github.com/en/billing/concepts/product-billing/github-actions)
2. From this directory, run the commands below, replacing OWNER and REPO
   with the repository you created.

   ```sh
   git add README.md AGENTS.md smoke .github/workflows/smoke.yml
   git commit -m "Add siteconf smoke build"
   git remote add origin https://github.com/OWNER/REPO.git
   git push -u origin HEAD
   ```

3. Open **Actions → siteconf smoke test** and select the first run to see
   the build log. If Actions is disabled for the repository, enable it and
   use **Run workflow** on the default branch.

Pushes and pull requests here test upstream `master`. A weekly run on Monday
at 06:23 UTC picks up changes made in the separate siteconf repository.
For an earlier result, use **Run workflow** and enter a branch, tag or commit
from rapidcow/siteconf that contains the seven package directories.
The job needs only read access and uses no deployment credentials.

## Reading a failure

The log shows the siteconf commit and prints each package name before running
its tests. To reproduce a failure, check out that commit in a local clone
and pass the clone’s path to `./smoke`.
