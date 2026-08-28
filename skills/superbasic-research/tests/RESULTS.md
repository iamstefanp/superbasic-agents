# Results Registry

One row per graded run, pinned to the `sbr.py` git SHA it ran against.
This is the regression memory — after any change logged in
`CORRECTIONS.md`, the affected cards get re-run and a new row lands here,
never overwriting the old one.

**Pre-battery runs**, for reference (not against this battery's cards,
graded informally by the author session — the exact self-grading problem
this battery exists to fix; included here only as provenance, not as
evidence):

| Date | Card | Mode | SHA | Verdict | Notes |
|---|---|---|---|---|---|
| 2026-08-27 | (ad hoc — EU AI Act GPAI obligations) | LIGHT | pre-battery | ungraded | "Stranger test A." Found 3 method bugs, fixed. DIVERSITY gate failed and looped correctly. Self-graded — superseded by V-T2 in this battery. |
| 2026-08-27 | (ad hoc — Marginalia Search funding) | LIGHT | pre-battery | ungraded | "Stranger test B." 11 sources collapsed to 3 origins; caught an over-CONFIRMED claim in the reconstruction. Self-graded. |

---

## Battery runs

| Date | Card | Mode | SHA | Verdict | Gates | Scores | Notes / linked corrections |
|---|---|---|---|---|---|---|---|
| 2026-08-28 | M-T2 (shakedown) | HEAVY | f16ecb1 | **UNSCORED — shakedown** | CHECK PASS (first pass), VERIFY PASS (first pass), 0 loops | not graded | First-ever HEAVY execution. Found 1 method bug (fixed, see CORRECTIONS.md 2026-08-28), 1 agent-discipline lapse (skipped opening a required reference), 1 design question deferred pending reader evidence. **Loop machinery entirely untested — biggest open risk heading into wave 2.** Full transcript not preserved in repo; findings captured in CORRECTIONS.md. |

---

## How to read this file

- **Verdict** is the RUBRIC.md one-page verdict: PASS / PASS-WITH-FINDINGS / FAIL.
- **SHA** must match a real commit in `superbasic-agents`. A row with no
  SHA is not a battery result.
- A card re-run after a `CORRECTIONS.md` entry gets a new row, not an
  edit to the old one — the history of "it used to fail this way" is
  part of the record.
- M-T1 gets two rows per battery (both blind runs) plus, if AMBER, a
  third.
- M-T2 gets an unscored shakedown row (marked as such) before its first
  scored row.
