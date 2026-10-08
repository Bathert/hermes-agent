# Hermes Agent — agent entry point

For code, tests, dependencies or PR review, load [CODING_STANDARDS.md](CODING_STANDARDS.md) and follow its task index; docs-only work needs none of it. Read every matching area guide below.

## Invariants

- Keep the cached system-prompt prefix stable across a conversation. Only compression changes past context; prompt-changing slash commands defer until the next session unless invoked with `--now`.
- Keep core tools small: extend existing code or use CLI + skill, gated tool, plugin or MCP first.
- Verify bugs and original intent on current `main`. Automated triage closes only `implemented_on_main`, `cannot_reproduce` or `incoherent`; subjective scope belongs to maintainers. [Rubric](website/docs/developer-guide/contributing.md).
- Report §3.1 vulnerabilities privately, never in a public PR: [SECURITY.md](SECURITY.md).

## Routes

| Work | Read |
|---|---|
| Agent | [agent](agent/AGENTS.md) |
| CLI, profiles | [hermes_cli](hermes_cli/AGENTS.md) |
| Gateway, adapters | [gateway](gateway/AGENTS.md); new adapter: [guide](gateway/platforms/ADDING_A_PLATFORM.md) |
| Tools | [tools](tools/AGENTS.md) |
| Plugins, catalog | [plugins](plugins/AGENTS.md), [catalog](plugin-catalog/README.md) |
| TUI, web | [tui_gateway](tui_gateway/AGENTS.md), [web](web/AGENTS.md) |
| Desktop | [desktop](apps/desktop/AGENTS.md), [src](apps/desktop/src/AGENTS.md) |
| Skills, curator | [skills](skills/AGENTS.md) |
| Cron, kanban | [cron](cron/AGENTS.md) |
| Tests, deps, host | [tests](tests/AGENTS.md), [pm](pm/AGENTS.md), [platform](hermes_platform/AGENTS.md) |

Root modules follow their owner: `run_agent.py` → agent; `cli.py` → hermes_cli; `toolsets.py`/`model_tools.py` → tools; `pyproject.toml`/`uv.lock` → pm. Plugin loader → plugins; web routers → web; curator → skills. [Long form](website/docs/developer-guide/).
