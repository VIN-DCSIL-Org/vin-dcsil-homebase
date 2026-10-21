# Demo 1 — Proof of Concept

## Overview

Our product is a technical assessment platform aimed at making coding interviews more flexible for smaller businesses. Our longer-term vision includes customizable tests, AI-assisted features, and hiring-manager tools. Demo 1 focused on the **developer's coding environment**.

The main technical question we wanted to answer was: **Can we build a browser-based IDE that lets a developer work with real files and execute real code on an Amazon EC2 instance, without leaving our application?**

This was our main technical risk. A visual editor alone would not be enough: developers must be able to save real files, run programs, and see results.

## Scope and Primary User Interaction

The primary user is a developer completing an assessment who needs to edit, save, and run code without local setup.

For Demo 1, a successful end-to-end interaction means the developer can:

1. Open the IDE within our application.
2. Browse and access files in the EC2-hosted file system.
3. Open and edit file contents directly through our UI.
4. Save their changes to the corresponding files on EC2.
5. Run Python code on EC2 from within the IDE.
6. View execution output through a terminal-like interface in the application.

These operations are real, not simulated.

## Technical Approach

We wrapped actions on an EC2 instance in an IDE interface, connecting file navigation, editing, saving, and execution to the remote machine.

The central challenge was connecting browser interactions to EC2 operations. An edit must update the actual remote file, and **Run** must execute the program and return its output. Our implementation connects those steps while keeping the workflow inside our UI.

This establishes a real execution environment for future assessments.

## Known Constraints and Accepted Limitations

This demo has a deliberately limited scope:

- **Python is the demonstrated language.** Support for additional languages has not been established by this demo.
- **Hiring-manager workflows are outside this validation.** Creating assessments, assigning candidates, and grading remain separate product goals.
- **The terminal is terminal-like.** Code execution and output are demonstrated, but full terminal capabilities are not established.
- **Production readiness is not validated.** Multi-user isolation, execution security, concurrency, scaling, and reliability require further testing.

## Validation Result: Go

**We consider the Demo 1 proof of concept passed for its defined scope.** A developer can use our IDE to work with files on EC2, save changes, execute Python code remotely, and see the output in the application. This confirms the central technical assumption behind our developer experience: our UI can interact with a real remote development environment end to end.

This does not validate the entire platform. Future demos can build on this foundation with assessment management, evaluation, and safer execution controls.
