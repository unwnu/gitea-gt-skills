# Gitea gt skills

This marketplace packages one skill for agents that use the official Gitea `gt` CLI. The skill selects a command from the user's request, reads current help for its flags, and inspects the result. It covers repositories, issues, pull requests, releases, Actions, and related resources.

`gt` and Gitea 28 or newer are required. Install `gt` from the [official instructions](https://docs.gitea.com/cli/installation/). Sign in with `gt auth login`, or supply `GITEA_TOKEN` and `GITEA_INSTANCE_URL` for a temporary session. The marketplace does not include the binary or credentials.

## Claude Code

From the parent directory of this repository, run:

```sh
claude plugin marketplace add ./gitea-gt-skills
claude plugin install gitea-gt@gitea-gt-skills
```

## Codex

From the parent directory of this repository, run:

```sh
codex plugin marketplace add ./gitea-gt-skills
codex plugin add gitea-gt@gitea-gt-skills
```

Ask the agent to list issues, review a pull request, or inspect an Actions run. The skill name is `gt`. Claude Code exposes it as `/gitea-gt:gt`.

## Sources and scope

The [gt manual](https://docs.gitea.com/cli/) defines command behavior. The [official Gitea MCP tool list](https://pkg.go.dev/gitea.com/gitea/gitea-mcp#hdr-Available_Tools) informed the resource map. The [tea skills](https://github.com/deevus/tea-skills) and a short `glab` skill informed the single-skill layout. This project does not copy their instructions or run an MCP server.

`gt` 0.x can change flags and text output. The skill reads installed command help and uses JSON for structured output. This repository is independent of Gitea and its maintainers.
