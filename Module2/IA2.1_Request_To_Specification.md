# IA 2.1 — Request to Specification

## Assignment Type

Individual · In-class work with peer review and a short take-home revision · 20 points

## Learning Objectives

- Turn an incomplete request into bounded, observable requirements.
- Distinguish requirements, constraints, exclusions and unresolved assumptions.
- Use acceptance criteria and counterexamples to expose hidden decisions.

## Duration

Approximately 60 minutes in class, followed by up to 15 minutes to finalise your submission.

## Task Description

You are preparing instructions for a coding agent. **Do not write or request an implementation.** Your task is to specify a small booking-rescheduling feature.

### Initial request

> “Let staff move a booking to another room or time. If the move cannot be made, keep the original booking.”

Before reading the stakeholder card, spend **5 minutes** recording three questions you would ask and why their answers matter. Preserve these initial answers in your submission.

### Stakeholder card — confirmed information for this exercise

#### The people and the limits of this prototype

Staff need to move an existing reservation without losing it if the requested move fails. The person who owns or uses the booking may also be affected.

For this exercise, assume authorised staff have already obtained any approval needed before requesting a move. The prototype does not check customer consent or staff permissions. This does **not** establish a real business policy allowing staff to move bookings without consent. You may record that policy as a question for a real deployment, but do not add an approval system to this task.

#### How the booking records work

- A **booking** is a reservation record. A **room** is the space being reserved. For example, **Booking #17** reserves **Room 201**, 10:00–11:00. Each booking has a unique integer ID, room name, start time, end time and status (`active` or `cancelled`).
- Records are held in program memory. There is no database, room catalogue or separately stored list of available times. The code checks availability by looking for overlapping **active bookings** in the requested room.
- All bookings concern one day. Times are whole-number minutes after midnight: 10:00 = 600, 11:00 = 660 and 24:00 = 1440. Valid times satisfy `0 <= start < end <= 1440`. Decimal values and Python booleans are not valid times.
- A room name must be text containing at least one non-whitespace character (not just spaces, tabs or line breaks). This only checks the name's format, not whether the room exists. Match names exactly: `Room 201` and `room 201` are different names. Do not automatically change capitalisation or remove spaces.

#### What a move must do

- Move an **existing active booking** to the requested room and time. On success, keep the same booking ID and active status, update its room and times, and leave every other booking unchanged. Do not create or delete a booking.
- The booking's old position must stop blocking availability. Availability is then calculated from the updated records. If the new time overlaps part of the old time in the same room, that shared period remains reserved by the moved booking.
- Reject a move that overlaps **another active booking in the same room**. Bookings in different rooms do not conflict. Cancelled bookings do not block the requested destination.
- Back-to-back bookings are allowed: one may end at 11:00 and another start at 11:00. This is called **adjacency**.
- Do not count the booking being moved as an obstacle to itself. For example, moving Booking #17 from 10:00–11:00 to 10:30–11:30 must not fail solely because it overlaps its own old time. Other active bookings can still block the move.
- Requesting the booking's current room and times again succeeds without changing any data. This is an **unchanged request**, also called a no-op.
- Reject an unknown booking ID, a booking already marked cancelled, an invalid room name or time, or a conflict with another booking. Explain why the request failed and leave **all booking records unchanged**, including the original reservation.

#### What is outside this task

Keep the existing booking model and other behaviour. Do not add a database, extra software package, room catalogue, login or consent workflow, automatic choice of an alternative slot, notifications, recurring bookings, or support for different days/time zones. Assume requests are processed one at a time.

The card supplies the decisions for this teaching exercise. Use them in your specification. Identify any real-world limitation separately rather than silently expanding the task.

### Your work

**A. Initial questions** — Keep your three pre-card questions and reasons. After reading the card, mark each as **answered, partly answered or still open**, with a brief explanation. If a concern is handled by an exercise assumption or excluded from the task, say so; that is different from establishing a real business policy.

**B. Specification for this task** — Write:

- the stakeholder's goal in 1–2 sentences;
- 5–8 numbered requirements, using IDs such as R1 and R2;
- at least two **constraints** (limits on how it may be built) and two **exclusions** (features this task will not include);
- any essential question still open after reading the card. If none remains, say so; do not manufacture uncertainty. Your initial questions already record the decisions you identified.

**Examples of numbered requirements**

| Requirement ID | Example requirement |
|---|---|
| R1 | A successful move must update the existing booking, keep its ID and active status, and stop its old position from blocking availability. |
| R2 | A rejected move must leave all booking records unchanged, including the original booking's room and times. |

You may use or adapt these two requirements and complete your own set of 5–8. Use your requirement IDs consistently in Part C.

**C. Acceptance table** — Write **eight case groups**, with columns: `Case ID | Requirement ID | Existing bookings and requested action | Expected result and what must remain unchanged`. Cover:

1. A successful move, including what happens to the old slot.
2. A conflicting move that preserves the original booking.
3. Back-to-back bookings: one ends exactly when another starts.
4. An overlapping time in a different room that does not block the move.
5. A move overlapping the booking's own old time, plus a separate request that leaves its room and times unchanged.
6. A cancelled booking at the requested room and time that does not block the move.
7. Rejection of an unknown booking ID and of a request to move an already-cancelled booking (two subcases).
8. Invalid input (one time example and one room example).

Use clear labels such as **Booking #17** and **Room 201**, with concrete times. Requirement IDs such as R1 label your written rules, not bookings. Each group may contain short subcases; it is not limited to one test. Treat each subcase as starting from its own stated booking state. You may use clock notation such as 10:00–11:00. No test code is required.

**Example of one case: a successful move**

This example uses R1 from Part B. If you number or group your requirements differently, use the matching requirement ID(s) from your own specification.

| Case ID | Requirement ID | Existing bookings and requested action | Expected result and what must remain unchanged |
|---|---|---|---|
| C1 | R1 | The only record is Booking #17, active, Room 201, 10:00–11:00. Request moving it to Room 202, 12:00–13:00. | Accept the move. Booking #17 now reserves Room 202, 12:00–13:00; its ID and active status remain unchanged. Room 201, 10:00–11:00 is available again. The list still contains exactly one booking. |

This row covers the successful-move group. You may adapt it for your submission, then complete the remaining groups. Each row should state the starting situation, requested action and observable result, rather than only saying “the move works.”

**D. Counterexample and revision** — Describe one concrete situation showing why a plausible but incorrect approach would fail. You may reuse a case from your acceptance table. Explain the incorrect result and the required result. Compare your draft with a partner for 5–10 minutes, then record one revision you made, or one reason you retained your original decision. Include your review partner’s full name and student ID. If you finish outside class, keep the feedback from your in-class review or arrange a brief review with a classmate before submitting.

## AI Policy

Do not use generative AI to produce, critique, translate or rewrite this assignment, including the take-home revision. Ordinary non-generative spell-check is allowed. Use the lecture, course reading and stakeholder card. Discussion is allowed during the designated peer review.

**DO NOT PLAGIARISE, including from your review partner.** You may discuss ideas and give feedback, but you must write your own answers, tables and explanations. Do not copy or lightly reword another student’s work. Naming your partner does not make copying acceptable. The supplied examples may be used or adapted as permitted above.

## Submission Requirements

- Submit **one PDF** to the corresponding Google Classroom assignment, by its displayed deadline.
- Include your name, student ID, all four sections and the peer-review note. Use concise tables and bullets; typically **2–3 readable pages**. This is guidance, not a page limit or minimum word count.
- Identify your review partner by **full name and student ID**, and state what you revised or why you retained your original decision after the review.
- Filename: `ICCS471_IA2.1_[FirstName]_[FirstThreeLettersOfLastName].pdf`
- Example: Narin Sombat → `ICCS471_IA2.1_Narin_Som.pdf`
- Check that the PDF opens and that table text is readable. No code, ZIP or separate template is required.

## Rubric

Each row is scored from 0–4; total **20 points**. Your work is assessed on clear reasoning and consistency with the stakeholder card.

| Criterion | Complete and precise (4) | Mostly sound (3) | Developing (2) | Limited (1) | Missing (0) |
|---|---|---|---|---|---|
| Questions and decisions | Three consequential questions have reasons and answered/partly answered/open status and explanations consistent with the card | Questions and decisions are useful with one minor omission | Some questions are generic or decision status is unclear | Little useful questioning; invented policy treated as fact | No assessable questions |
| Requirements and scope | Goal and requirements are consistent, actionable and cover core behaviour; constraints and exclusions bound the work | Main behaviour and scope are clear with a minor omission | Several gaps or ambiguous requirements remain | Major contradiction or expansion makes the specification unsafe to implement | No usable specification |
| Acceptance cases | All eight categories have concrete conditions and correct expected outcomes, including preserved state | Most cases are usable; one category or detail is weak | Several categories are missing or expected outcomes are vague | Mostly generic success statements or incorrect outcomes | No usable acceptance cases |
| Counterexample and revision | Counterexample exposes a specific wrong approach; correct result and reasoned revision/retention are explained | Sound counterexample and review with a minor explanation gap | Plausible example or review, but their reasoning is incomplete | Example does not challenge an approach; revision is unexplained | Neither counterexample nor review is provided |
| Organisation and submission | PDF is readable, correctly named, identifies the student and includes clearly located sections and review acknowledgement | Readable and complete with one minor submission issue | Several presentation/submission issues slow review | Major missing identification or poor organisation makes review difficult | Submitted file cannot be opened or read |
