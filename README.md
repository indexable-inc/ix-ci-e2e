# ix CI end-to-end test

> **Generated repository. Do not edit here.** This repository is a projection of `satellites/ix-ci-e2e` in the private ix monorepo; a bot overwrites it on every ix main push, so direct changes are lost. To propose a change, open an issue; pull requests here are closed automatically.

This public repository is the customer-facing smoke test for ix-hosted GitHub Actions runners. Its workflow has two jobs on `runs-on: ix` and prints the VM kernel, CPU count, disk space, and an `ok` marker. Keep it available for future ix CI checks.

Customer setup for the current webhook control plane is: install the ix-runners GitHub App on this repository, link the installation to the ix account at ix.dev, add `runs-on: ix` to a workflow, and push. No `IX_TOKEN` or `RUNNER_PAT` repository secrets are required. A green default-branch run becomes the warm seed for later jobs.
