# youtube-vers-agent

A skill that transforms YouTube tutorials into Claude Code skills through dual-source verification (local Claude + Gemini) and specification crossing.

## When to Use

Use this skill when a user:
- Pastes a YouTube link
- Asks to "build this", "make it into a skill", or "create an agent"
- Wants to convert tutorial content into executable Claude Code functionality

## Core Workflow

1. **Frame the request** - Determine scope and desired output
2. **Dual-source verification** - Get independent readings from local Claude and Gemini
3. **Specification crossing** - Create SPEC.md with CONFIRMED/UNE SOURCE/DÉSACCORD labels
4. **Skill construction** - Use skill-creator to build the final skill
5. **Validation** - Test the generated skill on a real case

## Files Created

- `notes/lecture-claude.md` - Local Claude's six-part specification
- `notes/lecture-gemini.md` - Gemini's two six-part specifications
- `notes/SPEC.md` - Crossed specification with labels
- Generated skill in output directory

## Dependencies

- watch:watch skill (for video analysis)
- example-skills:skill-creator (for skill building)
- Claude Code with subagent capability