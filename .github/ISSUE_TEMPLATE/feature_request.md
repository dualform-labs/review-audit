---
name: Feature request
about: Suggest a change to the audit workflow
title: "[idea] "
labels: enhancement
---

**The problem**
What part of the audit is missing or weak today? (an axis, the coverage table, the inline self-skepticism, the escalation-to-pro logic, the verdict …)

**Proposed change**
What you'd like `/review-audit` to do differently.

**Does it preserve the discipline?**
This skill's value depends on a few invariants:
no false PASS (an unverified axis can never be PASS), evidence-required findings
(`file:line` + grep/run output), read-only (it never mutates the target),
coverage honesty (no silent misses), and **staying lean** — depth, fan-out, and
detection-power proof belong in `review-audit-pro`, not here. Does your idea keep
these intact? If it relaxes one, say which and why the trade-off is worth it.

**Alternatives considered**
Anything you tried or ruled out.
