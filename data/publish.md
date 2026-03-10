# Publish Workflow

## Publish Command

Only after verification and approval:

```bash
npx clawhub publish <folder> \
  --slug "<slug>" \
  --name "<name>" \
  --version "<version>"
```

## Post-Publish Verification

After publishing:
1. Confirm success message
2. Optionally install to verify: `npx clawhub install <slug> --dir /tmp/verify`
3. Report to user: "Published [slug]@[version]"

## Version Guidelines

- `1.0.0` — First publish
- `1.0.1` — Small fixes (typos, clarifications)
- `1.1.0` — New content/features
- `2.0.0` — Major restructure

## If Something Goes Wrong

- Wrong slug? Cannot change. Contact ClawHub support.
- Wrong content? Publish new version with fix.
- Exposed private data? Publish sanitized version ASAP, contact support.
