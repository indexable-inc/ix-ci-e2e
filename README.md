# ix CI end-to-end test

> **Generated repository. Do not edit here.** This repository is a projection of `satellites/ix-ci-e2e` in the private ix monorepo; a bot overwrites it on every ix main push, so direct changes are lost. To propose a change, open an issue; pull requests here are closed automatically.

The customer-facing smoke test for ix-hosted GitHub Actions runners. Its workflow runs two jobs on `runs-on: ix` that print the VM kernel, CPU count, disk space and an `ok` marker.

Customer setup is four steps. Install the ix-runners GitHub App on the repository, link the installation to the ix account at ix.dev, add `runs-on: ix` to a workflow, and push. No `IX_TOKEN` or `RUNNER_PAT` secret is needed. A green default-branch run becomes the warm seed for later jobs.

The ix-hosted webhook control plane owns this repository's runner pool. Never add a reconcile job or the ix-runners action here, because two control planes on one pool double-spawn.

The control plane picks the pool's regions and the endpoint it creates VMs through. A manual run takes `arch` (`x86_64` or `arm64`, default from the repository variable `IX_RUNNER_ARCH`; a Graviton-only region needs `arm64`) and `expect_region` (default from `IX_REGION`, printed in the job log).
