# Demo 1 — Surface Product & Proof of Concept

## Project Overview

We are building a technical assessment platform for small businesses, inspired by platforms such as HackerRank and CoderPad. Our broader goal is to support customizable coding assessments, AI-assisted workflows, and a more accessible hiring process for smaller teams.

For **Demo 1**, we focused on the developer experience: a browser-based IDE connected to a real Amazon EC2 environment. Developers can browse files, edit and save them through our interface, execute Python code on EC2, and view the output in a terminal-like panel. This validates our central technical proof of concept without relying on simulated execution.

## Application and Source Code

- **Source code repository:** [Coding_Vin_DCSIL](https://github.com/VIN-DCSIL-Org/Coding_Vin_DCSIL)
- **Live application:** A deployment URL has not been provided for this release README. Add the public application link when available.

## Release Artifacts

The following index includes all expected Demo 1 documentation, including artifacts that are not yet completed.

| Artifact | Description | Status |
| --- | --- | --- |
| [`demo1/baseline-cuj.md`](../demo1/baseline-cuj.md) | Defines the hiring manager and developer personas, their value-driven goals, journey steps, and potential context switches and friction points. | Created |
| [`demo1/system-topology.jpg`](../demo1/system-topology.jpg) | Planned architecture diagram showing the UI, application logic/API, EC2 execution environment, and relevant data or file boundaries. | Not yet added |
| [`demo1/proof-of-concept.md`](../demo1/proof-of-concept.md) | Describes the implemented IDE-to-EC2 workflow, criteria for success, technical constraints, and Demo 1 validation outcome. | Created |
| [`demo1/reflections.md`](../demo1/reflections.md) | Optional reflection on validation evidence, limitations, lessons learned, and next steps. | Optional; not yet added |
| [`rdemo1/README.md`](README.md) | This release manifest and index of documentation and application links. | Created |

## Primary Interaction and Validation

**Primary persona:** A developer completing a technical coding assessment.

**Value-driven goal:** Edit, save, and execute code within a browser-based development environment so the developer can demonstrate technical ability without configuring a local environment.

**Validated interaction:** Open the IDE → browse remote files → edit code → save changes on EC2 → execute Python → view output in the application.

**Proof-of-concept decision: GO for the defined Demo 1 scope.** We demonstrated that our application can interact with real files and execute code on EC2. This does not mean that the full assessment platform has been validated.

## Current Scope and Next Steps

The current demonstration focuses on Python execution and file operations within the developer IDE. Hiring-manager assessment creation, automated grading, AI-assisted functionality, complete terminal capabilities, and production-grade multi-user security and scaling remain outside this proof of concept.

The next iteration will build on the EC2 integration while addressing these features and testing usability and friction with actual users.
