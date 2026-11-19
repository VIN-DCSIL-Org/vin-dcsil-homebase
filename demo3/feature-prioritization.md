# Demo 3 — Feature Prioritization and Competitive Gap Analysis

**Sprint:** 2026-11-05 (A5 release) to 2026-11-19.
**Competitors:** HackerRank and CodeSignal, the two platforms a small-business hiring manager is most likely to compare against CodeCheck for take-home technical assessments.

## Method

- **Capability checklist:** 10 capabilities along the CUJs (assign → complete → review → decide). A competitor gets credit only where its **public documentation** describes the capability (sources below, accessed 2026-11-19). "Not found" means we did not find it documented, not that it is absent.
- **Scoring:** 1 = supported, ½ = partial, 0 = no or not found. **Parity ratio** = CodeCheck score ÷ competitor score.
- **Performance:** CodeCheck timings were measured on 2026-11-19 against the team's EC2 instance (ca-central-1) from the development backend; run counts are given. We did **not** run timed CUJs on HackerRank or CodeSignal (no accounts), so competitor speed is not compared. That measurement is part of the [next pivot contract](pivot-contract.md).

## Feature parity

| # | Capability (CUJ step) | HackerRank | CodeSignal | CodeCheck A5 | CodeCheck A6 |
| --- | --- | --- | --- | --- | --- |
| 1 | Automated unit tests run on submission (review) | ✅ [1] | ✅ [4] | ❌ | ✅ 20 per test: 10 public + 10 hidden |
| 2 | Hidden tests: candidate sees pass/fail only (complete) | ✅ [2] | ✅ [4] | ❌ | ✅ never written to the EC2 disk |
| 3 | Automatic score per candidate (review) | ✅ [1] | ✅ [4] | ½ AI ratings per answer only | ✅ tests %, code /100, communication /100, overall |
| 4 | AI follow-up questions on the submitted work (complete) | ✅ [5] | ✅ [6] | ✅ 3 questions | ✅ 5 (3 on the code, 2 on logic), required to complete the submission |
| 5 | Front-end / full-stack project questions (complete) | ✅ [3] | ✅ [7] | ❌ | ✅ React + Python apps with a live preview in the IDE |
| 6 | Results list with filters or sorting (review) | ✅ [8] | ✅ [10] | ❌ unsorted list | ✅ 7 sort orders, decision filter, search |
| 7 | Record a pass / reject decision (decide) | ✅ [8] | Not found | ❌ | ✅ Accept, Reject, Undo |
| 8 | Copy-paste integrity signal (complete) | ✅ [9] | ✅ [10] | ❌ | ½ copying blocked with a warning; pastes not tracked |
| 9 | Plagiarism / similarity detection (review) | ✅ [9] | ✅ [10] | ❌ | ❌ |
| 10 | Proctoring (complete) | ✅ [9] | ✅ [11] | ❌ | ❌ |
| | **Score (of 10)** | **10** | **9** | **1.5** | **7.5** |

### Parity ratios

| | vs HackerRank | vs CodeSignal |
| --- | --- | --- |
| CodeCheck A5 | 0.15 | 0.17 |
| CodeCheck A6 | **0.75** | **0.83** |

A6 is a **5×** improvement in parity against both competitors. Two capabilities were not found in the competitor documentation we reviewed: an AI **code-structure score out of 100** with coding-standards notes, and an AI **communication score out of 100** with strengths and points to work on. We treat them as possible differentiators, not proven ones.

## Measured performance (CodeCheck)

| Metric | A5 | A6 | Measurement |
| --- | --- | --- | --- |
| Automated tests per assessment | 0 | 20 | Catalog of 4 tests (80 unit tests in all). |
| Grading round trip, 20 tests | n/a | median **249 ms** (203–253, n = 5) | Backend → EC2 → JSON report; 7 ms of it inside the Python runner. |
| Code sent to the AI per submission | 80–89K characters | **1.4–2.8K** characters | 4 catalog tests. A5 sent the whole folder (including `package-lock.json`); A6 sends only the candidate's code: **29–63× less**. |
| 5 AI follow-up questions | n/a (3 questions) | 3.0–4.9 s (n = 2) | One model call. |
| AI code review | n/a | 3.4 s (n = 1) | One model call. |
| Full-stack app start → ready | n/a | **≈ 0.96 s** (957–966 ms, n = 3) | `sh start.sh` until Vite prints its URL. |
| Preview page through the SSH tunnel | n/a | median **131 ms** (30–441, n = 6) | HTML of the candidate's React app. |
| App API call through tunnel → Vite → Python | n/a | **≈ 80 ms** (77–93, n = 5) | `GET /api/stats`. |
| Full-stack apps running at once on one EC2 | n/a | **≥ 2 verified** | Random free ports per app. The mid-sprint build allowed 1 (fixed ports). |

## Gap classification

**Critical: close before a pilot with a real company.**

- **Plagiarism and paste tracking (#8, #9).** Both competitors document it. CodeSignal reports that cheating and fraud attempts on proctored assessments rose from 16% to 35% in a year [12], so scores without integrity signals are hard to trust.
- **Execution isolation and authentication** (carried from A5): candidates share one EC2 user with no per-candidate sandbox.
- **Hidden-test storage:** the hidden tests live in the code repository, so anyone with repository access can read them.

**Acceptable for the small-business MVP.**

- **Proctoring (#10):** high friction and a privacy cost for small teams; the required AI follow-up questions check understanding instead.
- **Decision workflow depth (#7):** HackerRank has ATS states; Accept/Reject is enough for teams without an ATS.
- **Library breadth:** a Python catalog of 4 tests is enough to validate the journeys; breadth is a scale problem.
- **Competitor speed:** not measured yet; required by the next contract.

## Strategic feature decisions

| Decision | Feature | Gap | Justification |
| --- | --- | --- | --- |
| Built | Public and hidden unit tests, piped to the EC2 instead of copied there | #1, #2 | The largest parity gap; both competitors' scoring is built on it. |
| Built | Results page: scores, sorting, filters, accept/reject | #3, #6, #7 | A5's results (raw ratings and full transcripts) did not support a decision. |
| Built | React + Python full-stack tests with a live in-IDE preview | #5 | Both competitors offer web front-end questions. |
| Built | 5 required AI questions (3 code + 2 logic); AI sees only the candidate's code | #4 | Before the fix, the questions targeted code we provided, not the candidate's. |
| Built | AI code score and communication score, each /100 | Differentiator | Not found in the competitor documentation reviewed. |
| Built (partial) | Copy blocking with a warning | #8 | Cheap deterrent; detection is deferred. |
| Killed | Tkinter desktop apps streamed over VNC | — | Built mid-sprint, reported laggy, and needed ~300 MB of X/VNC packages on the EC2. Neither competitor's front-end questions are desktop GUIs. Replaced by the web preview. |
| Killed | AWS console panel | — | Not on any CUJ. |
| Reprioritized | Fixed app ports → random free ports | #5 | Fixed ports let only one candidate run an app at a time. |
| Deferred | Plagiarism detection, paste tracking | #8, #9 | Critical; next sprint. |
| Deferred | Proctoring, more languages, ATS integrations | #10 | Acceptable gaps for now. |

## Sources (accessed 2026-11-19)

1. HackerRank — [Coding Questions (scoring)](https://support.hackerrank.com/hc/en-us/articles/115006676188-Scoring-a-Coding-Question)
2. HackerRank — [Hidden Test Cases (candidate support)](https://candidatesupport.hackerrank.com/articles/6052652546-hidden-test-cases)
3. HackerRank — [Hidden Test Cases for Front-End, Back-End and Full Stack Questions](https://support.hackerrank.com/articles/1626384486-hidden-test-cases-for-front-end,-back-end-and-full-stack-questions)
4. CodeSignal — [General Coding Assessment structure](https://support.codesignal.com/hc/en-us/articles/360040370853-What-should-I-expect-when-I-take-the-General-Coding-Assessment-GCA-and-how-is-it-structured) and [Quick Start Guide: Assessments](https://support.codesignal.com/hc/en-us/articles/22112130416535-Quick-Start-Guide-Pre-Screen)
5. HackerRank — [Introduction to Chakra](https://support.hackerrank.com/articles/6908366644-introduction-to-chakra) and [Interview with Chakra](https://candidatesupport.hackerrank.com/articles/4278399240-interview-with-chakra)
6. CodeSignal — [AI Interviewer](https://codesignal.com/ai-interviewer/)
7. CodeSignal — [Quick Start Guide: Interview](https://support.codesignal.com/hc/en-us/articles/22112352841879-Quick-Start-Guide-Interview)
8. HackerRank — [Filtering and Sorting Candidate Test Reports](https://support.hackerrank.com/articles/1829746072-filtering-and-sorting-candidate-test-reports) and [View Candidate Test Summary Report](https://support.hackerrank.com/articles/8111267829-viewing-a-candidate's-test-summary-report)
9. HackerRank — [Plagiarism Best Practices Guide](https://support.hackerrank.com/articles/4291690360-plagiarism-best-practices-guide), [How Plagiarism Detection Works](https://www.hackerrank.com/blog/how-plagiarism-detection-works-at-hackerrank/) and [Proctor Mode vs. Secure Mode](https://www.hackerrank.com/writing/proctor-mode-vs-secure-mode-hackerrank-detects-chatgpt-ai-cheats-2025)
10. CodeSignal — [Using Suspicion Score](https://support.codesignal.com/hc/en-us/articles/16957476906135-Using-Suspicion-Score) and [Viewing the reason for non-verified results](https://support.codesignal.com/hc/en-us/articles/4409230511767-Viewing-the-reason-for-a-test-taker-s-non-verified-results)
11. CodeSignal — [What is proctoring and how does it work?](https://support.codesignal.com/hc/en-us/articles/360039872174-What-is-proctoring-and-how-does-it-work)
12. CodeSignal — [Press release: assessment fraud more than doubled in 2025](https://codesignal.com/newsroom/press-releases/codesignal-detection-systems-identify-and-stop-record-high-cheating-attempts-as-assessment-fraud-more-than-doubled-in-2025/)
