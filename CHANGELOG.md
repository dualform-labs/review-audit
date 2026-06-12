# Changelog

All notable changes to this project are documented here.
The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## [1.0.0] - 2026-06-12

### Added

- Initial public release of the `review-audit` skill for Claude Code: a read-only, single-pass, six-axis code audit (correctness, wiring/anti-Potemkin, security, test efficacy, spec compliance, regression) run in the calling agent's own context — no sub-agent fan-out, low token cost.
- **No-false-PASS discipline**: an axis is `audited` only with concrete `file:line` / command / grep evidence; coverage is reported per axis (`audited / partial / not-audited / n-a`) and an unexamined axis can never form a `PASS`.
- **Read-only guarantee** via a source-only before/after checksum; the audit proposes fixes but never applies them.
- **Inline self-skepticism** in place of fresh-context refuters (the heavier adversarial verification lives in `review-audit-pro`), plus an explicit escalation path to the pro tier for releases, high-risk changes, or when per-run detection-power proof is needed.
- Configurable output language (`auto` / `ja` / `en`) via `skills/review-audit/config.yml`; code, commands, and `file:line` always stay in English.
- This tier carries no benchmark — single-pass detection is model-dependent; the measured/reproducible numbers belong to the companion `review-audit-pro`.

[Unreleased]: https://github.com/dualform-labs/review-audit/compare/v1.0.0...HEAD
[1.0.0]: https://github.com/dualform-labs/review-audit/releases/tag/v1.0.0
