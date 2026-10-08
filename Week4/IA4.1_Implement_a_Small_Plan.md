# IA4.1 — Implement a Small Plan

## Assignment Type
Individual formative assignment · **10 points**

## Learning Objectives
Follow a bounded plan, supervise implementation, inspect a change and justify it with evidence.

## Duration
Allow approximately 40–60 minutes. Finish by the Classroom deadline if needed. This is one function and one additional test, with a short response.

## Task Description
Use `ICCS471_Week4_Starter.zip`. Staff at an office-space rental business ask: **“Which candidate rooms can we offer for this time interval?”**

Implement the function **`service.py` → `available_rooms(bookings, rooms, start, end)`** to return the available room names in the supplied order. `SPEC.md` defines the required behaviour; `PLAN.md` gives the implementation steps.

| Code location | Role |
|---|---|
| `rules.py` → `has_conflict(...)` — existing function | Checks one room. Returns `True` if a conflicting active booking exists, otherwise `False`. |
| `service.py` → `available_rooms(...)` — function to implement | Checks each supplied candidate using the existing helper and returns the names with no conflict. |

The existing helper already handles cancelled bookings and adjacency correctly. Reuse it; do not implement those rules again. `rules.py` → `validate_interval(...)` supplies input validation.

### A. Prepare and review

1. Extract the starter, open it in VS Code and keep an untouched copy for comparison. Read `SPEC.md`, `PLAN.md` and `AGENTS.md`.
2. Run the full test command in `README.md` and record the initial result. **Two tests pass and two raise `NotImplementedError`** because the function is unfinished.
3. Choose one additional check: adjacency, ignoring a cancelled booking, or preserving candidate-room order. Test `available_rooms`, not just the helper. **Write your own concrete Given/When/Expect comment inside `StudentCheck` in `test_student.py`, immediately above the test method to be added.** Leave writing the method to the implementation step.
4. In Copilot's **Plan mode**, ask it to read the supplied documents, relevant code/tests and your comment. Ask it to explain how it will implement `available_rooms` and add one test method based on your expectation. Review its approach before authorising edits. **Do not ask it to rewrite `PLAN.md` or your expectation.** No plan transcript is required.

> **Format example from another project**
>
> ```python
> # Given: saved titles are ["Dune", "Solaris"].
> # When: search for "ocean".
> # Expect: no matches and the saved titles remain unchanged.
> ```
>
> Use your own concrete values and expected outcome for the booking case you choose.

### B. Implement and check

1. After reviewing the approach, switch to **Agent mode** (or use **Start Implementation**) and authorise Copilot to implement **`available_rooms` in `service.py`** and add **one `test_...` method inside `StudentCheck` in `test_student.py`**, using your comment. Keep the comment immediately above that method.
2. Compare both edited files with your untouched starter copy. In VS Code's Explorer, right-click the original file and choose **Select for Compare**, then right-click the edited file and choose **Compare with Selected**. Inspect the function and the test's assertions: do they implement and check the behaviour you intended?
3. Run the full suite using the README command. With your one added test, **five tests should be discovered**. Investigate failures, correct faulty implementation or test code, and rerun. Do not weaken a correct expectation merely to obtain a pass.

> **File boundary**
>
> Keep `SPEC.md`, `PLAN.md`, `AGENTS.md`, `models.py`, `rules.py` and supplied tests unchanged. Only the `available_rooms` function in `service.py`, your test/comment in `test_student.py`, and your own `RESPONSE.md` may change.

### C. Record the result briefly
Complete `RESPONSE.md`: initial/final commands and results, one code review decision naming the file/function and explaining what you kept or corrected in 1–2 sentences, and a Done/Not Done judgment in 2–3 sentences. State what your evidence supports and one limitation or next check. Keeping correct code with a specific reason counts as a review decision. If you know the code violates a requirement, mark it Not Done.

## AI Policy
AIAS Level 3: Copilot may assist implementation and test code. Write your expectation comment, review decision and Done judgment yourself; AI must not generate or rewrite them. Ordinary spell-check is allowed. If AI is unavailable, review the supplied plan and implement the function and test manually, keeping the same sequence and submission requirements. Record No AI.

Optional discussion is allowed; name human discussion partners (or write Worked independently) and submit individually. Declare Copilot separately as a tool. **DO NOT PLAGIARISE, including from a partner.** Each student must understand and explain their submitted code.

## Submission Requirements
Submit one ZIP to Classroom named `ICCS471_IA4.1_[FirstName]_[FirstThreeLettersOfLastName].zip`, containing only `service.py`, `test_student.py` and `RESPONSE.md`. Include your name/ID, tool and partner declaration in the response. No new repository, PDF, screenshot collection or full chat transcript is required.

## Rubric
**Total: 10 points.**

| Criterion | Complete (2) | Partial (1) | Missing or unusable (0) |
|---|---|---|---|
| Implementation | Function follows R1–R5 and keeps edits within scope | Useful implementation with a behaviour/scope gap | No usable implementation |
| Independent check | Concrete student-chosen expectation and assertions meaningfully test one listed behaviour | Relevant case but weak expectation/assertions | No meaningful additional check |
| Review decision | Identifies an actual code decision and a sound reason | Relevant but vague/incomplete explanation | No credible inspection evidence |
| Results and Done judgment | Actual initial/final results support a bounded judgment and a specific next check/limitation | Useful evidence with a missing result or weak judgment | Unsupported claim or no usable evidence |
| Submission | Correct ZIP/files and readable identity/tool/partner details | Minor format or declaration gap | Missing/unidentifiable or unusable submission |
