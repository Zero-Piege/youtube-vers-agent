# ✨ youtube-vers-agent

**Transform YouTube tutorials into executable Claude Code skills through intelligent analysis and dual-source verification.**

---

## Overview

A minimal, powerful system for converting video content into production-ready Claude Code skills. Leverages dual-source verification (local Claude + Gemini) and specification crossing to ensure accuracy.

## Core Features

- **Dual-source verification** — Independent analysis from Claude and Gemini
- **Specification crossing** — Validated consensus extraction
- **Automated skill generation** — Convert tutorials to executable code
- **Quality validation** — Real-world testing included

## Quick Start

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
```

## Workflow

1. **Frame** the request scope
2. **Verify** with dual independent sources
3. **Cross** specifications with conflict resolution
4. **Generate** the final skill
5. **Validate** on real cases

## Output

- `notes/lecture-claude.md` — Claude's interpretation
- `notes/lecture-gemini.md` — Gemini's interpretation  
- `notes/SPEC.md` — Merged specification with confidence levels
- Generated skill artifact

## Requirements

- Node.js ≥ 20.0
- Claude Code runtime with subagent support
- `watch:watch` skill (video analysis)
- `example-skills:skill-creator` (skill generation)

## License

Apache License 2.0 — [See LICENSE](LICENSE)

## Security

[Security Policy](SECURITY.md)

---

**Built for Claude Code.** Inspired by excellence.
