# Gitea gt skill

This marketplace provides one skill for Claude Code and Codex. It helps agents use the official Gitea `gt` CLI. The skill reads installed command help before it uses unfamiliar flags and reads each changed resource after a write.

You need `gt` and Gitea 28 or newer. Follow the [official installation guide](https://docs.gitea.com/cli/installation/), then run `gt auth login`. For a temporary session, supply `GITEA_TOKEN` and `GITEA_INSTANCE_URL`. This marketplace contains no binary or credentials.

## Claude Code

Run these commands:

```sh
claude plugin marketplace add unwnu/gitea-gt-skills
claude plugin install gitea-gt@gitea-gt-skills
```

## Codex

Run these commands:

```sh
codex plugin marketplace add unwnu/gitea-gt-skills
codex plugin add gitea-gt@gitea-gt-skills
```

Ask the agent to list issues, review a pull request, or inspect an Actions run. The skill is named `gt`. Claude Code also exposes it as `/gitea-gt:gt`.

## Sources

The [gt manual](https://docs.gitea.com/cli/) defines the commands. The [official Gitea MCP tool list](https://pkg.go.dev/gitea.com/gitea/gitea-mcp#hdr-Available_Tools) informed the resource map. The [tea skills](https://github.com/deevus/tea-skills) suggested workflow coverage. This project copies no source instructions and includes no MCP server.

`gt` 0.x can change flags and text output. The skill reads installed command help and uses JSON for structured output. This project is independent of Gitea and its maintainers.
