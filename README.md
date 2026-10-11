<div style="background:#0b1220; color:#edf3ff; font-family:Segoe UI, Arial, sans-serif; border:1px solid #1d2a39; border-radius:12px; overflow:hidden; max-width:1200px; margin:0 auto;">
  <div style="display:flex; align-items:center; justify-content:space-between; padding:16px 22px 14px; border-bottom:1px solid #263548; background:#0b1220;">
    <div style="display:flex; align-items:center; gap:30px; font-size:18px; font-weight:700;">
      <span style="color:#f7f9ff; border-bottom:3px solid #ff5b28; padding-bottom:12px;">README</span>
      <span style="color:#dfe9f8; opacity:0.9; font-weight:500;">Apache-2.0 license</span>
      <span style="color:#dfe9f8; opacity:0.9; font-weight:500;">Security</span>
    </div>
    <div style="display:flex; align-items:center; gap:18px; color:#dfe9f8; font-size:20px; opacity:0.9;">
      <span>◌</span>
      <span>✎</span>
      <span>☰</span>
    </div>
  </div>

  <div style="padding:34px 26px 18px; background:#0b1220;">
    <div style="display:flex; align-items:center; justify-content:center; gap:24px; margin:8px auto 20px;">
      <div style="position:relative; width:120px; height:120px; border-radius:50%; background:radial-gradient(circle at center, #ff9d56 0%, #ff7a32 30%, #ffb870 52%, #f26d2e 68%, #e75a28 100%); box-shadow:0 0 0 10px rgba(255,122,61,0.14);">
        <div style="position:absolute; inset:0; display:grid; place-items:center;">
          <div style="width:42px; height:42px; border-radius:50%; background:#ffb874; box-shadow:0 0 0 8px rgba(255,179,106,0.16);"></div>
        </div>
      </div>
      <h1 style="margin:0; font-family:Georgia, 'Times New Roman', serif; font-style:italic; font-size:68px; letter-spacing:-0.06em; font-weight:500; color:#f2f5ff;">youtube-vers-agent</h1>
    </div>

    <div style="border-top:1px solid #2b3a4a; border-bottom:1px solid #2b3a4a; margin-top:18px; padding:18px 0;">
      <div style="display:flex; justify-content:center; align-items:center; flex-wrap:wrap; gap:18px 24px; color:#dfe9f8; font-weight:700; font-size:14px; letter-spacing:0.06em; text-transform:uppercase;">
        <div style="display:flex; align-items:center; gap:10px;">
          <span style="display:inline-block; width:0; height:0; border-top:8px solid transparent; border-bottom:8px solid transparent; border-left:14px solid #dfe9f8; margin-right:4px;"></span>
          <span>Version</span>
          <span style="color:#7fe0a3;">1.0</span>
        </div>
        <div style="display:flex; align-items:center; gap:10px;">
          <span style="color:#7fe0a3; font-size:16px;">●</span>
          <span>Node</span>
          <span style="color:#7fe0a3;">≥ 20.0</span>
        </div>
        <div style="display:flex; align-items:center; gap:10px;">
          <span style="color:#86c7ff; font-size:16px;">✦</span>
          <span>Claude Code</span>
          <span style="color:#86c7ff;">ready</span>
        </div>
      </div>
    </div>

    <div style="text-align:center; margin-top:28px; margin-bottom:18px;">
      <strong style="font-size:30px; color:#edf3ff; letter-spacing:-0.03em;">Persistent memory compression system built for Claude Code.</strong>
    </div>

    <div style="display:flex; justify-content:center; flex-wrap:wrap; gap:12px; margin-top:16px;">
      <span style="display:inline-block; padding:8px 14px; border-radius:8px; background:#1c2f45; border:1px solid #2e435d; color:#edf3ff; font-weight:600;">License: Apache 2.0</span>
      <span style="display:inline-block; padding:8px 14px; border-radius:8px; background:#193629; border:1px solid #2a5644; color:#d9ffeb; font-weight:600;">Version: 1.0.0</span>
      <span style="display:inline-block; padding:8px 14px; border-radius:8px; background:#243a63; border:1px solid #3a4f7f; color:#dfe7ff; font-weight:600;">Node ≥ 20.0</span>
    </div>

    <div style="display:flex; justify-content:center; margin-top:34px; margin-bottom:8px;">
      <div style="display:inline-flex; align-items:center; gap:12px; border:1px solid #2e4058; background:#171f2d; border-radius:12px; padding:12px 18px; color:#edf3ff; font-weight:700; letter-spacing:0.04em; text-transform:uppercase;">
        <span style="font-size:28px; color:#f0d48b;">✦</span>
        <span>GitHub Trending</span>
        <span style="color:#ffd86f;">#1 Repository Of The Day</span>
      </div>
    </div>
  </div>
</div>

<hr style="margin:28px 0 14px; border:0; border-top:1px solid #2a384d;" />

# README

A skill that transforms YouTube tutorials into Claude Code skills through dual-source verification (local Claude + Gemini) and specification crossing.

## Overview

This repository helps convert a tutorial into a usable Claude Code skill by comparing multiple interpretations, validating contradictions, and generating a concrete specification before building the final output.

## When to use

Use this skill when a user:
- pastes a YouTube link
- asks to "build this", "make it into a skill", or "create an agent"
- wants to turn tutorial content into executable Claude Code functionality

## Core workflow

1. **Frame the request** — determine scope and desired output
2. **Dual-source verification** — gather independent readings from local Claude and Gemini
3. **Specification crossing** — compare and reconcile the results in `notes/SPEC.md`
4. **Skill construction** — build the final skill with the project workflow
5. **Validation** — test on a real use case

## Files created

- `notes/lecture-claude.md` — local Claude's six-part specification
- `notes/lecture-gemini.md` — Gemini's independent read
- `notes/SPEC.md` — crossed specification with confirmed/disputed items
- generated skill in the output directory

## Requirements

- Node.js ≥ 20.0
- Claude Code with subagent capability
- `watch:watch` skill for video analysis
- `example-skills:skill-creator` for skill generation

## License

This project is licensed under the Apache License 2.0. See [LICENSE](LICENSE).

## Security

See [SECURITY.md](SECURITY.md) for the reporting and security policy.
