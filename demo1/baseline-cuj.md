# Demo 1 — Baseline Critical User Journey (CUJ) Audit

## Product Overview

Our product is an AI-assisted technical assessment platform for small businesses. Similar to HackerRank and CoderPad, it helps employers assess programming skills, but focuses on customizable coding tests, useful AI assistance, and a developer-friendly coding environment. The goal is to make technical hiring practical for teams without dedicated assessment infrastructure.

This document defines two related CUJs: the **hiring manager's assessment workflow (primary)** and the **developer candidate's coding workflow (supporting)**. Together, they describe how a test is created, completed, and evaluated. The Demo 1 validation scope should be limited to the parts that are implemented and can be demonstrated end-to-end.

> **Scope note:** These journeys describe the intended user workflows, not completed usability testing. Only features demonstrated in the prototype should be described as validated.

## CUJ 1 — Hiring Manager (Primary)

### Persona

**Role:** Hiring manager or technical lead at a small business.

**Context:** Needs to screen developers but has limited time, recruiting support, and budget. Wants to reuse or customize assessments instead of building and grading every coding exercise manually.

### Value-Driven Goal

> As a hiring manager at a small business, I want to create and customize a coding assessment, send it to a candidate, and review the candidate's results so that I can evaluate technical ability efficiently and make a more informed hiring decision.

**Successful outcome:** The manager can create an assessment with test cases, make it available to a candidate, and view the candidate's submission and results in one workflow.

### Journey Audit

| Step | User action | Context switch / potential friction |
| --- | --- | --- |
| 1 | Open the platform and navigate to assessment creation. | May need to search menus to find where to begin. |
| 2 | Create an assessment and enter its title, description, language, and instructions. | May refer to a separate document for the problem statement. |
| 3 | Add or upload a coding problem and configure example, hidden, or custom test cases as supported. | May switch to an editor or terminal to prepare inputs and expected outputs. |
| 4 | Save the assessment and confirm its settings. | May need to revisit earlier screens to verify requirements and tests. |
| 5 | Make the assessment available to a candidate and share access details. | May leave the product to send a link or invitation. |
| 6 | Return after the candidate submits and open the candidate's results. | May switch between the candidate list and assessment details. |
| 7 | Review test-case results, grade, and submitted code to inform a decision. | May need to manually interpret failures or compare results outside the product. |
| **Total** | **Assessment setup through results review** | **Context switching evaluated across the workflow** |

## CUJ 2 — Developer / Candidate (Supporting)

### Persona

**Role:** Developer completing a coding assessment for a job opportunity.

**Context:** Needs to demonstrate programming skills under time constraints. Wants a familiar editing and execution experience without installing dependencies or configuring a local IDE.

### Value-Driven Goal

> As a developer completing a technical assessment, I want to write, edit, run, and debug code in a browser-based IDE with the tools I need so that I can demonstrate my programming ability without wasting time on environment setup.

**Successful outcome:** The developer opens an assigned assessment, writes code, runs it against supported tests, fixes issues, and successfully submits a solution.

### Journey Audit

| Step | User action | Context switch / potential friction |
| --- | --- | --- |
| 1 | Open the assessment link and read the problem statement. | May need to switch between instructions and the editor. |
| 2 | Select the supported programming language and inspect the starter code. | May need to check syntax or available runtime features elsewhere. |
| 3 | Write and edit a solution in the browser-based IDE. | May prefer a local editor if essential editing features are missing. |
| 4 | Run code and inspect standard output, errors, and test feedback. | May need a separate terminal or tool if execution feedback is unclear. |
| 5 | Debug the solution, make changes, and rerun tests. | May repeatedly navigate between editor, problem, and output panels. |
| 6 | Submit the completed solution and confirm submission status. | May be uncertain whether the final version was saved or submitted. |
| **Total** | **Open assessment through successful submission** | **Context switching evaluated across the workflow** |

## Audit Method

- Walk through each implemented journey using a realistic assessment.
- Identify points where users leave the platform or shift focus between tools and tasks.
- Document any confusing steps or blockers during testing.
- Treat incomplete journeys as not validated rather than assuming success.

### Friction Severity Rubric

| Severity | Definition |
|---|---|
| **None / Great** | User completes the step smoothly without confusion. |
| **Moderate** | User hesitates or encounters unclear UI but recovers independently. |
| **Severe** | User cannot proceed, needs outside help, or experiences substantial frustration. |

## Highlights, Lowlights, and Proposed Fixes

These are **potential friction points**, not confirmed findings from user testing.

| Area | Potential highlight or friction | Proposed improvement |
| --- | --- | --- |
| Hiring manager: test creation | Custom test cases may require repeated manual entry or external preparation. | Provide a clear test-case editor with input/output validation and bulk upload where feasible. |
| Hiring manager: results review | Scores without test-level explanations may be difficult to interpret. | Show passed/failed cases, the submitted solution, and a clear result summary. |
| Developer: editing | A limited editor may force candidates into an external IDE. | Add essential editing support such as syntax highlighting, indentation, and error display. |
| Developer: execution | Unclear run output may make debugging unnecessarily slow. | Place execution output and test feedback beside the editor with clear error messages. |

## Next-Iteration Recommendations

1. **Improve assessment configuration:** Support straightforward creation and editing of custom test cases, with visible validation before an assessment is shared. This targets the manager's setup workflow.
2. **Improve the coding feedback loop:** Keep code, run controls, execution output, and test results accessible in one workspace. This targets the developer's edit-run-debug workflow.
3. **Make grading understandable:** Show which tests passed and failed, alongside the candidate's code, rather than relying on a score alone. This supports faster, more defensible review.

AI-assisted question generation or feedback may be evaluated in later iterations, but should only be claimed as part of the Demo 1 proof of concept if actual working functionality is demonstrated.

## Quantitative Success Metrics

The following are **proposed Demo 1 acceptance thresholds**, not measured results. They can guide validation once the prototype is tested.

| Metric | Proposed target |
| --- | --- |
| Hiring manager completes the implemented creation-to-results workflow | 100% of required steps completed |
| Hiring manager total task time | 10 minutes or less |
| Hiring manager context switches | 2 or fewer |
| Developer completes the implemented coding-and-submission workflow | 100% of required steps completed |
| Developer total task time | 15 minutes or less for a fixed, simple test problem |
| Developer external-tool context switches | 1 or fewer |
| Severe friction points | 0 in either journey |

**Validation decision:** Not yet assessed.

**Technical feasibility check:** A `GO` also requires a working end-to-end primary interaction using real assessment, execution, and grading functionality—not hardcoded responses or simulated results. If only part of a journey is implemented, document the supported steps and limitations explicitly in `proof-of-concept.md`.

## Follow-Up

Once user testing is completed, evaluate the workflow against the proposed targets and record verified findings separately for comparison with future demos.
