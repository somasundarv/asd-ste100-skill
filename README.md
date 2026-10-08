# asd-ste100-skill

A [Claude Code](https://claude.com/claude-code) skill that rewrites or drafts
text in ASD-STE100 (Simplified Technical English).

A skill is a folder with a `SKILL.md` file: YAML frontmatter (`name`,
`description`, `allowed-tools`, ...) plus Markdown instructions. Claude Code
loads the frontmatter at session start and pulls in the full instructions
when the task matches the `description`.

## What it does

**ASD-STE100** is the aerospace/defense controlled-language standard used
for maintenance and operational procedure docs: active voice, simple tenses,
one instruction per sentence, a fixed ~900-word approved vocabulary,
numbered steps.

Triggers on: "STE", "Simplified Technical English", "ASD-STE100", or a
request to write/rewrite a maintenance or ops procedure in unambiguous
English.

Details and rule tables: [`skills/asd-ste100/SKILL.md`](skills/asd-ste100/SKILL.md).

## Installation

Three ways to install, pick one.

### Option A: plugin marketplace (recommended)

This repo is also a Claude Code plugin marketplace (`.claude-plugin/marketplace.json`).

```
/plugin marketplace add somasundarv/asd-ste100-skill
/plugin install asd-ste100@asd-ste100-skill
```

Updates land with `/plugin marketplace update asd-ste100-skill` + `/plugin update asd-ste100`.

### Option B: per-user skill (all projects, no plugin system)

```bash
git clone https://github.com/somasundarv/asd-ste100-skill.git
cp -r asd-ste100-skill/skills/asd-ste100 ~/.claude/skills/asd-ste100
```

Or symlink instead of copy, to pick up future `git pull` updates:

```bash
ln -s "$(pwd)/asd-ste100-skill/skills/asd-ste100" ~/.claude/skills/asd-ste100
```

### Option C: per-project skill

```bash
git clone https://github.com/somasundarv/asd-ste100-skill.git
mkdir -p .claude/skills
cp -r asd-ste100-skill/skills/asd-ste100 .claude/skills/asd-ste100
```

### Verify

Start (or restart) Claude Code in a project, then ask:

```
what skills do you have available?
```

`asd-ste100` should be listed. Trigger it directly:

```
rewrite this in ASD-STE100: <your text>
```

## Adding a new skill to this repo

```bash
mkdir skills/my-skill
cat > skills/my-skill/SKILL.md <<'EOF'
---
name: my-skill
version: 1.0.0
description: |
  One paragraph: what it does and when Claude should use it.
license: MIT
compatibility: claude-code
allowed-tools:
  - Read
  - Write
  - Edit
---

# My Skill

Instructions go here.
EOF
git add skills/my-skill && git commit -m "Add my-skill"
```

## License

MIT — see each skill's `SKILL.md` frontmatter.
