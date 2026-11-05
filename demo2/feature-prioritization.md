# Demo 2 — Feature Prioritization

## Prioritization principle

Prioritize the smallest connected assessment loop that proves value across both sides of the marketplace: a manager assigns work, a candidate completes it, and a manager can review evidence. Preserve the Demo 1 remote execution experience while adding the workflow surfaces needed to make it an assessable product.

## Sprint allocation

| Priority | Feature | Journey steps / problem | Decision |
| --- | --- | --- | --- |
| P0 | Assignment creation, candidate access, authentication workflow, and notifications | Manager CUJ 1; removes manual coordination and access ambiguity. | Built |
| P0 | Remote file browsing, Monaco editing, save, Python execution, and SSH terminal | Candidate CUJ 2; preserves the validated Demo 1 foundation. | Built |
| P0 | Assessment submission and completion visibility | Candidate CUJ 2 and manager CUJ 1; makes progress observable. | Built |
| P0 | AI interviewer chat, follow-up handling, and ratings | Candidate CUJs 2–3 and manager CUJ 4; adds structured interview evidence. | Built |
| P0 | System-design Markdown prompt, Excalidraw board, AWS icons, autosave, and submission | Candidate CUJ 3; supports architecture assessment beyond code execution. | Built |
| P0 | Results, saved conversation, status, and rating review | Manager CUJ 4; connects candidate work to a hiring decision. | Built |
| P1 | Terraform tests against Moto and AWS resource/state inspection | Technical validation; tests cloud workflows without live AWS mutation. | Built |
| P2 | Production identity and access management | Security limitation affecting all journeys. | Deferred |
| P2 | Sandboxed execution with quotas and network/process limits | Safety limitation affecting candidate execution. | Deferred |
| P2 | Durable persistence and recovery for assignments, boards, and conversations | Reliability limitation across all journeys. | Deferred |
| P2 | Stronger grading, reviewer controls, and explainability evaluation | AI ratings are signals, not automatic decisions. | Deferred |
| P3 | Observability, deployment hardening, and concurrent-session validation | Needed before production scale. | Deferred |

## Timeline

1. **Foundation:** Retain the remote IDE and execution path from Demo 1.
2. **Workflow build:** Add assignment creation, candidate access, test modes, submission, and completion visibility.
3. **Assessment depth:** Add AI interviewer behavior, system-design whiteboard tooling, autosave, and results review.
4. **Technical validation:** Exercise Terraform workflows with Moto and inspect emulated AWS resources.
5. **Next sprint:** Measure CUJ completion and prioritize security, isolation, persistence, grading quality, and operations based on evidence.
