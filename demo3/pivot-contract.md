# Demo 3 — Pivot Contract

## 1. The pre-commitment this sprint ran under

The team did **not** write a separate, competitor-relative contract before the A6 work began on 2026-11-05. The contract in force was the A5 pre-sprint contract, [`demo2/pivot-contract.md`](../demo2/pivot-contract.md), committed in `51c4602` (2026-11-05) before any A6 code, with a decision date of **2026-11-20**. We record that gap instead of writing a contract after the fact and presenting it as pre-sprint.

### Result against the A5 contract (evidence collected 2026-11-19)

| Clause | Threshold | Evidence | Result |
| --- | --- | --- | --- |
| Hypothesis | ≥ 80% of required journey steps completed, no critical blocker, ≤ 2 external-tool context switches per journey | Team-run, browser-driven end-to-end runs of the four CUJs: HR assigns → candidate codes, runs tests and previews the app → submits → answers 5 AI questions → HR reviews, sorts and accepts/rejects. All steps completed. The candidate needs no external tool (tests, terminal, app preview and AI interviewer are in the IDE). | **Met in team runs.** Not yet observed with external candidates or hiring managers. |
| Kill metric | < 60% of steps, or ≥ 2 critical blockers | Two critical blockers were found mid-sprint and fixed: (1) **Run** waited for the program to exit, so servers showed "Running…" forever; (2) every candidate's app used fixed ports 3000/8000, so only one candidate could run an app at a time. None remain in the release build. | **Not triggered.** |
| Evidence still missing | Manager timings, candidate completion rates with real users, concurrency beyond two sessions | Not collected this sprint. | **Open**: moved into the contract below. |

**Decision: continue, not kill.** This sprint narrowed the product towards competitive parity on grading and review (see [feature-prioritization.md](feature-prioritization.md)).

## 2. Pre-sprint contract for the next sprint (A7)

*Written 2026-11-19, before any A7 work, and committed with this release so the timestamp is verifiable.*

### Hypothesis (competitive positioning)

For small businesses without a recruiting-operations team, CodeCheck can reach **grading and review parity with HackerRank** on the 10-capability checklist in [feature-prioritization.md](feature-prioritization.md), and **beat it on time-to-decision**: a hiring manager reaches an accept/reject decision on a submitted full-stack test faster, because CodeCheck shows tests, a code score and a communication score in one view.

### Measures

| Measure | Now (A6) | How it is measured |
| --- | --- | --- |
| Parity ratio vs HackerRank | 0.75 | Checklist in feature-prioritization.md, re-scored at the trigger date. |
| Time-to-decision | Not measured | Median minutes from opening a submission to accept/reject, the same submissions reviewed in CodeCheck and in a HackerRank trial or demo account (CodeSignal if HackerRank access is unavailable; recorded as such), n ≥ 5 reviews per product. |
| AI–human score agreement | Not measured | Share of AI code and communication scores within ±15 points of a human reviewer's score, n ≥ 10 submissions. |

### Kill metric (falsifiable)

Stop competing head-on with HackerRank if, at the trigger date, **any** of these holds:

1. CodeCheck's median time-to-decision is **≥ 1.5×** the competitor's for the same submissions;
2. the parity ratio vs HackerRank is **< 0.85** (the plagiarism and paste-tracking gaps were not closed);
3. AI–human agreement is **< 70%**.

### Trigger date

**2026-12-03.** The decision uses only the evidence above, as recorded in the A7 release.

### Fallback options

1. **Add-on, not platform:** offer CodeCheck's AI follow-up interview and review as a layer on top of tests run elsewhere.
2. **Full-stack niche:** focus on React + Python project assessments for small businesses, where CodeCheck's setup-free live preview is the selling point.
3. **Integrity first:** if AI agreement fails, keep AI scores advisory only and ship plagiarism and paste signals before any new feature.
4. **Return to the Demo 1 boundary:** keep the remote IDE as an internal developer tool (the A5 fallback).
