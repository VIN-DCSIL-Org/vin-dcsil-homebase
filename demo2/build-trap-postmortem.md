# Demo 2 — Build-Trap Postmortem

## What we set out to learn

The sprint tested whether the Demo 1 remote execution proof of concept could support a complete assessment loop rather than only an isolated coding interaction. The value hypothesis required a connected path: a hiring manager assigns work, a candidate accesses and completes it, optional AI and system-design interactions enrich the evidence, and the manager reviews the result.

## What building made possible

Building was necessary because the hypothesis depended on integration behavior, not individual screens. Assignment records, candidate access, remote files, save/run operations, terminal interaction, AI conversation, whiteboard autosave, submission, and results review had to work together. The implementation also made it possible to test two assessment modes and to exercise Terraform workflows against a Moto AWS emulator while inspecting emulated resources and state.

The release demonstrates the connected assessment workflow and supports a **GO for the scoped Demo 2 MVP**. That is a product-scope decision, not a production-readiness claim.

## What remains unproven

The available evidence does not establish secure multi-tenant execution, finalized grading quality, production identity, strong authorization, concurrent-session behavior, or measured CUJ completion thresholds. AI ratings and follow-up questions remain useful signals that require evaluation, explainability, and reviewer controls. Remote execution also requires sandboxing, quotas, resource limits, auditability, and stronger isolation.

## Build-trap assessment

The build was justified because the connected loop could not be evaluated through mockups or a standalone IDE. However, further feature expansion would become a build trap if it occurs before measuring manager and candidate task completion. The next investment should focus on evidence: measured CUJ runs, failure modes, security boundaries, persistence recovery, and concurrent-session testing.

## Decision

Keep the connected MVP and proceed to validation and hardening. Do not treat the current workflow as a production hiring platform. Prioritize authentication and authorization, sandboxed execution, durable persistence, grading quality, observability, and operational testing before broad deployment.
