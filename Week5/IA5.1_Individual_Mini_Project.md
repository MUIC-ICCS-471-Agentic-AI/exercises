# IA5.1 — Build a Small Project with Copilot

## Assignment Type

Individual mini-project · **20 points**

## Learning Objectives

Practise the complete workflow: define a task, review a plan, supervise implementation, check the result, and explain your decisions.

## Duration

**One week.** See Classroom for the deadline. Aim for roughly **4–6 hours in total**; choose a scope that fits your experience.

## Task Description

Build a small application, useful tool or game with GitHub Copilot. Start your own project and GitHub repository. Choose **two or three related features** and at least one rule or calculation you can check. A command-line interface is enough; graphics and saving data between runs are optional unless your requirements need them.

Use Python or another language you already know. This is individual practice before Practical 1, separate from the team term project. A small, understandable project is enough for full marks.

--- **IMPORTANT** It is conventional and is a professional habit to commit changes in small meaningful chunks. Do NOT make 5-10 changes across different files then commit as one. Ideally each commit should be separated by file then per purpose of code edit.

### Possible projects

Propose your own idea or choose among the examples below. These are starting points, not prescribed specifications.

| Idea | A possible small version |
|---|---|
| Expense tracker | Enter expenses, group them by category, and calculate totals. |
| Study planner | Add tasks, mark completion, and show remaining work. |
| Flashcard quiz | Ask questions, check answers, and show a score. |
| Small data tool | Read a simple CSV file, filter its rows, and produce a useful summary. |
| Number-guessing game | Accept guesses, give higher/lower hints, and limit attempts. |
| Tic-tac-toe | Two local players, reject occupied squares, and detect a win or draw. |
| Text adventure | A few connected locations, an inventory, and one puzzle or goal. |

## Tasks

Keep four short Markdown files in the repository root. **These are templates to complete and adapt, not finished submission files.** Replace every bracketed prompt with content specific to your project. You may keep useful headings and general instructions, but complete the project-specific details. Bullets and short sentences are enough; do not repeat the same information across files.

| File | Purpose |
|---|---|
| `README.md` | What the project should do and how to run it. |
| `AGENTS.md` | How Copilot should work in this repository. |
| `PLAN.md` | The implementation steps you reviewed before coding. |
| `EVIDENCE.md` | Your checks, actual results, decisions and final judgment. |

No `SPEC.md` is needed. Your three requirements belong in `README.md`.

### A. Define the project and prepare the checks

Write the purpose and **three concrete requirements** in `README.md`, including an important rule or boundary. Give them IDs R1–R3 so you can refer to them in your checks. Fill in the setup/run/test instructions as the project develops.

**README.md template**

```markdown
# [Project name]

> This file explains who the project is for, what it should do, and how to run it.

## Purpose
[Who will use it, and what will it help them do? One or two sentences.]

## Requirements
- R1: [One concrete behaviour.]
- R2: [One concrete behaviour.]
- R3: [One concrete behaviour, including an important rule or boundary.]

## Setup and use
- Prerequisites: [Language/version and any dependencies.]
- Setup: [Exact command(s) or steps.]
- Run: [Exact command and a brief example of how to use it.]
- Run tests: [Exact command.]

## Author and acknowledgements
- Name / student ID: [...]
- AI tools used: [...]
- External code/resources: [Links and what you used, or None.]

See PLAN.md for the implementation plan and EVIDENCE.md for results and decisions.
```

Before asking AI to write implementation or tests, write **two concrete checks yourself** in `EVIDENCE.md`: one normal case and one boundary, invalid action or failure case. Fill in Given, When and Expected result; leave Actual result blank until you run the check. Add checks later if needed to cover all three requirements.

> **Example from another project**
>
> | Given | When | Expected result |
> |---|---|---|
> | A basket contains two items priced at 40 each | Calculate its total | The total is 80 |
>
> Use your own project's inputs and expected results. The EVIDENCE.md template is in Part C.

### B. Review a plan, then implement

Create a short `AGENTS.md` with useful instructions for this project. Ask Copilot to read it together with your requirements and initial checks. Explicitly provide these files as context if necessary.

**AGENTS.md template**

```markdown
# Instructions for this repository

> This file tells the coding agent how to work on this project. It does not replace the requirements or plan.

- Read README.md, PLAN.md and the checks in EVIDENCE.md before implementing.
- Keep changes within the three requirements in README.md.
- Use [language/version and any project-specific conventions].
- [One useful project-specific instruction, such as keeping calculations separate from interface code.]
- Run tests with: [command; fill in once chosen].
- Do not change an expected result merely to make a test pass. Raise any disagreement for review.
- Leave requirements, expected results, decision notes and the final judgment for the student to write.
```

Ask Copilot to propose a short implementation plan, including how to check the result. Review and adjust the approach before authorising implementation, and save the agreed steps in `PLAN.md`. Record one plan decision and its reason in `EVIDENCE.md`.

**PLAN.md template — replace the prompts with your reviewed project steps**

The numbered items below are planning prompts, **not a ready-made implementation plan**. Replace each with an actual step for your application or game: name what you will build or check and the relevant file/function/component where useful. You may add, combine or reorder steps to suit your project. Copilot may draft the plan, but you must review it before implementation.

```markdown
# Implementation plan

> This file records my project-specific steps reviewed before coding. Replace the prompts below with the agreed plan; refer to R1–R3 rather than copying the requirements here.

## Steps
1. [What will I create first? Name the main files/components and their roles.]
2. [Which behaviour will I implement next, where, and for which requirement(s)?]
3. [Which specific rule or boundary will I handle, and how?]
4. [Which check from EVIDENCE.md will become an automated test, and how will I run the tests?]
5. [Which realistic task will I try from start to finish to judge usefulness?]

## Later changes, if any
[Briefly state any change to the agreed plan and why, or None.]
```

Commit your requirements, agent instructions, reviewed plan and two expected checks **before implementing**. If the scope changes later, update the requirements and plan and briefly explain the change.

Implement with Copilot in small steps. Read the changed code, run it, and correct problems before continuing. Commit at meaningful points. In `EVIDENCE.md`, record **one code decision**: what you accepted or changed and why, naming the relevant file/function or component. You do not have to find an AI mistake if the proposal is sound.

### C. Check the result and record your judgment

- Run your concrete checks and record actual results. Check each of R1–R3 at least once; one check may cover more than one requirement.
- Include **at least one automated test** for an important rule or calculation. Copilot may help write it; inspect its assertion against your expected result. Interface interactions may be checked manually.
- Run all automated tests and record the command and final result. Correct problems and rerun where needed.
- Try one realistic task from start to finish: use the application for its intended purpose or play a round of the game. Record whether it was useful or playable and one difficulty or limitation. You may do this yourself; another person's input is optional.

**Verification:** does it behave as specified? **Validation:** does it serve the intended user and purpose? A passing test alone does not answer both questions.

**EVIDENCE.md template**

```markdown
# Checks and decisions

> This file records what I checked, what actually happened, and why I accepted or changed the work. It does not repeat setup instructions or the implementation plan.

## Concrete checks
Write the first two expectations before implementation. Fill in actual results after running them.

| Check / requirement | Given | When | Expected result | Actual result / pass or fail |
|---|---|---|---|---|
| C1 / R... — normal case | [Concrete starting state/input.] | [Action.] | [Exact expected outcome.] | [Complete after checking.] |
| C2 / R... — boundary or failure case | [Concrete starting state/input.] | [Action.] | [Exact expected outcome.] | [Complete after checking.] |

[Add rows only as needed to cover R1–R3.]

## Two review decisions
- Plan decision: [What I accepted or changed, and why. One or two sentences.]
- Code decision: [File/function/component, what I accepted or changed, and why. One or two sentences.]

## Automated tests
- Test file and behaviour checked: [...]
- Command I ran: [...]
- Final result: [Actual test count and outcome.]
- Correction and rerun, if needed: [Brief account, or None needed.]

## Realistic use and final judgment
- Task I tried: [One realistic use from start to finish.]
- Outcome: [What happened and whether it served the intended user/purpose.]
- Judgment: [Done / Partly done / Not done, with a brief reason based on the evidence.]
- Remaining limitation or unfinished work: [One specific item, or a useful next check.]
```

### D. Finish and submit

Replace any remaining template prompts with your own content (or an explicit None / Not completed where appropriate). Complete the four files and check that the setup/run/test instructions work from a fresh copy of your repository. Include the application, test(s), and any dependencies or sample data needed to run it. Keep credentials and private data out of the repository.

Short notes are sufficient. No separate report or chat transcript is required.

## AI Policy

Use **GitHub Copilot for planning and implementation**. It may also help with tests, debugging and documentation. You are responsible for understanding and checking the result.

Write the requirements, expected results, decision notes and final judgment in your own words. Discussion is welcome, but each student must develop their own project. **Do not plagiarise, including from a partner.** Acknowledge reused code and resources. If Copilot access blocks you, contact the instructor early.

## Submission Requirements

Submit your **GitHub repository URL and final commit ID** in Classroom. Ensure the instructor has access. The repository must contain your code, test(s), `README.md`, `AGENTS.md`, `PLAN.md` and `EVIDENCE.md`.

Submit your progress even if something remains unfinished, and identify it honestly in `EVIDENCE.md`.

## Rubric

**Total: 20 points.** The emphasis is on completing and understanding the workflow, not project size or visual polish.

| Criterion | What earns full credit | Points |
|---|---|---:|
| Scope and planning | A clear purpose, three concrete requirements, useful agent instructions, and a reviewed plan recorded before implementation. | 4 |
| Implementation | The small project's main features and important rule work as described. | 6 |
| Review and decisions | Two brief, specific notes explain a plan decision and a code decision. | 3 |
| Verification | Concrete checks cover the requirements; at least one meaningful automated test is included; actual results are reported. | 4 |
| Usefulness and delivery | The project can be run from the instructions, and a realistic walkthrough supports an honest conclusion and limitation. | 3 |

Partial credit is available for meaningful progress. Minor cosmetic issues do not prevent full marks. Additional features, lengthy reports and elaborate interfaces earn no extra credit by themselves.
