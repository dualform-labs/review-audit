# Contributing to review-audit

Thank you for your interest! This project welcomes issues and pull requests.

## What this project is

`review-audit` is a **documentation-only** skill: the entire behavior lives in `skills/review-audit/SKILL.md`, a single prompt that Claude Code loads. There is no build step and no runtime code. Changes are edits to that prompt (or the docs around it).

This is the **lightweight tier**. Its companion, [`review-audit-pro`](https://github.com/dualform-labs/review-audit-pro), is the heavy multi-agent tier. Keep them distinct: depth belongs in pro, not here.

## Design intent — keep these invariant

When proposing changes to `SKILL.md`, preserve the core contract:

- **No false PASS.** An axis can be `audited` only with concrete `file:line` + grep/run evidence. An unexamined axis can never be part of a `PASS`. Don't weaken this.
- **Coverage honesty.** Every axis reports `audited / partial / not-audited / n-a`. "I didn't check" is a first-class output, not a silent gap.
- **Read-only.** It proposes fixes, never applies them; a before/after checksum proves the tree is untouched.
- **Stay lean.** This tier deliberately does *not* fan out sub-agents or run live self-calibration — those are pro. A change that grows the token cost toward pro is moving in the wrong direction; it should **escalate to pro**, not bloat the lean tier.

## Testing a change

There is no automated test suite — the skill is a prompt. Validate changes empirically:

1. Install your edited `skills/review-audit/` into `~/.claude/skills/`.
2. Run `/review-audit <a real change>` end-to-end in Claude Code.
3. Confirm the coverage table is complete and that any `audited` axis cites concrete evidence (command / grep / `file:line`).
4. Describe what you ran and what you observed in the PR.

## Pull request checklist

- [ ] No hard-coded personal paths (`/Users/...`) or machine identifiers in the diff.
- [ ] The core invariants above are preserved (or the PR explains why a change is intended).
- [ ] The change keeps this tier lean — depth/rigor work belongs in `review-audit-pro`.
- [ ] `CHANGELOG.md` updated under `[Unreleased]` for user-visible changes.

## Licensing

By submitting a Contribution, you agree that it is licensed under the **Apache License 2.0**, the same license as the project. See `LICENSE`.
