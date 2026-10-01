# IA 3.1 — Repository Brief and Agent Instructions

## Assignment Type

Individual · Begin in class and finish at home if needed · 10 points

## Learning Objectives

- Find code relevant to a proposed change and explain its role.
- Establish the starting behaviour before implementation.
- Write useful project instructions for a coding agent.

## Duration

Aim for 25–35 minutes in class. Finish by the Google Classroom deadline. This is a planning estimate, not a speed test.

## Task Description

Use `ICCS471_Week3_Booking_Starter.zip`. Follow `README.md` and read `SPEC.md`. You are preparing to implement booking movement for an office-space rental business in IA 3.2; **do not implement it yet**.

> **Provided specification:** `SPEC.md` contains the agreed feature requirements. Read it as provided and **do not edit it**. If anything seems unclear or inconsistent, ask the instructor.

### A. Baseline

Run the creation checks using README section 2. Record the command and final result, or the exact error if blocked. Six creation tests should pass. The `move_booking` function in `service.py` is deliberately unfinished.

### B. Two code observations

Choose **two different files from `models.py`, `rules.py`, and `service.py`**. For each file, identify one function or class, explain what it does, and explain why it matters when implementing `move_booking`. Complete the two rows below. A short code excerpt is optional.

| File and function/class | What the code does | Why it matters for `move_booking` |
|---|---|---|
| First observation | | |
| Second observation | | |

> **Example from a different project (format only)**
>
> | File and function/class | What the code does | Why it matters for the search feature |
> |---|---|---|
> | `models.py / ReadingItem` | Stores an item’s ID and title. | Search results should refer to existing items without changing their IDs. |
>
> Write your own observations about the booking repository.

### C. Agent instructions

Create `AGENTS.md` with **3–5 short bullets** covering the project/context, behaviour and scope to preserve, a check command, and when to stop for review. Combine related points where useful. Refer to `SPEC.md` for the feature rules. You may use `AGENTS.template.md` as a starting point; save your completed instructions as `AGENTS.md`.

> **Example `AGENTS.md` from a different project**
>
> - This is a Python reading-list application. Use `SPEC.md` for the search requirements.
> - Preserve saved entries and their order. Keep the change limited to search.
> - Run `python -m unittest test_search` after changes.
> - Stop after the agreed edit and show the changed files for review.

Write instructions for this booking repository and keep `AGENTS.md` for IA 3.2.

## AI Policy

Read and write this yourself. Do not use generative AI to produce, critique, translate or rewrite your observations or instructions. Course materials and ordinary spell-check are allowed. Peer discussion is optional; acknowledge anyone you worked with. No peer-review report is required.

**DO NOT PLAGIARISE, including from a partner.** Submit your own work; scores are individual.

## Submission Requirements

- Submit **one PDF** to Google Classroom, containing your name/student ID, sections A–C (including the full text of your `AGENTS.md`) and collaboration acknowledgement. No page target; brief, readable answers are enough.
- Name discussion partners by full name/student ID, or write “Worked independently.”
- Filename: `ICCS471_IA3.1_[FirstName]_[FirstThreeLettersOfLastName].pdf`
- Check that the PDF opens. No implementation or code ZIP is required.

## Rubric

Each row is scored **0–2 points; total 10 points**. The two observations are scored separately.

| Criterion | Complete and clear (2) | Partly demonstrated (1) | Missing or unusable (0) |
|---|---|---|---|
| A. Baseline | Actual command and final result/error are accurately recorded | Command or result is incomplete, but the attempt is traceable | No usable record of an attempt |
| B. First observation | Precise file and function/class reference, accurate behaviour and relevant consequence for movement | Useful observation with a reference, accuracy or relevance gap | No usable observation |
| B. Second observation | A different file from the three listed in Part B supplies another precise, accurate and relevant observation | Useful but incomplete observation, or both rows use the same file | No usable second observation |
| C. Agent instructions | 3–5 specific bullets cover context, preservation/scope, checks and a review boundary, with SPEC.md referenced | Useful instructions with missing coverage or generic advice | Missing, contradictory or unusable instructions |
| Organisation and submission | Readable, correctly named PDF identifies the student, locates A–C clearly and acknowledges collaboration | Readable submission with a naming, identity, organisation or acknowledgement gap | No readable submission or student cannot be identified |
