# Corrections Log

Every change to `sbr.py` or its references, justified. No entry, no
change — this is the discipline the Methodology panel set: a method
that can be edited without a paper trail is a method that will drift the
same way the pre-battery estate did.

**Format per entry:**

```
## YYYY-MM-DD — <short title>

**Forced by:** <run ID / card ID that failed>
**Bin:** A (agent) / B (method bug) / C (environment) / D (test itself)
**What changed:** <the actual diff, described>
**Which Law's purpose it serves:** <name the Law or gate>
**Falsifiable prediction:** <what should now be true that wasn't>
**Ratified by:** <fresh session that restated the justification cold —
  required for anything touching sbr.py itself>
**Regression re-run:** <which prior runs were re-executed after this
  change, and result>
```

**Rules, restated from RUBRIC.md and the plan:**
- Thresholds may tighten on evidence at any time.
- Thresholds may only be **loosened** after demonstrating, against a
  frozen answer key, that the current threshold rejects claims that are
  actually true — across at least 2 independent runs — plus a
  devil's-advocate review of the loosening specifically.
- Any **addition** (a phase, a Law, a scoring dimension, a document) must
  cite a reader-facing failure it fixes (a real M-T2-style cold-reader
  failure, not a theoretical one), and must not regress process-economy
  or the reader gates.
- The author session may draft a change. It may not ratify its own
  change — a fresh session, given only this log's entry and the method
  files, must be able to restate the justification without being told
  it, before the change is considered live.

---

## Entries

## 2026-08-28 — Split DIVERSITY into two labeled sub-checks in Phase 5 doc_schema

**Forced by:** M-T2 HEAVY shakedown (unscored — first-ever HEAVY execution)
**Bin:** B (method bug — prose underspecified what the code already did)
**What changed:** `PHASE_AGENTS[5]["doc_schema"]` split the single line
`"DIVERSITY — personas present, media modes present — PASS/FAIL"` into
two explicit lines, one for persona diversity and one for media-mode
diversity, matching `gate_check()`'s actual behavior (two independent
failure conditions, both currently labeled "DIVERSITY" in the code's own
failure messages).
**Which Law's purpose it serves:** Law 8 (phases run in order, and their
exit gates must be unambiguous) and Law 9 (a phase without its document
didn't happen — a merged verdict that silently drops one sub-check is
functionally an undocumented phase).
**Falsifiable prediction:** a future fresh agent running Phase 5 will
report both persona and media-mode diversity as separate PASS/FAIL lines
without needing to read `gate_check()`'s source to notice they're
distinct.
**Ratified by:** not yet — drafted and applied by the author session
under time pressure ahead of wave 1. Flagged honestly rather than
falsely marked ratified. Needs a fresh-session read-back before being
treated as fully settled per the discipline this file sets for itself.
**Regression re-run:** not yet re-run against a fresh LIGHT card (the
change only touches Phase 5's doc_schema text, not LIGHT/HEAVY logic or
thresholds, so risk of regression is low — but this is a claim, not a
demonstrated fact, until it's actually re-run).

**Logged, not yet acted on (from the same shakedown):**
- No mechanism distinguishes a CONFIRMED claim sitting at exactly the
  origin threshold from one comfortably above it. Candidate Bin B, but
  withheld pending a reader-facing failure per the anti-ratchet rule —
  M-T2's cold-reader protocol (its second, scored run) is the natural
  test for whether this omission actually confuses a reader.
- The shakedown agent skipped opening `references/independence-test.md`
  at VERIFY, against `sbr.py`'s own explicit instruction, judging the
  inline description sufficient. Bin A (agent discipline, not a method
  bug) — logged as a grading-rubric addition: judges must verify cited
  references were actually opened, not just referenced.
- CHECK felt like ceremony as a standalone document on a bounded-scope
  HEAVY topic (five one-line verdicts). Bin D-ish design note, no action
  — needs evidence across more HEAVY cards, not one shakedown, before
  touching document structure.
- The loop-back machinery (`buffer` truncation, `loop_counts` per
  target in `run_sbr`) was never exercised — this shakedown run passed
  every gate on the first try. Not a bug; a coverage gap in this run.
  V-T3 (wave 2) is specifically designed to force a loop and will be the
  real test of this surface.
