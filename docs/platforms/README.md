# Platform support

youtube-vers-agent keeps one evidence-based workflow and adapts the packaging and instructions to each target. A portable Agent Skill is the shared starting point; each product still has its own discovery rules, tools, permissions, and availability.

## Supported targets

| Target | Repository format or path | What to expect |
| --- | --- | --- |
| Claude Code | **.claude/skills/youtube-vers-agent/** | Claude Code project skill. Claude-specific video tools are used only when installed and available. |
| OpenAI Codex | **.agents/skills/youtube-vers-agent/** | Repository skill discovered by Codex. Invoke it with **$youtube-vers-agent** or select it from the skill picker. |
| ChatGPT desktop Skills | Upload **.agents/skills/youtube-vers-agent/** as a skill package | Native Skills are limited to eligible accounts and workspace settings. If unavailable, use the project-instructions fallback below. |
| OpenAI API / Agents SDK | Put the skill directory in the agent sandbox or upload it through the API | The developer must make the files available to the runtime. This is an application integration, not an account-wide ChatGPT setting. Never include an API key in this repository. |
| Gemini CLI | **.agents/skills/youtube-vers-agent/** | Gemini CLI discovers workspace skills through **.agents/skills**; it also supports installing from a repository or linking a local folder. |
| GitHub Copilot | **.agents/skills/youtube-vers-agent/** | Copilot documents **.agents/skills** as a project skill location for supported Copilot agents and clients. |
| ChatGPT Projects | **docs/platforms/chatgpt-project-instructions.md** | Instructions apply only to chats in the selected Project; they are not a native Skill and do not affect other chats. |

The portable package is under **.agents/skills/youtube-vers-agent/**. The Claude Code copy remains under **.claude/skills/youtube-vers-agent/** because Claude Code uses its own project discovery path. Keep the two skill instructions aligned when the shared workflow changes, while retaining platform-specific invocation and tool guidance.

## ChatGPT availability

ChatGPT Skills and Project instructions are different features. Skills are currently available only to eligible ChatGPT Business, Enterprise, Healthcare, and Edu users, and workspace administrators can control access. A free account may therefore use the project-instructions fallback rather than upload the Skill.

For current account and workspace eligibility, use the [official Skills in ChatGPT guide](https://help.openai.com/en/articles/20001066-skills-in-chatgpt). The [OpenAI Build Skills guide](https://developers.openai.com/codex/skills) documents the Agent Skills package and Codex discovery. Project scope is documented in [Projects in ChatGPT](https://help.openai.com/en/articles/10169521-projects-in-chatgpt).

## Install by target

### Claude Code

Copy **.claude/skills/youtube-vers-agent/** into **~/.claude/skills/youtube-vers-agent/**, or keep it in the repository for project use. Claude-specific skills such as **watch:watch** and **skill-creator** are optional dependencies and must be available before the workflow uses them.

### Codex

Codex discovers repository skills under **.agents/skills/**. Open the repository in Codex and select the skill, or invoke it with **$youtube-vers-agent**. If the skill list does not refresh, restart Codex.

### ChatGPT desktop

When Skills are enabled for the user's account and workspace, upload the portable skill folder from the Skills area. Review the package and test it before relying on it. When Skills are not available, copy **chatgpt-project-instructions.md** into the Project's instructions field.

### OpenAI API and Agents SDK

Expose the portable skill directory to the agent runtime using the documented sandbox or capability-directory mechanism, or upload a version through the Skills API. API usage requires a separately configured application and credentials; this repository does not provide or store them.

### Gemini CLI

Gemini CLI can discover the skill from the repository's **.agents/skills/** folder. It also supports **gemini skills install** for repository-based installation and **gemini skills link** for local development. Remote installation and activation may require explicit consent in Gemini CLI.

### GitHub Copilot

Copilot supports project skills in **.agents/skills/** for its documented skill-enabled clients. Keep any repository-wide coding conventions in the relevant instructions file; use this skill for the on-demand YouTube workflow.

## Why there is no one-click installer for every product

A Skill contains instructions and optional resources. It does not grant video access, connect Gemini, provide an API key, authorize shell commands, or create an MCP connection. The product must support the package format, and the user must configure any tools the tutorial requires.

## Official platform references

- [Agent Skills specification](https://agentskills.io/specification)
- [Claude Code skills](https://code.claude.com/docs/en/skills)
- [OpenAI Build Skills: ChatGPT and Codex](https://developers.openai.com/codex/skills)
- [OpenAI API skills](https://developers.openai.com/api/docs/guides/tools-skills)
- [Gemini CLI Agent Skills](https://github.com/google-gemini/gemini-cli/blob/main/docs/cli/using-agent-skills.md)
- [GitHub Copilot agent skills](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills)
- [Skills in ChatGPT](https://help.openai.com/en/articles/20001066-skills-in-chatgpt)
- [Projects in ChatGPT](https://help.openai.com/en/articles/10169521-projects-in-chatgpt)
