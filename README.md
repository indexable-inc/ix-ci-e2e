# ix CI end-to-end test

> **Generated repository. Do not edit here.** This repository is a projection of `satellites/ix-ci-e2e` in the private ix monorepo; a bot overwrites it on every ix main push, so direct changes are lost. To propose a change, open an issue; pull requests here are closed automatically.

This public repository is the customer-facing smoke test for ix-hosted GitHub Actions runners. Its workflow has two jobs on `runs-on: ix` and prints the VM kernel, CPU count, disk space, and an `ok` marker. Keep it available for future ix CI checks.

Customer setup for the current webhook control plane is: install the ix-runners GitHub App on this repository, link the installation to the ix account at ix.dev, add `runs-on: ix` to a workflow, and push. No `IX_TOKEN` or `RUNNER_PAT` repository secrets are required. A green default-branch run becomes the warm seed for later jobs.

Ownership: the ix-hosted webhook control plane owns this repository's runner pool. The workflow has no reconcile job and the ix-runners action must not be added to it: two control planes on one pool double-spawn.

Which ix the runners come from is decided by the control plane (the pool's regions and the endpoint it creates machines through), not by this workflow. A manual run takes `arch` (`x86_64` or `arm64`, the runner label; the repository variable `IX_RUNNER_ARCH` is its default, and a Graviton-only region needs `arm64`) and `expect_region`; the repository variable `IX_REGION` is the default expectation, printed in the job log.
