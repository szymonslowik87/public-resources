# skill-audit

A Claude skill for auditing prompt instruction files (SKILL.md and similar) before installing them in AI workflows.

Created by [Szymon Słowik](https://www.szymonslowik.com) - SEO strategist and AI workflow practitioner.

---

## What it does

Before you load a skill into your Claude setup, this skill acts as a security gate. It scans the file for five threat categories and returns a structured verdict: **SAFE TO INSTALL**, **REVIEW REQUIRED**, or **DO NOT INSTALL**.

It is pattern-based, not execution-based. Think of it as a pre-flight checklist, not a firewall.

---

## Threat categories

| ID | Threat | What it catches |
|---|---|---|
| T1 | Data exfiltration | URLs, fetch/curl references, instructions to send output externally |
| T2 | Prompt injection | Override instructions, persona switches, "silently do X" patterns |
| T3 | Silent side effects | Secondary actions hidden alongside the main task |
| T4 | Scope creep | Instructions to access files, credentials, or conversation history beyond stated purpose |
| T5 | Obfuscation | Base64 encoding, hidden whitespace, instructions buried in code blocks |

---

## How to use

### Installation

Add `SKILL.md` to your Claude skill library. The recommended path follows whatever convention your setup uses, for example:

```
/mnt/skills/user/skill-audit/SKILL.md
```

### Triggering the skill

In Claude, paste or reference the skill you want to audit and use any of these phrases:

- "Audit this skill"
- "Is this skill safe?"
- "Review this skill file"
- "Run a skill security check on this"

### Output

Claude will return a structured report:

```
SKILL AUDIT REPORT
File: [filename]
Date: [date]

FINDINGS:
[T1 - Data exfiltration]: CLEAN / [LEVEL: quote]
[T2 - Prompt injection]: CLEAN / [LEVEL: quote]
[T3 - Silent side effects]: CLEAN / [LEVEL: quote]
[T4 - Scope creep]: CLEAN / [LEVEL: quote]
[T5 - Obfuscation]: CLEAN / [LEVEL: quote]

VERDICT: [SAFE TO INSTALL / REVIEW REQUIRED / DO NOT INSTALL]

ACTION: [specific recommendation]
```

---

## When to run an audit

- Before installing any skill from an external, community, or unknown source
- When a skill produces unexpected output or behavior
- When reviewing shared prompt libraries
- When onboarding team members who bring their own skill sets
- When a skill is updated - re-audit on every version change

---

## Limitations

This skill does pattern matching, not sandboxed execution. A sufficiently subtle or indirect skill could pass this audit and still cause unexpected behavior in practice.

**SAFE TO INSTALL does not mean zero risk.** It means no obvious threat patterns were detected given the current taxonomy.

For high-stakes environments, combine this audit with a sandboxed test run before deploying to live workflows.

---

## Disclaimer

This skill is provided as a best-effort security heuristic. Szymon Słowik does not take responsibility for the safety or behavior of skills audited using this tool. The audit may produce false negatives (missing a real threat) or false positives (flagging legitimate instructions). Always apply your own judgment. You are responsible for what you install in your AI workflows.

---

## About the author

Szymon Słowik is an SEO strategist, founder of [takaoto.pro](https://www.takaoto.pro), and an international conference speaker. He builds structured methodologies for SEO, AI-driven search visibility, and LLM-integrated workflows.

- Website: [szymonslowik.com](https://www.szymonslowik.com)
- Agency: [takaoto.pro](https://www.takaoto.pro)

This skill is part of his personal Claude skill library, shared publicly for the SEO and AI practitioner community.
