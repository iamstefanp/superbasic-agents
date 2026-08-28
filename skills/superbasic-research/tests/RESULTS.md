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
| 2026-08-28 | V-T1 | LIGHT | af727bd | mechanical PASS (6/6), Layer-0/2 grading pending | CHECK PASS, VERIFY PASS, 0 loops | pending | Trap beaten: traced 4 apparently-independent sources (incl. Similarweb's own "independent" figure) to one origin; capped MAU claim at LIKELY correctly. |
| 2026-08-28 | V-T4 | LIGHT | af727bd | mechanical PASS (6/6), Layer-0/2 grading pending | CHECK PASS, VERIFY PASS, 0 loops | pending | Trap beaten: reported 4 catalog figures, marked only the disagreement CONFIRMED, no false precision. |
| 2026-08-28 | F-T1 | LIGHT | af727bd | mechanical PASS (6/6), Layer-0/2 grading pending | CHECK PASS, VERIFY PASS, 0 loops | pending | Trap beaten: found 7 distinct "Meridian Capital" entities on page 1, refused to merge a criminally-prosecuted defendant into the legitimate firm's profile. |
| 2026-08-28 | F-T4 | LIGHT | af727bd | mechanical PASS (6/6), Layer-0/2 grading pending | CHECK PASS, VERIFY PASS, 0 loops | pending | Trap beaten: distinguished "blocked" (CourtListener 403, PACER) from "not found"; caught a law-firm site citing other marketing sites, not the docket. |
| 2026-08-28 | M-T1 run 1 | LIGHT | af727bd | mechanical PASS (6/6 after checker fix) | CHECK PASS, VERIFY PASS, 0 loops | pending | Replication card, run 1 of 3. See run 2/3 rows — **this card's own AMBER/FAIL protocol triggered.** |
| 2026-08-28 | M-T1 run 2 | LIGHT | af727bd | mechanical PASS (6/6 after checker fix) | CHECK PASS, VERIFY PASS, 0 loops | pending | Replication card, run 2 of 3, blind to run 1. **CONFIRMED-overlap vs run 1 was below the 60% floor — outright FAIL per BATTERY.md's own rule.** No CONFIRMED-vs-contradicted flip. Root cause: `sbr.py` had no per-KRQ canonical-source check, so which specific statute section an agent happened to find was arbitrary. Forced the 2026-08-28 PLAN/INTEL correction (CORRECTIONS.md). |
| 2026-08-28 | M-T1 run 3 (post-fix) | LIGHT | e189cc8 | mechanical PASS (partial — my saved copy was over-compressed, not a run defect) | CHECK PASS, VERIFY PASS, 0 loops | pending | Replication card, run 3 of 3, testing the correction. **Result: partial confirmation.** Registration mechanism and mandatory-insurance basis now CONFIRMED unanimously across all 3 runs. Headline claim moved 1-of-2 → 2-of-3 CONFIRMED. Surfaced a new finding (§43 LuftVG delegates its minimum-coverage figure to an unlocated ordinance) neither prior run reached. Second-tier facts (geo-zones, exact fines, exact insurance figure) still did not converge on the same statute section across runs. **Decision: accepted as an inherent property of open research on a scattered-statute subject, not carried forward as an open method gap** — see CORRECTIONS.md 2026-08-28 for full reasoning. |
| 2026-08-28 | V-T3 | HEAVY | af727bd | **PASS-WITH-FINDINGS** (adversarial judge, independent re-verification) | CHECK PASS, VERIFY FAIL→LOOP→LOOP→FAIL, status PARTIAL | Verif 8/10 · Calib 26/30 · Reach 7/10 | Judge independently fetched TechCrunch's actual article: confirms both the run's sole CONFIRMED claim ("unclear who led") and its independence collapse (TechCrunch attributes to The Information). Independently fetched the "$23B Series E-6" claim: confirmed zero citation, matching the run's exclusion. One dissonant low-quality source (texau.com naming a lead investor) weighed and correctly discounted against the primary TechCrunch statement. First real exercise of the loop-back machinery — worked as designed. |
| 2026-08-28 | F-T3 | HEAVY | af727bd | **PASS-WITH-FINDINGS** (adversarial judge) | CHECK PASS, VERIFY PASS, 0 loops, status COMPLETE | Verif 7/10 · Calib 27/30 · Reach 8/10 | Judge spent real effort (4 searches) trying to find a named beneficial owner for the tanker; found none — UNKNOWN survives adversarial spot-check. Verified the Grokipedia near-miss is real and checkable, not a staged admission. **Flagged tension:** run declared COMPLETE where the card's narrative intent leaned PARTIAL — mechanically sound (no gate failed) but a legitimate point of disagreement, the same boundary F-T2 hit from the other direction. |
| 2026-08-28 | F-T2 | HEAVY | af727bd | **PASS-WITH-FINDINGS** (adversarial judge) | CHECK PASS, VERIFY PASS, 0 loops, status PARTIAL (contested) | Verif 7/10 · Calib 25/30 · Reach 8/10 | Judge independently re-derived Stefan's PARTIAL-was-wrong decision *before* reading CORRECTIONS.md, then compared and agreed. All 3 spot-checked facts (administration since Nov 2025, current administrator, Carlyle sale) confirmed live. Bulgarian-language sourcing judged substantive, not decorative (caught and excluded a real 4-outlet syndicate). **New finding:** RUBRIC.md's "PARTIAL bluffed" gate only catches over-claiming, has no clause for this run's under-claiming direction — logged to RUBRIC.md 2026-08-28. |
| 2026-08-28 | F-T1 | LIGHT | af727bd | **PASS-WITH-FINDINGS** (adversarial judge) | CHECK PASS, VERIFY PASS, 0 loops, status COMPLETE | Verif 8/10 · Calib 24/30 · Reach 9/10 | Judge searched specifically for entity-blending (the card's core trap) and found none — every regulatory/litigation fact stayed correctly scoped to its entity, collision named as the headline finding. Independently verified 2 facts live (Brooks/Herzka transition, Freddie Mac dispute). **Cross-battery flag:** this run's absence-claim marked ESTIMATED vs. F-T3's structurally similar absence-claim marked CONFIRMED-as-absence — same shape of claim, different confidence treatment, worth resolving directly. |
| 2026-08-28 | V-T2 | LIGHT | 7c81f5f | **ground-truth audit vs. frozen key — BEAT THE KEY** | CHECK PASS, VERIFY PASS, 0 loops, status COMPLETE | 4 CONFIRMED · 2 LIKELY · 0 ESTIMATED · 0 UNKNOWN | The one fully-keyed card, finally run. Retrieved EUR-Lex directly via the Browser tool (WebFetch fails on EUR-Lex — logged to capability-ledger.md) and found textual proof the key itself couldn't reach: the 2026 Omnibus amends points (a)/(c) of Art. 113(3), never touches point (b) — the GPAI clause. Key had this at ESTIMATED (inferred from silence); this run earned CONFIRMED on direct retrieval, exactly as the key's own text anticipated ("a run that retrieves the consolidated text directly... should score above this key"). Correctly *more* conservative than the key on one point (legacy-model transition date held at LIKELY — genuinely couldn't locate the clause in a huge rendered document, disclosed rather than guessed). First report under the new Part One/Part Two split format. |

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
