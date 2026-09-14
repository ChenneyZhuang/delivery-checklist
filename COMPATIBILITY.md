# Compatibility / 兼容性

One SKILL.md, no scripts, no dependencies beyond what the agent already has. 安装即用，无脚本依赖。

| Agent | Install | Notes |
|---|---|---|
| Claude Code | `npx skills add ChenneyZhuang/delivery-checklist` or clone to `~/.claude/skills/delivery-checklist/` | model-invoked via description triggers |
| Codex CLI | `npx skills add ChenneyZhuang/delivery-checklist` | same SKILL.md |
| Cursor | `npx skills add ChenneyZhuang/delivery-checklist` | loads per CLI mapping |
| OpenCode / Windsurf / Gemini CLI / Cline / AMP / GitHub Copilot | `npx skills add ChenneyZhuang/delivery-checklist` | 75+ agents via skills CLI |
| DSH | clone, `dsh plugin --profile <name> add link:<repo>` | `dsh.bundle` manifest included |
| Hermes | `cp -r` into `~/.hermes/profiles/<profile>/skills/delivery-checklist/` | verify with `hermes skills` |

Runtime needs: file read/write access; where the skill's steps call for web search or shell, the runtime must provide them or the skill's integrity rules require labeling results `unverified`. 运行时需要文件读写；涉及搜索或 shell 的步骤需运行时支持，否则按诚信规则标注 `unverified`。
