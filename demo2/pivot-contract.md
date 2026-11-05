# Demo 2 — Pre-Sprint Pivot Contract

## Hypothesis

If the Demo 1 remote coding workspace is connected to assignment management, candidate access, AI-assisted interviews, system-design work, and results review, then a small business can run a complete assessment loop without coordinating separate tools for files, execution, interviews, diagrams, and review.

The sprint hypothesis is considered directionally supported when a representative manager and candidate can complete the four documented journeys end to end, with **at least 80% of required journey steps completed**, **no critical blocker**, and **no more than two external-tool context switches per journey**.

## Kill metric

Kill or materially narrow the product direction if fewer than **60% of required journey steps** can be completed in observed runs, or if **two or more critical blockers** prevent assignment, candidate completion, or results review. A critical blocker includes inability to access assigned work, save or run candidate work, submit an assessment, or retrieve review evidence.

## Trigger date

**Decision point: 2026-11-20.** Review observed manager and candidate runs, failure logs, and technical validation evidence at this date. The current release is a GO for the scoped MVP; this date is the next investment decision, not a claim of production readiness.

## Evidence to collect

- Manager assignment completion rate and elapsed time.
- Candidate coding and system-design completion rate.
- Save, run, autosave, and submission failures.
- AI conversation and rating review usability.
- Number of context switches and outside assistance requests.
- Concurrent-session, authorization, and execution-isolation failures.

## Fallback options

1. **Narrow the MVP:** Keep coding assessments and defer system-design or AI features if they create disproportionate friction.
2. **Harden before expanding:** Prioritize identity, tenant isolation, sandboxing, persistence, and observability if workflow value is clear but operational risk is high.
3. **Separate assessment modes:** Treat coding and system-design assessments as independent products if their workflows need different controls.
4. **Return to the Demo 1 boundary:** Preserve the remote IDE as a developer tool if the complete hiring loop does not achieve the completion threshold.
