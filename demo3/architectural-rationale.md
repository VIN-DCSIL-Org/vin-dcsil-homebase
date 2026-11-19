# Demo 3 — Architectural Rationale

## What changed

A5 connected the remote IDE to an assessment loop. A6 adds what competitors use to make that loop **decidable**: automated grading, full-stack project questions, and a review view built around a decision. Four components are new (see [evolved-topology.jpg](evolved-topology.jpg)):

1. **Grading service.** Each catalog test has public and hidden unit tests. The backend pipes a runner script plus the tests into `python3 -` over the existing SSH connection, so **tests are never written to the EC2 disk**. The runner allows 3 s per test and 30 s in total; 20 tests take a median of 249 ms round trip.
2. **AI review pipeline.** On submit, the model scores code structure (/100) and writes 5 follow-up questions (3 on the code, 2 on logic). It then scores communication (/100) after the last answer. It reads **only the candidate's own code**, not the provided app: 29–63× less text.
3. **Preview tunnels.** A candidate's React app and Python API start on **random free ports**, on 127.0.0.1 inside the EC2. The IDE reads the port from the terminal. The backend then opens a local port and pipes each connection through an SSH `direct-tcpip` channel. The Preview tab is an iframe on that port, and no EC2 port is exposed.
4. **Redaction and decisions.** Candidates never receive grading data or HR's decision, and hidden tests are reported as pass/fail only. HR records Accept/Reject on the assignment.

## Why

The gap analysis ([feature-prioritization.md](feature-prioritization.md)) found that A5 covered 1.5 of the 10 capabilities HackerRank documents. The largest gaps were automated hidden tests, per-candidate scores and project questions, and the review view did not lead to a decision.

## Alternatives considered

- **Copying tests into each workspace:** hidden tests would be readable from the candidate's terminal.
- **Exposing app ports or adding a reverse proxy on the EC2:** this opens the instance and needs per-candidate routing. The SSH connection already exists.
- **A path-based proxy (`/preview/<port>/`):** this breaks the app's absolute URLs. A port per tunnel keeps the app unmodified.
- **Desktop GUI apps over VNC (Tkinter):** built, then removed. It was laggy and needed an X server per workspace plus ~300 MB of packages, while competitors assess web front ends.
- **Fixed ports 3000/8000:** only one candidate could run an app at a time.

## Technical debt

**Resolved:**

- AI context bloat;
- port collisions;
- the VNC stack;
- the unused AWS console UI;
- a Run button that hung on servers.

**Introduced:**

- Hidden tests are stored in the code repository.
- There are up to 40 local tunnel ports per backend, which suits a VM but not a single-port host.
- Grading results live in a JSON file.
- The A5 diagram showed Cloud Firestore, but the implementation persists to JSON files. This release states that instead of hiding it.

## Limitations remaining

- No per-candidate sandbox or CPU, memory and network quotas.
- Lightweight authentication.
- No plagiarism or paste-tracking signal.
- Python-only tests.
- AI scores not checked against human reviewers.
- Concurrency verified for two apps only.

These are the next sprint's priorities and the measures in the [pivot contract](pivot-contract.md).
