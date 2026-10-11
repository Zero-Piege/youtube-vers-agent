<table width="100%" cellpadding="0" cellspacing="0" bgcolor="#0b1220">
  <tr>
    <td>
      <table width="100%" cellpadding="16" cellspacing="0" bgcolor="#0b1220">
        <tr>
          <td align="left" valign="middle" width="50%">
            <p><strong><a href="#readme" style="color:#f2f5ff; text-decoration:none;">README</a></strong></p>
          </td>
          <td align="left" valign="middle">
            <p><a href="LICENSE" style="color:#dfe7f7; text-decoration:none;">Apache-2.0 license</a></p>
          </td>
          <td align="right" valign="middle">
            <p><a href="SECURITY.md" style="color:#dfe7f7; text-decoration:none;">Security</a></p>
          </td>
        </tr>
      </table>

      <hr size="1" color="#1e2a3b" />

      <table width="100%" cellpadding="32" cellspacing="0" bgcolor="#0b1220">
        <tr>
          <td align="center">
            <p><img alt="youtube-vers-agent logo" src="https://img.shields.io/badge/🎬-youtube--vers--agent-ff7a18?style=for-the-badge&logoColor=white" /></p>
            <h1 align="center" style="font-size:64px; margin:0; color:#f2f5ff; font-family:Georgia, serif;">youtube-vers-agent</h1>
            <p align="center" style="font-size:20px; color:#b7c1d9; margin-top:18px; margin-bottom:0;">
              Turn YouTube tutorials into executable Claude Code skills.
            </p>
          </td>
        </tr>
      </table>

      <table width="100%" cellpadding="12" cellspacing="0" bgcolor="#0b1220">
        <tr>
          <td align="center">
            <img alt="License" src="https://img.shields.io/badge/License-Apache%202.0-blue.svg" />
            <img alt="Node" src="https://img.shields.io/badge/node-%3E%3D20.0-4caf50.svg" />
            <img alt="Claude Code" src="https://img.shields.io/badge/Claude%20Code-ready-9C5CFF.svg" />
            <img alt="Status" src="https://img.shields.io/badge/Status-Active-22c55e.svg" />
          </td>
        </tr>
      </table>

      <table width="100%" cellpadding="18" cellspacing="0" bgcolor="#0b1220">
        <tr>
          <td align="center">
            <p><strong>Persistent memory compression system built for Claude Code.</strong></p>
          </td>
        </tr>
      </table>

      <table width="100%" cellpadding="0" cellspacing="0" bgcolor="#0b1220">
        <tr>
          <td align="center">
            <table cellpadding="10" cellspacing="0" border="0">
              <tr>
                <td bgcolor="#1f2937" style="border-radius:8px; padding:10px 18px;">
                  <strong>License</strong> <a href="LICENSE">Apache 2.0</a>
                </td>
                <td bgcolor="#1f2937" style="border-radius:8px; padding:10px 18px;">
                  <strong>Version</strong> 1.0.0
                </td>
                <td bgcolor="#1f2937" style="border-radius:8px; padding:10px 18px;">
                  <strong>Node</strong> &gt;=20.0
                </td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
    </td>
  </tr>
</table>

# README

A skill that transforms YouTube tutorials into Claude Code skills through dual-source verification (local Claude + Gemini) and specification crossing.

## Why this project exists

This repository helps you take a tutorial, compare multiple interpretive reads, and convert the result into an executable Claude Code skill.

## When to use

Use this skill when a user:
- pastes a YouTube link
- asks to "build this", "make it into a skill", or "create an agent"
- wants to convert tutorial content into executable Claude Code functionality

## Core workflow

1. Frame the request — determine scope and desired output
2. Dual-source verification — collect independent readings from local Claude and Gemini
3. Specification crossing — create a `notes/SPEC.md` with confirmed and disputed items
4. Skill construction — build the final skill with the creator workflow
5. Validation — test the generated skill on a real case

## Files created

- `notes/lecture-claude.md` — local Claude's six-part specification
- `notes/lecture-gemini.md` — Gemini's two six-part specifications
- `notes/SPEC.md` — crossed specification with labels
- generated skill in the output directory

## Dependencies

- `watch:watch` skill for video analysis
- `example-skills:skill-creator` for final skill generation
- Claude Code with subagent capability

## Quick start

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
```

Then follow the workflow described above and generate your own Claude Code skill from a YouTube tutorial.

## License

This project is licensed under the Apache License 2.0. See [LICENSE](LICENSE) for details.

## Security

See [SECURITY.md](SECURITY.md) for the security policy and reporting process.
