---
name: gt
description: Use the Gitea gt CLI to inspect or change repositories, issues, pull requests, releases, and Actions on Gitea 28 or newer. Use for Gitea CLI work, not Graphite, Gitee, GitHub, or GitLab.
---

# Gitea CLI

Use `gt` to act on Gitea. It needs Gitea 28 or newer. Use this skill for both read and write requests.

## Choose the command

1. Run `gt version` when the CLI is uncertain. Use `gt auth status` for stored accounts; `GITEA_TOKEN` can supply a temporary account.
2. Select the instance and repository from the user's request. Use `--host` or `--repo` when discovery is ambiguous.
3. Run `gt <area> --help`, then `gt <area> <action> --help` before using unfamiliar flags. The 0.x command surface can change.
4. Prefer a named `gt` command. Use `gt api` only when that command lacks the needed operation.
5. Use `--json` for machine-readable results and `--no-input` when a prompt cannot be answered. Inspect the exit code and resulting state.

Use this map to choose an area:

- Repositories, branches, and releases: `gt repo`, `gt branch`, `gt release`.
- Issues, labels, and milestones: `gt issue`, `gt label`, `gt milestone`.
- Pull requests and reviews: `gt pr`.
- Workflows, runs, and their settings: `gt workflow`, `gt run`, `gt secret`, `gt variable`.
- People and teams: `gt org`, `gt team`.
- Cross-repository discovery: `gt search` or `gt status`. `gt search` covers repositories, issues, and pull requests, not source code.

## Before a write

Read the target with `gt repo view --json full_name,url,private` when the repository is unclear. A fork can select its upstream repository. Inspect the branch and diff before `gt pr create`, which can push the branch. Read the workflow before dispatching a run. Use the authorization in the current request, and ask only when the target or effect remains ambiguous.

Do not print tokens, secret values, or private message bodies. Do not disable TLS verification to bypass an error. When SSH-signature login is used for Git, select the SSH protocol. Set the instance `ssh_host` if its Git SSH host differs from its API host.

After a write, read back the changed resource and report its URL or ID and observed state. Report failures without claiming the write did not occur, since a later step can fail after creation.

Use the [gt manual](https://docs.gitea.com/cli/) for current behavior. The [Gitea MCP tool list](https://pkg.go.dev/gitea.com/gitea/gitea-mcp#hdr-Available_Tools) helps identify available resource operations, but its tool names are not `gt` commands.
