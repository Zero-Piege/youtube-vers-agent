# youtube-vers-agent

A Claude Code skill that transforms YouTube tutorials into Claude Code skills through dual-source verification (local Claude + Gemini) and specification crossing.

## Description

This skill converts YouTube tutorial content into structured Claude Code skills by:
1. Extracting key concepts and procedures from video transcripts
2. Verifying information through dual-source validation (video + documentation)
3. Creating properly formatted SKILL.md files following Claude Code conventions
4. Ensuring accuracy and completeness through cross-referencing

## When to Use

Use this skill when you want to:
- Convert educational YouTube content into reusable Claude Code skills
- Create skills based on tutorial videos about development tools, frameworks, or methodologies
- Ensure skill accuracy through verification against official documentation
- Build a library of verified skills from video learning resources

## Skill Workflow

### 1. Video Analysis Phase
- Process YouTube video using the watch skill to extract transcript and key frames
- Identify main topics, procedures, and code examples presented
- Structure the learning objectives and outcomes

### 2. Dual-Source Verification
- For each key concept/procedure, consult official documentation using context7-mcp or find-docs skills
- Cross-reference video content with authoritative sources
- Note any discrepancies or version differences
- Verify code examples work as demonstrated

### 3. Skill Creation
- Generate properly formatted SKILL.md file following Claude Code conventions
- Include clear description, when-to-use guidance, and step-by-step workflow
- Reference both video source and documentation sources used for verification
- Add appropriate tool recommendations based on verified procedures

### 4. Quality Assurance
- Test any code examples or procedures mentioned
- Validate that the skill follows Claude Code skill formatting standards
- Ensure the skill provides actionable, verifiable guidance

## Output

Produces a complete SKILL.md file in the appropriate .claude/skills/ directory that:
- Clearly defines the skill's purpose and applicability
- Provides specific usage guidelines
- Outlines a verifiable workflow
- References sources used for dual-source verification
- Follows Claude Code skill conventions

## Required Tools

- watch: For processing YouTube video content
- context7-mcp or find-docs: For dual-source verification against official documentation
- Bash: For file operations and skill creation

## Installation

1. Clone this repository:
   ```bash
   git clone https://github.com/Zero-Piege/youtube-vers-agent
   ```

2. Copy the skill to your Claude Code skills directory:
   ```bash
   cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
   ```

3. Reload plugins:
   ```bash
   /reload-plugins
   ```

## Usage

After installation, you can use the skill by providing a YouTube URL and specifying what you want to build:

```
/youtube-vers-agent [YouTube URL] [what to extract] [what to build]
```

Example:
```
/youtube-vers-agent https://youtu.be/zke3bTtvmLo Tout le projet Une skill Claude Code
```

## Example Usage

Transform a YouTube tutorial about creating React components into a Claude Code skill:
1. Use watch skill to extract video transcript and key points
2. Use context7-mcp to verify React component creation patterns against official React docs
3. Create SKILL.md with verified procedures for creating React components in Claude Code
4. Include references to both the YouTube tutorial and React documentation used

## Verification Standards

All created skills must:
- Reference at least two independent sources (video + documentation)
- Include specific, actionable steps
- Provide clear when-to-use guidance
- Follow established Claude Code skill formatting
- Contain verifiable procedures that can be tested

## License

MIT License - see [LICENSE](LICENSE) file for details.
