---
name: gt
description: Use Gitea's gt CLI for repositories, issues, pull requests, releases, and Actions on Gitea 28 or newer. Use for Gitea CLI tasks, not Graphite, Gitee, GitHub, or GitLab.
---

# Gitea CLI

Use `gt` to act on Gitea 28 or newer.

## Choose a command

1. If the CLI version is uncertain, run `gt version`.
2. For stored accounts, run `gt auth status`. `GITEA_TOKEN` can provide a temporary account.
3. Select the instance and repository from the request. If discovery is ambiguous, pass `--host` or `--repo`.
4. Before unfamiliar operations, read `gt <area> --help` and `gt <area> <action> --help`. The 0.x commands can change.
5. Prefer a named `gt` command. Use `gt api` only when no named command covers the action.
6. For structured results, use `--json`. When a prompt cannot be answered, use `--no-input`.
7. Inspect the exit code and result.

Choose an area from this map:

- Repositories, branches, and releases: `gt repo`, `gt branch`, `gt release`.
- Issues, labels, and milestones: `gt issue`, `gt label`, `gt milestone`.
- Pull requests and reviews: `gt pr`.
- Workflows and runs: `gt workflow`, `gt run`, `gt secret`, `gt variable`.
- Organizations and teams: `gt org`, `gt team`.
- Instance-wide discovery: `gt search`, `gt status`. `gt search` covers repositories, issues, and pull requests, not source code.

## Before a write

If the target repository is unclear, read `gt repo view --json full_name,url,private`. A fork can select its upstream repository. Before `gt pr create`, inspect the branch and diff because the command can push the branch. Before dispatching a run, read the workflow. Ask only if the target or effect remains ambiguous.

Do not print tokens or secret values. Do not disable TLS verification to bypass an error. For SSH-signature login, select SSH for Git. If the Git SSH host differs from the API host, set the instance `ssh_host`.

After a write, read the changed resource and report its URL or ID and observed state. A later failure can occur after creation, so do not claim that a failed command changed nothing.

Use the [gt manual](https://docs.gitea.com/cli/) for current behavior. The [Gitea MCP tool list](https://pkg.go.dev/gitea.com/gitea/gitea-mcp#hdr-Available_Tools) maps resource operations, but its tool names are not `gt` commands.
