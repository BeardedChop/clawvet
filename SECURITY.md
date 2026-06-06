# Security Policy

ClawVet scans agent skill files before they are loaded.

## Supported Versions

The `main` branch is the supported version.

## Reporting A Vulnerability

Open a GitHub issue with:

- the affected file or command
- the unexpected behavior
- a minimal sample if possible

Do not include secrets, private keys, tokens, or private machine details in public issues.

## Security Notes

- Review scanner output before trusting a third-party skill.
- Do not run unknown shell commands copied from untrusted skills.
- Treat hidden Unicode, prompt injection, and remote shell execution findings as high risk.
