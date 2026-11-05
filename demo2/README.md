# Demo 2 — Assessment Platform MVP

Demo 2 expands the Demo 1 remote coding workspace into an assessment platform MVP connecting hiring-manager workflows, candidate assignments, AI-assisted interviews, system-design assessments, and results review.

## Direct links

- **Source code:** [Coding_Vin_DCSIL](https://github.com/VIN-DCSIL-Org/Coding_Vin_DCSIL)
- **Documentation repository:** [vin-dcsil-homebase](https://github.com/VIN-DCSIL-Org/vin-dcsil-homebase)
- **Live Demo 2 application:** TBD
- **GitHub Project Board:** [VIN-DCSIL Project Board](https://github.com/orgs/VIN-DCSIL-Org/projects/1)

## Artifact index

| Artifact | Purpose |
| --- | --- |
| [product-definition-cuj.md](product-definition-cuj.md) | Product definition, personas, feature-to-value mapping, and end-to-end critical user journeys. |
| [feature-prioritization.md](feature-prioritization.md) | Sprint priorities connecting delivered and deferred work to user journeys. |
| [evolved-topology.jpg](evolved-topology.jpg) | Updated architecture showing browser clients, Node.js APIs/WebSockets, remote execution, AI, system design, and AWS emulation. |
| [architectural-rationale.md](architectural-rationale.md) | Design decision log for the assessment-platform evolution. |
| [pivot-contract.md](pivot-contract.md) | Pre-sprint hypothesis, kill metric, trigger date, and fallback options. |
| [build-trap-postmortem.md](build-trap-postmortem.md) | Retrospective on what the implementation validated and what remains unproven. |

## Validation decision

**GO for the scoped Demo 2 MVP.** The release demonstrates a connected assessment workflow from assignment through candidate work and results review. It does not establish production readiness, secure multi-tenant execution, or finalized grading quality.

## Known limitations

Production-grade authentication and authorization, tenant isolation, sandboxed execution limits, durable recovery, observability, concurrent-session testing, and measured CUJ results remain next-step work.
