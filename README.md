# ClawVet

Security scanner for OpenClaw SKILL.md files.

Scan any skill before your agent runs it — catch prompt injection, hidden unicode, dangerous shell vectors, and HTML comment overrides before it's too late.

## Usage

```bash
# scan a local file
bash tools/claw-vet.sh path/to/SKILL.md

# scan a remote skill
bash tools/claw-vet.sh https://raw.githubusercontent.com/user/repo/main/SKILL.md
```

## Output

```
✅ PASS   — No issues detected. Safe to load.
⚠️  WARN   — Suspicious content found. Review before loading.
⛔ FAIL   — Critical issues detected. Do NOT load this SKILL.md.
```

Findings include severity, category, and line number.

## What it detects

| Category | Examples |
|----------|----------|
| Hidden unicode | Zero-width chars, BOM markers invisible to humans but processed by LLMs |
| Prompt injection | "ignore previous instructions", role reassignment, DAN mode |
| Dangerous shell | `curl\|bash`, `eval`, `/dev/tcp`, `base64 -d\|bash`, `npx -y` |
| HTML comment overrides | Hidden instructions inside `<!-- -->` comments |

## Test fixtures

```bash
bash tools/claw-vet.sh tests/clawvet/good-skill.md       # → PASS
bash tools/claw-vet.sh tests/clawvet/malicious-skill.md  # → FAIL
bash tools/claw-vet.sh tests/clawvet/subtle-skill.md     # → WARN
```

## License

MIT. Do whatever you want with these.

## About

Made by [@BChopLXXXII](https://x.com/BChopLXXXII)

Vet your skills before your agent runs them. Your credentials will thank you.

Ship it. 🚀

---

If this helped, [star the repo](https://github.com/BChopLXXXII/clawvet) — it helps others find it.
