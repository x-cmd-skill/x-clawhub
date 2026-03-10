# Semantic Versioning for Skills

x-cmd skills follow [Semantic Versioning 2.0.0](https://semver.org/).

## Version Format

```
MAJOR.MINOR.PATCH
```

Example: `1.2.3`

## Version Rules

| Level | When to Bump | Example |
|-------|--------------|---------|
| **MAJOR** | Breaking changes, incompatible API changes | `1.0.0` → `2.0.0` |
| **MINOR** | New features, backwards compatible | `1.0.0` → `1.1.0` |
| **PATCH** | Bug fixes, backwards compatible | `1.0.0` → `1.0.1` |

## Practical Guidelines

### Initial Development

- Start with `0.1.0` for initial development
- `0.x.x` versions: anything may change at any time
- First stable release: `1.0.0`

### First Publish (1.0.0)

Mark as `1.0.0` when:
- Skill is feature-complete for initial use
- Public API (commands, options) is stable
- Ready for public use

### Patch Release (0.0.1 → 0.0.2)

Bump PATCH when:
- Fix typos in documentation
- Correct examples
- Fix bugs without changing behavior
- Clarify confusing descriptions

### Minor Release (0.1.0 → 0.2.0)

Bump MINOR when:
- Add new commands or options
- Add new examples
- Expand compatibility
- Add new sections to documentation

### Major Release (1.0.0 → 2.0.0)

Bump MAJOR when:
- Remove or rename commands
- Change command behavior significantly
- Restructure SKILL.md format
- Change required dependencies

## Pre-Release Tags (Optional)

For testing versions before stable release:

```
1.0.0-alpha.1
1.0.0-beta.1
1.0.0-rc.1
```

## Version in SKILL.md

```yaml
metadata:
  version: "1.2.3"  # Use quotes for string
```

## Version Check Before Publish

```bash
# Check current version
grep "version:" SKILL.md

# Remember: published versions are PERMANENT
# Plan your versioning carefully!
```
