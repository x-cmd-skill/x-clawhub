---
name: x-clawhub
description: |
  Helper for publishing x-cmd skills to ClawHub registry with safety checks.
  
  Validates skill structure, scans for sensitive data, creates preview for review.
  
  Note: Use `x skill` for skill creation and transformation. This module focuses on publish workflow.
  
  Requires x-cmd: Use x-cmd skill to install, see https://x-cmd.com/llms.txt.

license: Apache-2.0
compatibility: POSIX Shell

metadata:
  author: Li Junhao
  version: "1.0.0"
  category: x-cmd-extension
  tags: [x-cmd, publish, clawhub, validation]
---

# x-clawhub

> Publish helper for ClawHub registry with safety checks.

---

## Quick Start

```bash
# 1. Check for issues
x clawhub check ./x-my-skill

# 2. Create preview in /tmp
x clawhub preview ./x-my-skill

# 3. Review /tmp/publish-x-my-skill/

# 4. Publish (requires 'yes' confirmation)
x clawhub publish ./x-my-skill
```

---

## Scope

- **x skill** → Create and transform skills (use that for skill development)
- **x clawhub** → Publish skills to ClawHub registry (this module)

Publishing is **permanent**. This tool ensures:

1. **Validate Structure** - Required fields present
2. **ClawHub Sanitization** - Scans for data that shouldn't be public
3. **Preview & Confirm** - Review before final publish

---

## Commands

| Command | Purpose |
|---------|---------|
| `check <path>` | Dry-run validation |
| `preview <path>` | Create publish-ready copy in /tmp |
| `publish <path>` | Full workflow with confirmation |
| `sanitize` | Show ClawHub-specific privacy checklist |

---

## Validation Checks

### Structure
- YAML frontmatter present
- Required fields: `name:`, `description:`, `license:`

### Privacy Scan
| Pattern | Action |
|---------|--------|
| Local paths (`/Users/...`, `/home/...`) | ⚠️ Warn |
| Email addresses | ⚠️ Warn |
| IP addresses | ⚠️ Warn |
| Keywords (apikey, token, password) | ⚠️ Warn |
| Model refs ("Claude", "GPT") | ℹ️ Suggest generic |

---

## Sanitization Checklist

Run `x clawhub sanitize` to view full checklist.

Key items:
- [ ] Remove personal names, emails, usernames
- [ ] Remove internal URLs, project names
- [ ] Genericize examples (`mycompany` → `example`)
- [ ] No API keys, tokens, passwords
- [ ] No environment variable VALUES
- [ ] Generic model refs ("the agent" vs "Claude")

---

## Workflow Detail

### Step 1: Check

```bash
x clawhub check ./x-theme
```

Runs validation without modifying files.

### Step 2: Preview

```bash
x clawhub preview ./x-theme
```

Creates `/tmp/publish-x-theme/` with:
- SKILL.md (copy)
- lib/, data/ (if exist)
- FILES.txt (manifest)

**Always review preview before publish.**

### Step 3: Publish

```bash
x clawhub publish ./x-theme
```

Shows summary and requires typing `yes`:

```
Slug:    x-theme
Name:    x-theme
Version: 0.0.1
Files:
  SKILL.md
  lib/main

Ready to publish to ClawHub?
Type 'yes' to confirm:
```

---

## Post-Publish

Verify installation:

```bash
npx clawhub install x-theme --dir /tmp/verify-x-theme
```

---

## Notes

- **Never** publish without preview review
- **Always** run sanitize checklist for new skills
- Published skills are **permanent** - plan accordingly
