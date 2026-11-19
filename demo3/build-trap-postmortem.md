# Demo 3 — Build-Trap Postmortem

## What we set out to learn

Would closing the largest documented gaps against HackerRank and CodeSignal make CodeCheck's assessment loop one a hiring manager can **decide** from? Those gaps were hidden tests, per-candidate scores, full-stack questions and a decision-oriented review. The hypothesized value: faster, evidence-based decisions for the hiring manager, and clear feedback for the candidate without exposing the hidden tests.

## Features that delivered the hypothesized value

| Feature | Evidence | Was building necessary? |
| --- | --- | --- |
| Hidden + public tests, piped over SSH | 20 tests in a 249 ms median round trip. The starter scores 0/20 and a reference solution 20/20 on the EC2's Python 3.9. Hidden tests never reach the EC2 disk. | **Yes.** Latency, timeouts and secrecy needed real runs. |
| Results page: scores, sorting, accept/reject | HR sorts by overall, tests, code, communication, date or name, and decides from one view. | **Partly.** The layout could have been a mockup first. |
| Full-stack React + Python preview | Ready in ≈ 0.96 s; pages arrive through the tunnel in a 131 ms median; two apps ran at once. | **Yes.** URL, live-reload and port behaviour only show up in a browser. |
| 5 required AI questions, candidate-only context | The AI used to read the provided app too (80–89K characters) and asked about code the candidate never wrote. It now reads 1.4–2.8K characters of their code. | **Yes.** The defect only appeared in real generated questions. |

## Where we fell into the build trap

- **Tkinter desktop over VNC.** We built per-workspace X servers, a VNC bridge and a viewer, installed ~300 MB of packages, and then removed it all. It was laggy, and both competitors assess web front ends. Ten minutes on competitor question types would have answered this. **Building was not necessary.**
- **The first results page.** A5's page listed raw ratings and full transcripts. In review it was rejected because it did not support a decision: the reviewer asked for score bars, a summary of strengths and weaknesses, and grades out of 100. A mockup would have found this.
- **Fixed ports.** The collision surfaced only when a second session started; a one-line design check ("two candidates?") would have caught it.
- **Voice interviewer.** Built, but there is no evidence that candidates want it.

## What remains unproven

All evidence comes from **team-run** journeys. No external hiring manager or candidate has used A6, and no journey was timed on HackerRank or CodeSignal. The 0.75 parity ratio measures feature coverage, not performance. AI scores have not been compared with human reviewers. The [pivot contract](pivot-contract.md) turns each of these into a falsifiable measure.

## Decision

Keep the grading, review and preview work: it closed measurable gaps, raising parity from 0.15 to 0.75. Stop adding features until the next sprint has collected:

- time-to-decision against a competitor;
- AI–human score agreement;
- integrity signals (plagiarism and paste tracking), the critical gap.

New surfaces that are not on a CUJ get a mockup before any code.
