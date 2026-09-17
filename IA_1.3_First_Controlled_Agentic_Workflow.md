# Assignment 1.3 — First Controlled Agentic Workflow: Room Booking

## Assignment Type

Individual, formative coding exercise. **10-point rubric for feedback; this is not a separate percentage of the course grade.**

Allow approximately **75–100 minutes after completing Assignment 2**. Begin in class and finish at home if needed. You need a working GitHub account, VS Code, Git, `uv`, Python 3.12 through `uv`, and Copilot Free or another active Copilot plan.

## Purpose and task

The [ICCS471 room booking starter repository](https://github.com/MUIC-ICCS-471-Agentic-AI/iccs471-booking-starter) already creates and lists bookings. Four existing tests pass, but the service incorrectly accepts overlapping bookings in the same room.

Change `create_booking` so that a proposed booking that overlaps an existing booking **in the same room** raises `ValueError`. A rejected booking must not be stored. Keep the existing behavior that already works.

| Existing booking | Proposed booking | Expected result |
| --- | --- | --- |
| Room A, 09:00–10:00 | Room A, 09:30–10:30 | Reject |
| Room A, 09:00–10:00 | Room A, 10:00–11:00 | Accept: boundary only |
| Room A, 09:00–10:00 | Room B, 09:30–10:30 | Accept: different room |

Times are integer minutes after midnight: `540` means 09:00. Booking intervals include their start but exclude their end: `[start, end)`. The rule must also cover a booking entirely contained within another booking. Room names are exact strings.

**Permitted edits:** `booking_app/booking.py` and `tests/test_booking.py` only. Preserve the current validation and baseline tests. Do not change `demo.py`, configuration, or other starter files; do not add dates, persistence, a web interface, or room-name normalization.

**Learning goals:** Understand an unfamiliar repository; review an AI-generated plan before allowing edits; supervise a bounded change; inspect the resulting files; test and directly exercise the requested behavior.

## Work sequence

### 1. Clone the starter and establish the baseline

In **PowerShell**, run each line separately:

```powershell
cd $env:USERPROFILE
git clone https://github.com/MUIC-ICCS-471-Agentic-AI/iccs471-booking-starter.git booking-lab
cd booking-lab
git status
uv sync
uv run python --version
uv run python -m unittest discover -s tests -v
uv run python demo.py
```

If `booking-lab` already exists, choose a different unused local folder name in the `git clone` and `cd` lines. Open the cloned folder in VS Code.

**Expected baseline:** clean Git status, Python `3.12.x`, **four passing tests**, and demo output including `Overlapping booking in room A: accepted (BUG)` and `Stored bookings: 4`. The tests pass because they do not yet cover the missing rule. Resolve a baseline or setup problem before editing.

Read `README.md`, `booking_app/booking.py`, `tests/test_booking.py`, and `demo.py` yourself.

### 2. Ask: understand the repository

In VS Code Copilot **Ask** mode, request a short explanation of where bookings are created, validated, and tested. Tell Copilot **not to edit files or run commands**. Compare at least two claims in its answer with the actual files.

> Briefly explain where bookings are created, validated, and tested. Name the relevant files and functions. Do not edit files or run commands.

Ask additional questions as you see fit.

### 3. Plan: decide what should change

Switch to **Plan** mode. Ask for a plan to implement the required rule and tests within the two permitted files, **without making changes yet**. For example:

> Plan a change so every same-room booking overlap raises ValueError and is not stored. Preserve existing validation; allow adjacent bookings and overlapping times in different rooms. Edit only booking_app/booking.py and tests/test_booking.py. Include test cases and verification commands. Do not implement yet.

Review the proposed plan. Check for same-room overlap (including containment), unchanged storage after rejection, adjacency, different rooms, preservation of existing validation, and useful tests. If the plan includes unnecessary changes, give specific feedback. For example:

> Remove the proposed change to `demo.py`. Keep implementation and tests in the two permitted files. Retain the overlap, adjacency, and different-room test cases.

**Do not select Start Implementation until you accept the plan.**

### 4. Agent: implement under supervision

Select the **Start Implementation** button from the accepted Plan response and choose the **local Agent**. Review any proposed terminal commands and inspect its file changes. Correct or stop work that exceeds the two permitted files. If the handoff button is unavailable, switch to local Agent yourself and provide the accepted plan.

Copilot Free is sufficient for this small task; keep requests focused. If Agent access or its allowance blocks you, retain the exact message and contact the instructor. **Do not buy a subscription.**

Keep approvals **manual** during this exercise. Do not enable automatic approval; inspect proposed commands before allowing them, and review the resulting file edits.

### 5. Inspect, verify, and validate

Run the following commands **yourself** in the VS Code PowerShell terminal:

```powershell
git status
git diff
uv run python -m unittest discover -s tests -v
uv run python demo.py
```

Read the actual changes in both permitted files. New tests must check **overlap rejection, unchanged stored bookings after rejection, adjacency, and overlapping times in a different room**. Include a contained overlap case if the other tests do not cover one. Keep all four original tests.

All old and new tests should pass. The unchanged demo should now report the overlap as **rejected** and show `Stored bookings: 3`. Fix any failed check and rerun it. A passing suite supports the specific cases it tests; the demo provides a separate direct behavior check.

### 6. Publish your own public repository

On GitHub, create an **empty public repository under your personal account** named:

`iccs471-booking-lab-[FirstName]-[FirstThreeLettersOfLastName]`

For example, **Narin Sombat** creates `iccs471-booking-lab-Narin-Som`. Select **Public** and leave the options to add a README, `.gitignore`, and license **unchecked**. Do not create the repository under the course organization.

Back in PowerShell **inside your `booking-lab` folder**, run each line separately. Replace `YOUR-USERNAME` and the example name in the URL with your actual GitHub username and required repository name:

```powershell
git remote rename origin starter
git remote add origin https://github.com/YOUR-USERNAME/iccs471-booking-lab-Narin-Som.git
git remote -v
git add booking_app/booking.py tests/test_booking.py
git commit -m "Reject overlapping bookings in the same room"
git branch -M main
git push -u origin main
```

**Before pushing**, `git remote -v` must show **your own repository** as `origin` and the course repository as `starter`. If a Git sign-in prompt appears, sign in through the browser or Git credential manager. Do not provide credentials to Copilot.

Open your repository URL in a browser **while signed out or in a private window**. Confirm that it is publicly visible and that the updated `booking_app/booking.py` and `tests/test_booking.py` appear on `main`. If `git commit` says your identity is unknown, follow the Git instructions shown, configure your own name and email, and repeat the commit and remaining steps.

## Submission and AI Policy

Post the **URL of your public repository** in a **private comment on the Assignment 3 post in Google Classroom** by its displayed deadline. Submit the link, **not a ZIP**. Confirm that the comment appears; if Classroom offers **Mark as done**, use it after posting the link.

Copilot use is required for the **Ask → Plan → Agent** workflow. You remain responsible for the code and for the checks you claim to have run. Assignment 1.4 will separately asks you to explain your decisions and evidence in your own words.

If setup or Agent access prevents completion, post the link to any work you have published and state the exact blocker in the private comment. If you could not create a repository, describe the blocker in the comment. Do not invent results.

## Rubric — 10 points

| Criterion | Excellent | Good | Satisfactory | Not Acceptable / No Submission |
| --- | --- | --- | --- | --- |
| **Overlap rejection and stored state (4 pts)** | **4:** Same-room overlaps, including containment, raise `ValueError`; rejected bookings are not stored; existing validation still works. | **3:** Main rule works with one edge-case, state, or validation defect. | **2:** Some overlaps are rejected, but the rule is unreliable. | **0–1:** Rule absent or mostly ineffective. |
| **Allowed behavior (2 pts)** | **2:** Adjacent same-room bookings and overlapping times in different rooms work; existing create/list behavior remains intact. | **1.5:** Both required cases work with a minor regression elsewhere. | **1:** Only one required allowed case works reliably. | **0–0.5:** Neither works reliably. |
| **Regression tests (3 pts)** | **3:** Passing new tests cover rejection, unchanged storage, adjacency, and different rooms; the baseline tests remain intact. | **2:** Useful tests with one meaningful gap. | **1:** New tests exist, but coverage or assertions are weak. | **0:** No usable new tests, or original tests were disabled. |
| **Scope and repository submission (1 pt)** | **1:** Only permitted files changed; correctly named public repository contains the updated code and tests on `main`; correct link submitted. | **0.75:** Minor naming, scope, or publication issue; work readily assessable. | **0.5:** Significant issue requires reconstruction to assess. | **0:** No assessable repository or link. |

**Maximum: 10 points.** Assignment 4 assesses your plan decisions and evidence record separately.

## References

- [VS Code: Plan work with agents](https://code.visualstudio.com/docs/agents/run/planning)
- [GitHub: Create a new repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository)
- [GitHub: Manage remote repositories](https://docs.github.com/en/get-started/git-basics/managing-remote-repositories)
