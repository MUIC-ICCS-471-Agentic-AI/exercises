# IA 3.2 — Supervised Implementation and Change Review

## Assignment Type

Individual · Begin in class and finish at home · 20 points

## Learning Objectives

- Guide an agent using repository context and a reviewed plan.
- Inspect actual changes and justify one keep/correct decision.
- Check expected behaviour and recognise the limits of the evidence.

## Duration

Aim for 45–60 minutes in class; allow roughly 60–120 minutes total. Setup/debugging may take longer. Finish by the Google Classroom deadline.

## Task Description

Implement `move_booking` in `service.py` according to the supplied **SPEC.md**. Practise guiding an agent, inspecting its changes and checking the result. Keep existing creation behaviour and supplied tests intact.

> **Provided specification:** `SPEC.md` is the agreed target. **Do not edit it or ask AI to rewrite it.** Follow its “Allowed edits” section. If a requirement seems unclear or inconsistent, ask the instructor.

Use your own GitHub repository containing the Week 3 starter. You do not have to finish in class. Creating `AGENTS.md` and `REVIEW.md` is part of the submission; the implementation boundaries remain those in SPEC.md.

### A. Prepare and review a plan

Follow README sections 1–3 to run the baseline and commit the unchanged starter before implementation. Keep an untouched copy. Use your IA 3.1 `AGENTS.md`; if unfinished, complete it yourself using `AGENTS.template.md` first. The IA 3.1 instructions remain your own writing.

In **Plan** mode, ask Copilot to read `AGENTS.md`, SPEC.md and relevant code/tests, then propose 3–5 implementation steps. Attach files explicitly if needed. Check the referenced functions and proposed scope before starting implementation. No plan transcript is required for submission.

### B. Implement and inspect

After reviewing the plan, switch to **Agent** mode or use **Start Implementation**. Authorise the agreed change. Inspect commands before allowing them; do not use automatic approval for this exercise.

Inspect the actual changed code using **README section 4**, which explains the diff commands and how to inspect new files. Check both the new behaviour and effects on existing code. Ask for a correction if needed. Keeping a sound change with a specific reason also counts as supervision.

Record **one meaningful review decision** in `REVIEW.md`: what you inspected, its file/function or short excerpt, and why you kept or corrected it.

> **Example `REVIEW.md` excerpt from a different project**
>
> ### Review decision
>
> In `storage.py / save_item`, the diff added sorting of stored entries. The specification requires preserving their order, so I asked the agent to remove the sorting. I checked the revised diff to confirm its removal.
>
> Record a decision from your own actual work; do not copy this example.

### C. Add two tests and run the suite

Keep the supplied tests unchanged. Add a `unittest.TestCase` class in `test_student.py` with **two methods whose names start with `test_`**, covering:

- Move a booking within the same room so its new interval overlaps its own old interval, with no other blocker.
- Request the booking's current room and times again.

**Decide the starting state, action and expected outcome yourself before AI writes test code.** Record that expectation as a brief comment above each test, or as a docstring inside its method. No separate case table is needed. Inspect the assertions, including what should remain unchanged.

> **Example test expectation from a different project**
>
> ```python
> # Given: a reading list with no title containing "ocean".
> # When: search for "ocean".
> # Expect: no matches; saved entries and their order remain unchanged.
> ```
>
> This shows a starting state, action and expected result. Decide these yourself for the two booking cases above.

Run the full suite using README section 5. With exactly two added test methods it runs **11 tests**. If you add extra tests, report the actual count. Investigate failures and rerun after repairs; do not weaken correct expectations to obtain a pass.

## AI Policy

AI may help with planning, implementation and test code. Keep the `AGENTS.md` instructions from IA 3.1 student-written. **Write your initial test expectations, review decision and remaining uncertainty yourself**, without AI generation or rewriting. Ordinary spell-check and peer discussion are allowed. Work and scores remain individual.

**DO NOT PLAGIARISE, including from a partner.** Use the starter and your own declared AI output as permitted above.

> **If Copilot is unavailable**
>
> After five minutes of access troubleshooting, use the plan and candidate in `fallback/README.md` instead of the live Copilot steps. Review, test and repair the candidate manually; declare “Supplied candidate.” The same rubric and maximum score apply.

Report real results. If execution or repository access remains blocked, contact the instructor and report the exact problem.

## Submission Requirements

Submit your **GitHub repository URL and final commit hash** in Google Classroom. **Create a new repository for it. Don't mix it with week 1-2 repos**. Keep the starter project files at the repository root, as described in README section 7. Commit and push the final code, `AGENTS.md`, tests and **`REVIEW.md`**. The instructor must have access; grant access if the repository is private.

Use these headings in `REVIEW.md`:

- **Identity:** name/student ID; AI tool used or “Supplied candidate”; discussion partners' names/IDs or “Worked independently.”
- **Review decision:** the one code-grounded decision from Part B.
- **Checks:** baseline command/result and final suite command/result, or exact error if blocked. Include your baseline commit ID (or explain the comparison fallback).
- **Remaining uncertainty:** one specific behaviour or business question that your evidence has not settled.

A few sentences plus the test summary are enough. Keep the repository for Week 4. Check that a fresh clone runs with the documented command. If already working without a baseline commit, preserve your real history and explain your untouched-copy comparison; do not invent a baseline history.

## Rubric

Each row is scored **0–4 points; total 20 points**. A justified decision to retain correct code can earn full review credit.

| Criterion | Complete and precise (4) | Mostly sound (3) | Developing (2) | Limited (1) | Missing (0) |
|---|---|---|---|---|---|
| Implementation and preservation | Meets SPEC.md within scope and preserves existing behaviour | Main behaviour works with one minor requirement gap | Useful implementation with a significant behaviour or scope gap | Major failures undermine the requested feature | No assessable implementation |
| Change review and control | One actual change has a precise reference and a technically sound keep/correct decision with a clear reason | Specific, sound decision with a minor evidence or explanation gap | Relevant decision but weak code evidence or reasoning | Generic claim with little actual change inspection | No usable review decision |
| Two student tests | Both cases have student-written expectations and meaningful assertions covering outcome and relevant preserved state | Both cases are useful, with one minor expectation/assertion gap | One sound case, or substantial gaps across both | Tests mostly execute code without checking intended behaviour | No usable student tests |
| Results and remaining uncertainty | Actual baseline and final command/results and a specific uncertainty support appropriately limited claims | Honest results and relevant uncertainty with a minor detail gap | Incomplete execution evidence or vague uncertainty | Little evidence or an unsupported passing claim | No usable results or uncertainty |
| Preparation and submission | Accessible repository and submitted commit include usable AGENTS.md, baseline reference, concise REVIEW.md and identity/tool/partner details | Usable submission with one minor preparation or submission gap | Several gaps impede review or reproduction | Major missing files or traceability problems | No accessible, identifiable submission |
