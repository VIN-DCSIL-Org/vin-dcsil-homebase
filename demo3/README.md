# Demo 3 — Competitive Parity: Grading, Full-Stack Projects and Decisions

Demo 3 moves CodeCheck from a connected assessment loop (Demo 2) to one a hiring manager can decide from. It closes the largest gaps found against HackerRank and CodeSignal:

- automated public and hidden unit tests;
- per-candidate scores (tests, code /100, communication /100);
- React + Python full-stack tests with a live in-IDE preview;
- five required AI follow-up questions;
- a results view with sorting and Accept/Reject.

## Direct links

- **Live Demo 3 application:** TBD
- **Source code:** [Coding_Vin_DCSIL](https://github.com/VIN-DCSIL-Org/Coding_Vin_DCSIL)
- **Documentation repository:** [vin-dcsil-homebase](https://github.com/VIN-DCSIL-Org/vin-dcsil-homebase)
- **GitHub Project Board:** [VIN-DCSIL Project Board](https://github.com/orgs/VIN-DCSIL-Org/projects/1)

## Artifact index

| Artifact | Purpose |
| --- | --- |
| [feature-prioritization.md](feature-prioritization.md) | Competitive gap analysis against HackerRank and CodeSignal: a 10-capability parity checklist, parity ratios (A5 0.15 → A6 0.75 vs HackerRank), measured CodeCheck performance, critical vs acceptable gaps, and built / killed / deferred decisions. |
| [evolved-topology.jpg](evolved-topology.jpg) | Updated architecture: grading service, AI review pipeline, preview tunnels and the redaction/decision layer. |
| [architectural-rationale.md](architectural-rationale.md) | Decision log: what changed, why, alternatives considered, technical debt and remaining limitations. |
| [pivot-contract.md](pivot-contract.md) | The pre-commitment this sprint ran under (the A5 contract) and its result, plus the pre-sprint contract for the next sprint with competitor-relative kill metrics. |
| [build-trap-postmortem.md](build-trap-postmortem.md) | Which features delivered the hypothesized value, where building was unnecessary (the Tkinter/VNC desktop), and what remains unproven. |

The optional `competitive-review-cuj.md` is not included: the team did not run timed CUJs on competitor products this sprint. The next [pivot contract](pivot-contract.md) requires that measurement.

## Validation decision

**GO for the scoped Demo 3 release; continue under the next pivot contract.**

- **Parity:** against HackerRank's documented capabilities, it rose from 0.15 to 0.75.
- **Grading:** a 20-test run takes a median of 249 ms.
- **AI focus:** the AI now reads only the candidate's code (29–63× less text).
- **Full-stack apps:** they start in about 1 s and run side by side on random ports.

All evidence comes from team-run journeys. It does not establish performance relative to competitors, AI scoring accuracy, or production readiness.

## Known limitations

- **Execution isolation:** there is no per-candidate sandbox.
- **Authentication:** still lightweight.
- **Integrity:** there is no plagiarism or paste-tracking signal (a critical gap).
- **Test storage:** the hidden tests are stored in the code repository.
- **Language:** Python is the only test language.
- **Persistence:** data is kept in JSON files on the backend.
