# local-repo-finder-skill

[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-compatible-blue)](https://agentskills.io)
[![License](https://img.shields.io/badge/License-Apache%202.0-green.svg)](LICENSE)

An Agent Skill for fast detection of local Git repository paths.

## Problem

- You want to reference another repository from SlashCommand or AgentSkills
- But directory layouts differ between developers
- Hardcoding paths makes sharing impossible

## Solution

Use `fd` command for fast repository detection (approximately 30x faster than `find`).
```bash
fd -H "^\.git$" ~/ -t d 2>/dev/null | xargs -I {} dirname {} | grep "target-repo$" | head -1
```

## Installation

### Claude Code (Plugin)
```bash
/plugin marketplace add soramarjr/local-repo-finder-skill
/plugin install local-repo-finder
```

### Manual
```bash
cp -r local-repo-finder ~/.claude/skills/
```

## Prerequisites
```bash
# macOS
brew install fd

# Ubuntu/Debian
apt install fd-find
```

## Compatibility

- ✅ Claude Code
- ✅ GitHub Copilot (VS Code)
- ✅ OpenAI Codex CLI

## References

- [Original Article (Zenn)](https://zenn.dev/soramarjr/articles/e0de39a73bfbcd)
- [fd - GitHub](https://github.com/sharkdp/fd)

## License

Apache License 2.0
