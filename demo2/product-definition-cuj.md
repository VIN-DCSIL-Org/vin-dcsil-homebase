# Demo 2 — Product Definition and Critical User Journeys

## Product definition

Demo 2 turns the Demo 1 remote coding proof of concept into an assessment platform MVP. Hiring managers can create or select coding and system-design tests, assign them to candidates, monitor completion, and review assessment records. Candidates can complete coding work in the remote browser IDE, use an AI interviewer, or create a system-design diagram and answer follow-up questions.

## Personas and value

| Persona | Value-driven goal |
| --- | --- |
| Hiring manager | Create or select a test, assign it to a candidate, and track status without manually coordinating files and access. |
| Coding candidate | Open an assigned test, edit and run code remotely, use the AI interviewer, and submit work in one workflow. |
| System-design candidate | Express architecture visually, explain design decisions, autosave work, and submit a reviewable board. |
| Reviewing hiring manager | Inspect status, AI ratings, conversation history, and candidate work to make a more informed decision. |

## CUJ 1 — Create and assign an assessment

1. Sign in as a hiring manager.
2. Choose a coding or system-design test.
3. Enter candidate details.
4. Select an EC2 folder, upload a test folder, or save system-design instructions.
5. Assign the test.
6. Monitor assignment completion.

**Value:** A small-business hiring manager can coordinate an assessment without separate file sharing, access setup, and status tracking.

## CUJ 2 — Complete a coding assessment

1. Sign in as a candidate and open **My Tests**.
2. Read the instructions.
3. Browse and edit assigned remote files in Monaco.
4. Save changes and run Python on the remote Linux or EC2 environment.
5. Use the interactive SSH terminal and AI interviewer as appropriate.
6. Submit the assessment.

**Value:** A candidate demonstrates programming ability without configuring a local development environment.

## CUJ 3 — Complete a system-design assessment

1. Open a system-design assignment.
2. Read the Markdown prompt.
3. Place AWS service icons on an Excalidraw whiteboard.
4. Explain design decisions through the AI follow-up conversation.
5. Autosave and submit the board.

**Value:** Architecture reasoning and visual design are captured alongside the assessment conversation.

## CUJ 4 — Review results

1. Open Results as a hiring manager.
2. View completed or in-progress questions.
3. Inspect AI chat, ratings, and thinking-answer results.
4. Expand the saved conversation.
5. Review the candidate's assessment record.

**Value:** Reviewers receive a connected evidence trail instead of relying on disconnected notes or manual coordination.

## Feature-to-value mapping

| Feature | User problem | Value |
| --- | --- | --- |
| Assignment creation and candidate access | Manual coordination of tests, files, and access | Repeatable hiring workflow |
| Remote file browser, Monaco editor, save, and Python execution | Candidates must configure local tools | Low-friction coding assessment |
| Interactive SSH terminal | Candidates need realistic debugging and shell access | More complete remote development experience |
| AI interviewer and ratings | Interviews lack structured follow-up evidence | Consistent supplementary assessment signal |
| Excalidraw and AWS icon palette | System-design work is difficult to capture as text alone | Reviewable architecture reasoning |
| Autosave and read-only review | Submitted work can be lost or altered | Durable, inspectable candidate artifact |
| Results and conversation review | Managers need context behind assessment outcomes | Faster and more informed review |
| Terraform tests with Moto emulator and AWS console | Cloud behavior is hard to test safely | Visible, repeatable emulated AWS validation |
