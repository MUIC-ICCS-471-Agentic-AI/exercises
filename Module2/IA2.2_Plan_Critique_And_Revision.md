# IA 2.2 — Plan Critique and Revision

## Assignment Type

Individual · May be completed entirely outside class · 20 points

## Learning Objectives

- Check an agent's repository claims against actual code.
- Identify omissions, unsupported assumptions, unnecessary complexity and specification drift in a plan.
- Produce a bounded plan with checks that support its intended claims.

## Duration

Allow approximately **90–120 minutes in total**. Submit by the deadline shown in Google Classroom.

Stop after planning and review: **implementation is not required or graded**.

## Task Description

Review a proposed rescheduling feature for the supplied **`booking_week2` snapshot**. It is a separate teaching codebase, not a replacement for your Week 1 submission. It uses the same kind of booking problem but does not depend on your earlier implementation.

Use the agreed specification below even if your IA 2.1 draft differs. IA 2.1 is not a prerequisite for completing this assignment correctly.

### The model used in this assignment

The setting is an office-space rental business that rents meeting rooms by the hour for meetings and training sessions. Its booking staff manage these reservations. This is the same setting as IA 2.1.

A booking record reserves a room and time: for example, **Booking #17**, **Room 201**, 10:00–11:00. In the Python model, these are `id=17`, `room="Room 201"`, `start=600`, `end=660` and `status="active"`. Times are whole-number minutes after midnight.

The program keeps a list of booking records in memory. It has no database, room catalogue or separate availability value. The code checks availability by finding overlapping active bookings in the same room. Checking a room name's format does not establish that the room exists.

Assume authorised staff have already obtained any necessary approval outside this prototype. The task does not decide a real customer-consent policy or implement permission checks. Assume requests are processed one at a time.

### Agreed specification for everyone

Plan how to add the following function; do not implement it:

```python
move_booking(bookings, booking_id, new_room, new_start, new_end)
```

| ID | Required behaviour |
|---|---|
| R1 | Locate an existing active booking; reject an unknown ID or booking already marked cancelled with `ValueError` and an explanatory message |
| R2 | On success, update the room/start/end of the same existing `Booking` object and return that object; preserve its ID and active status; create or delete no record |
| R3 | Reject a destination overlapping another active booking in the same room; ignore cancelled bookings and the booking being moved |
| R4 | Allow back-to-back times (one booking ends when another starts) and overlapping times in different rooms. An unchanged request succeeds without changing data |
| R5 | Reject invalid input: times must be integers with `0 <= start < end <= 1440`; a room name must be text containing at least one non-whitespace character (not just spaces, tabs or line breaks). Match names exactly; do not change capitalisation or remove spaces |
| R6 | Every rejected request leaves the complete booking state unchanged. Successful moves also leave every other booking unchanged; the old position stops blocking availability. Calculate availability from the updated records, including the moved booking at its new position |
| R7 | Preserve existing creation behaviour, the in-memory list and `Booking` model. No extra software package, database, room catalogue, login/consent workflow, notifications, automatic alternative slot, recurring bookings or support for different days/time zones |

Bookings have unique integer IDs, and all records concern the same day. If several inputs are invalid, you may report any applicable error; no particular checking order is required. Python booleans are not valid times.

`ValueError` is the Python exception this function must raise when it rejects a request. Here, **input validation** means checking room names and times; it is different from **product validation**, which asks whether the system meets staff’s actual needs.

### Optional practice: examine a sample plan

If you want practice before reviewing your selected plan, examine this sample. You do not need to submit a critique of it:

> 1. Add a `previous_room` field and a database table so moves have permanent history.
> 2. Remove the original booking from the list and call `add_booking` with the requested room and time. Its existing validation and conflict checker make this easy.
> 3. If that slot conflicts, automatically try the following hour.
> 4. Use the booking returned by `add_booking` as the successful result.
> 5. Test that one ordinary move succeeds, then run the current tests. If they pass, mark rescheduling complete.

### Part A — inspect the supplied code

A repository fact is something you can establish by reading the supplied code. A function name alone is not enough: show a short code fragment and explain why its behaviour matters to the proposed change.

1. Open the supplied snapshot using the Windows instructions in its `README.md`. Read `booking.py` and `test_booking.py` yourself first. Running its baseline is recommended, but source inspection is enough if your environment fails.
2. Record **two repository facts** relevant to rescheduling. For each, identify the file and function, quote a short supporting code fragment and explain its consequence. Identify one capability the existing tests do **not** establish.

If you use the optional sample above, try identifying one requirement it violates, the consequence and a correction. You may do this on your own; no class discussion or written response is required.

### Part B — obtain a plan

Use Copilot's planning or read-only chat facility if available. Do not start implementation or approve edits. Attach/paste `booking.py`, `test_booking.py` and the agreed specification above. Ask once for a plan; one clarification is enough if needed.

Suggested prompt:

> Read the attached booking.py, test_booking.py and agreed rescheduling specification. Produce an implementation plan only. Identify the existing functions and behaviour that matter, propose the smallest changes, map checks to R1–R7, and state unresolved questions. Do not edit files, run commands, install dependencies or implement anything. Separate facts observed in the code from your proposed changes. Stop after the plan.

Save the prompt and relevant response as text. Asking for “a plan only” does not disable editing tools. Review proposed actions and decline modifications. If files change accidentally, stop and reopen a freshly extracted copy; disclose what happened. Do not delete or reset your Week 1 work.

**If Copilot is unavailable**, quota-limited or taking more than five minutes to troubleshoot, review the supplied plan below instead. Label your source `Fallback B`. This route has the same rubric and maximum score; do not invent an agent transcript.

### Fallback B: supplied plan

Use this plan for Part C if you cannot obtain a Copilot plan:

> 1. Find the target and reject it if missing or cancelled.
> 2. Validate the new room and interval with the existing validators.
> 3. Reuse `has_conflict` to check the destination against the whole list.
> 4. If it is free, update the target's room/start/end in place and return it. Do not add fields or dependencies.
> 5. Test an ordinary successful move and a conflict rejection, then run existing tests.

### Part C — review, revise and justify

Submit the following four parts in your own words.

**1. Review the plan you selected in Part B.** Give three substantive observations. For each, use these headings: `Plan excerpt | Code or requirement reference | Consequence | Correction or reason to retain`. You can identify a defect, an omission or a sound choice. If the plan is sound on a point, explain why; do not invent a defect.

*Format example from an unrelated reading-list app* (illustrative only, not a finding about `booking_week2`):

| Plan excerpt | Code or requirement reference | Consequence | Correction or reason to retain |
|---|---|---|---|
| “Keep `add_item` unchanged.” | Existing users must still be able to add reading-list entries. | The existing creation path remains available. | Retain the choice, then check that adding an entry still works after the proposed change. |

**2. Revise the plan.** Write 5–8 ordered steps and name the relevant functions. Make clear which functions already exist and which you propose adding. Your steps should explain how you would:

- Check for errors before changing any booking data.
- Avoid counting the booking being moved as a conflict with itself.
- Keep the same booking object and ID.
- Check that the existing booking-creation behaviour still works.

**3. Propose three groups of checks.** For each check, use the columns `Requirement IDs | Existing bookings and requested action | Expected result | What this check would establish`. Cover:

- A successful move to a *different room*: the same object and ID remain, and the old room and time become available.
- A rejected move: **all** booking records remain unchanged.
- Two separate subcases: a move whose new time overlaps its own old time, and a request that leaves the room and time unchanged.

*Check-format example from the same unrelated app* (not a booking check):

| Requirement IDs | Existing records and requested action | Expected result | What this check would establish |
|---|---|---|---|
| Example S1 | Reading list contains “Blue notebook” and “Red notebook”; search for “Blue”. | Return only “Blue notebook”; leave both entries stored. | Search finds the matching entry without changing the list. |

State the starting booking records for each check or subcase; do not assume one check follows another. You may adapt IA 2.1 cases without copying its whole table. Use distinct labels such as Booking #17 and Room 201. These are **checks you propose**, not results you have observed. In your revised plan, also name the other requirement groups you would check before accepting an implementation.

**4. Make an approval decision (60–100 words).** Approve your revised plan for implementation, request a revision, or defer the decision until a specific point is clarified. Give a reason, one remaining limitation and one way to investigate whether the feature meets staff's actual rescheduling need. A plan alone does not establish that the product has been verified or validated.

## AI Policy

AI is allowed only to generate the plan and clarify that plan during Part B. You may copy or adapt the supplied prompt. The repository facts, critique, revised plan, targeted checks and approval decision must be written by you without AI generation or rewriting. You may consult your saved Part B response and course materials. Save the original response rather than overwriting it with your revision. Ordinary non-generative spell-check is allowed.

The same AI rules apply in class and at home: Part B may use AI; your assessed reasoning must be your own.

Peer discussion is optional and may happen in class or outside class. If you discuss the work, name each discussion partner in your submission; otherwise state “Worked independently.” Each student submits their own work and is scored individually. **DO NOT PLAGIARISE, including from a discussion partner.** Do not copy or lightly reword another student's answers.

## Submission Requirements

- Submit **one PDF** to the corresponding Google Classroom assignment, by its displayed deadline.
- Include name and student ID; repository facts; selected-plan review; revised plan; three targeted check groups; approval decision; AI/fallback declaration and discussion-partner acknowledgement (or “Worked independently”).
- Append the exact prompt and relevant original response if using Copilot. If using fallback B, identify it; no copied transcript is necessary.
- Aim for **2–3 readable pages excluding the prompt/response appendix**. This is guidance, not a page limit. Tables and concise bullets are encouraged; no minimum total word count.
- Filename: `ICCS471_IA2.2_[FirstName]_[FirstThreeLettersOfLastName].pdf`
- Example: `ICCS471_IA2.2_Narin_Som.pdf`
- No implementation, code ZIP or screenshot collection is required. If you ran the baseline, state the result; if not, say source inspection only. Do not claim checks you did not run.

## Rubric

Each row is scored from 0–4; total **20 points**. Tool access and the quality of the agent's original answer do not determine your grade.

| Criterion | Complete and precise (4) | Mostly sound (3) | Developing (2) | Limited (1) | Missing (0) |
|---|---|---|---|---|---|
| Repository grounding | Two accurate facts cite relevant code and explain consequences; baseline limits are identified honestly | Accurate grounding with one minor missing explanation | One usable fact or weak code support; baseline limits unclear | Mainly unsupported claims about the repository | No repository evidence |
| Plan critique | Three selected-plan observations are accurate, tied to code/requirements and justify correction or retention | Most findings are well supported; a minor omission remains | Several findings are generic, repetitive or weakly supported | Major conflicts are missed; critique is mostly assertion | No assessable critique |
| Revised plan | Bounded, ordered and tied to actual/proposed functions; leaves data unchanged on rejection, keeps the booking object/ID, ignores the booking as its own conflict and preserves existing behaviour | Coherent plan with a minor gap | Useful steps but a significant requirement or sequencing gap | Changes data before checking for errors, adds excluded work or leaves a major inconsistency | No usable revised plan |
| Checks and judgment | Three targeted check groups have concrete outcomes; claims are appropriately limited; approval and validation proposal are justified | Mostly concrete checks and a sound decision with a minor gap | Several weak checks or an under-supported decision | Generic tests or unsupported completion claims | No usable checks or judgment |
| Evidence and submission | Readable, correctly named PDF with identity, organised sections, original prompt/response or fallback declaration, and acknowledgement | Complete, reviewable record with one minor submission issue | Multiple traceability or submission issues | Provenance or organisation is seriously incomplete | Submitted file cannot be opened or read |
