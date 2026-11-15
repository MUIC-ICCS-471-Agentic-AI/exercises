# ICCS471 — Term Project: Requirements and Final Submission

**Team project · GitHub Copilot and Claude permitted**

Build a small application based on your GA4.2 research and team feedback. Show that you can plan a change, supervise AI-assisted implementation, check the result and explain your decisions.

Work with your existing team and use the feedback on your GA4.2 project research. This document defines the required code, working documents, final submission and team-product rubric.

## 1. Schedule and assessment

All times are **Bangkok time**.

| Stage | When | Course weight | Instructions |
|---|---|---:|---|
| GA4.2 research | Already assessed | 5% | Existing mark counts once; no further submission |
| Informal team conversation | 20 November, in class | Ungraded | Show current work, discuss a difficulty and next step; no submission |
| Project checkpoint | 26 November, 23:59 | 10% | Detailed instructions will follow in Classroom |
| Individual defence and development evidence | Tentatively 27 November or 4 December | 25% | Dates, slots and detailed instructions will be confirmed in Classroom |
| Team demonstration | 4 December, in class | Included in final team mark | Detailed instructions will follow in Classroom |
| Final team submission | 6 December, 23:59 | 30%, including demonstration | Section 5 below |

The checkpoint and presentation guidance will be released separately.

## 2. Code and product requirements

**Expected work:** Choose two core features that work together to complete a useful user task. A third feature is optional. Use your team feedback to set the scope.

A **core feature** is a meaningful capability that helps users solve the main problem, rather than an individual button or screen. The **main workflow** is the connected sequence of actions that takes a user from a need to a useful result; it may involve more than one user role.

> **Example:** In a simple ordering application, the two core features could be **placing an order** and **managing the order queue**. The main workflow is: a customer submits an order → staff see it in the queue → staff mark it ready → the customer can see that it is ready.

By final submission, the application should:

- Complete its main workflow, with understandable results and useful handling of relevant errors.
- Retain the information needed for that task after closing and reopening. Browser storage, a local file or a database may be suitable.
- Have meaningful checks of important behaviour and reproducible setup/run instructions.

A simple interface, local execution, test accounts and clearly labelled simulated integrations are acceptable. Public hosting, real payments, campus data feeds, runtime AI, CI pipelines and production-scale infrastructure are not required. A small, reliable prototype can earn full marks.

You may choose the programming language and technology stack appropriate for your project. Document runtime versions, dependencies and the commands needed to install, run and test the application in README.md.

You may use libraries and starter templates. Identify what you reused and what your team implemented or changed. Each member must be able to explain their own contribution.

## 3. Required working documents

**Format:** Create or continue using a team GitHub repository, give the lecturer access and maintain these four Markdown files at its root. Use short bullets or tables; there is no minimum word count.

| File | What to write |
|---|---|
| `README.md` | Team members, intended users, the two core features, important behaviour rules, scope/simulations, runtime versions, dependencies, install/run/test commands, reused libraries/templates and known limitations. |
| `AGENTS.md` | Instructions for the AI assistant: relevant files, change boundaries, commands and review expectations. Provide it explicitly if your tool does not load it automatically. |
| `PLAN.md` | Your reviewed implementation steps, their progress and important changes to the approach. |
| `EVIDENCE.md` | Actual check results, review decisions, member contributions, tools used, user feedback, the checkpoint update and final status. |

Before implementing a core feature, describe its intended behaviour in README.md and record concrete expected outcomes in EVIDENCE.md. Update these when the intended behaviour changes. Give AI the relevant context, request a plan and review it in PLAN.md. Then implement in small changes, inspect the code and run checks.

The following are starting templates. **Replace every bracketed prompt with your own content** and add or adapt headings where useful. The prompts are not completed answers. Update the documents as your project develops.

**README.md template**

This introduces the application and explains how to run it. Keep development decisions and check results in EVIDENCE.md.

```markdown
# [Project name]

## Team and purpose
- Members: [names, student IDs and GitHub usernames]
- Intended users and problem: [who needs this and why]

## Core workflow and scope
- Feature 1: [what the user can do]
- Feature 2: [how it connects to feature 1]
- Important behaviour rules: [conditions the application must respect]
- Simulations and exclusions: [what is simulated or outside your scope]

## Setup, run and test
- Runtime versions and dependencies: [what is needed]
- Install: [commands and any configuration steps]
- Run: [commands and how to open/use the application]
- Test: [commands]
- Sample data/test accounts: [how to load or use them, if applicable]

## Reused work and limitations
- Libraries, starter templates, code and assets: [sources and what you changed]
- Known limitations: [what users should know]
```

**AGENTS.md template**

This guides the AI assistant in your repository. Fill it with actual paths, commands and boundaries; provide it explicitly if your tool does not load it automatically.

```markdown
# Repository instructions

## Project context
[Brief purpose and chosen stack. Refer to README.md for product details.]

## Relevant files
- [Path]: [its role]
- [Path]: [its role]

## Change boundaries
[What the assistant may change, what it must preserve, and when it should ask.]

## Commands
- Run: [actual command]
- Test: [actual command]

## Working and review expectations
[How the assistant should use PLAN.md, keep changes reviewable, and report
checks, failures and uncertainty for human review.]
```

**PLAN.md template**

This records your reviewed approach before implementation. Replace the prompts with actual steps for your project; they are not a completed plan.

```markdown
# Implementation plan

## First workflow
[What the user will do, from input to result]

## Steps
1. [Specific change, relevant component and how you will check it]
2. [Next specific change and check]
[Add only the further steps your workflow needs.]

## Plan review
[What you changed or confirmed in the suggested plan, and why]

## Progress and revisions
[Completed steps, remaining work and important changes to the approach]
```

Discuss a substantial change of project direction or removal of important agreed behaviour with the lecturer; routine implementation choices are yours.

## 4. Required development evidence

**Expected work:** Test important behaviour, explain your contributions and collect feedback from a person using the application for a realistic task. Record important checks and decisions as you work. You do not need a transcript of every AI conversation or a diary of every edit.

**Format:** Keep automated tests in the repository and concise records in EVIDENCE.md. The following records are required by final submission:

| Record | What is expected |
|---|---|
| Behaviour checks | A normal case, a rejected/invalid action and a relevant boundary or interaction. Use automated tests for important logic and a short manual walkthrough for the user-facing workflow. Record expected outcomes, actual results, commands/manual steps and relevant corrections/reruns. |
| User feedback | One willing person tries a realistic task. Record their user role, the task, one concrete observation and the change—or reason for no change—it led to. A suitable classmate or clearly identified proxy is sufficient. A proxy is someone who tries the task from the intended user’s perspective when an actual user is unavailable. No survey or research report is required. |
| Individual contributions and decisions | Add a **Member contributions** section to the shared EVIDENCE.md. Each student writes a short entry under their own name describing their technical work, supporting references and one decision they made. Use the member-entry structure in the template below. No separate file per student is required. |
| AI use | Record the tools used and how they helped. |

Write expected outcomes **before asking AI to generate test code**. Inspect assertions and run the checks yourself. When an action is rejected, check that it does not make unintended changes to stored data. Check access rules if the application has private data or staff-only actions. Use controlled inputs where time or randomness affects the result. Add checks if important behaviour remains unsupported; a test count alone does not establish correctness.

**EVIDENCE.md template**

This records what you actually checked, decided and learned. Repeat the check and member-entry sections as needed. Fill entries as the work happens; leave future stages clearly marked as pending rather than inventing results.

```markdown
# Development evidence

## Behaviour checks
### [Check name]
- Behaviour being checked: [rule or user task]
- Expected outcome, written before AI-generated test code: [concrete result]
- Test reference and command, or manual steps: [how to repeat the check]
- Actual result: [what happened]
- Correction and rerun, if needed: [change and subsequent result]

## Member contributions
### [Student name — each member writes their own entry]
- My technical contribution: [what I implemented, tested, debugged or integrated]
- References: [relevant code, tests or commits; identify your part in any shared work]
- What I inspected: [part of my work or an AI suggestion I reviewed]
- My decision and reason: [what I accepted, corrected, rejected or changed; why]
- Supporting evidence: [check or observation supporting that decision]

## AI use
- Tools used: [names]
- How they helped: [tasks they supported]

## User feedback
- User role: [intended user or clearly identified proxy]
- Task attempted: [realistic task]
- Observation: [what happened during usage]
- Response: [change made, or reason no change was needed]

## Checkpoint update
[Pending. Complete this section using the checkpoint instructions when released.]

## Final status
- What works: [completed behaviour and links to supporting checks]
- What remains unfinished: [behaviour and limitations]
- What user feedback revealed: [brief takeaway or link to the entry above]
- What we would improve next: [priorities]
```

A review decision may accept code as correct when you explain the evidence supporting it.

**Individual technical contribution is mandatory.** Each member must contribute through implementation, debugging, testing or integration and be able to explain their work. Contributions need not be identical or exactly equal, but everyone is expected to make a comparable effort. The lecturer will check GitHub history alongside the named entries in EVIDENCE.md and the individual defence. Identify each person’s role in shared work so contributions remain traceable.

**Reuse evidence:** A checkpoint decision may also count as a member’s personal entry. Link to the same entry rather than repeating it.

Distinguish **verification** (does the software meet its specified behaviour?) from **validation** (does the workflow help its intended user?). A simulated payment or parking feed does not establish that the corresponding real-world integration works.

**Submission:** No separate evidence report. Keep these records in your repository. The forthcoming checkpoint instructions will specify the smaller portion required earlier.

## 5. Final submission — 6 December, 23:59

**Expected work:** Submit the application, tests, four working documents and small sample data needed to run it. Include test-account instructions where relevant. Do not publish real credentials, API keys or private participant information. Credit external code, assets and sources.

**Format:** Update README.md so someone else can run the project. Add a short **Final status** section to EVIDENCE.md stating what works, the supporting evidence, unfinished behaviour, what user feedback revealed and what you would improve next. Include the records listed in section 4; link to earlier entries instead of repeating them.

**Submission:** One member posts the **repository URL, full commit hash and link to the Final status section in EVIDENCE.md at that commit** in Classroom. No separate report or PDF is required. Keep later changes in later commits.

**Assessment:** The final product and demonstration share one mark out of 100, scaled to 30% of the course grade; see the rubric at the end of this document. You may continue developing after the defence and demonstration until this deadline. Clearly identify unfinished behaviour. You can still earn credit for working parts, useful tests and sound reasoning; incomplete features are assessed as incomplete.

Keep your named contribution entry current as you work. An earlier defence does not require an earlier finished product; final development evidence is also considered.

## 6. AI use and academic responsibility

GitHub Copilot, Claude Code and Claude chat are permitted for planning, implementation, test code, debugging and routine documentation. No paid upgrade is required; no particular model or interface earns extra marks. Report access problems early.

Your expected outcomes, personal decision explanations, user-feedback observations and completion judgments must be your own. AI may help explain concepts or provide a blank structure, but must not supply these judgments or observations for you. Do not report checks or results that did not occur. Read generated changes and run the checks yourself.

Collaborate within your team and identify individual contributions. **Do not plagiarise**, including from other teams. Cite borrowed code, assets and ideas. Earlier assignments retain their own AI policies.

## 7. Final team-product and demonstration rubric

**100 points, scaled to 30% of the course grade.** Team members share this mark. The demonstration is included here, not graded as an additional course component.

**Individual assessment (25%) is separate.** The lecturer will use fair, evidence-based judgment to assess each student’s technical contribution, effort and understanding, considering the nature and difficulty of their work. GitHub history, contribution records and the defence support that judgment; commit counts or lines of code alone do not determine marks. The detailed individual rubric will accompany the defence guidance.

Full marks are available for a modest, coherent prototype. An unfinished feature does not automatically remove credit for useful tests or an accurate explanation of its limitations.

Each rubric row is assessed from **4 to 0**. Row points = level ÷ 4 × row maximum.

| Criterion | Maximum | 4 — Strong | 3 — Competent | 2 — Partial | 1 — Weak | 0 — Missing |
|---|---:|---|---|---|---|---|
| Core features and workflow | 30 | A coherent small product delivers its agreed core workflow and important behaviours. A basic interface and simulated integrations are sufficient. | Core workflow works with minor defects or omissions. | Useful parts work, but important agreed behaviour or integration is incomplete. | Major core behaviours are missing or broken. | No meaningful assessable product. |
| Testing, user feedback and completion claims | 20 | Relevant, independently reasoned checks and actual results support completion claims; important defects are addressed, and limits and user/proxy feedback are explained. | Useful evidence supports most important claims, with minor gaps. | Meaningful evidence exists, but important rules, outcomes or completion claims remain unsupported. | Mostly superficial checks or unsupported claims of success. | No credible checking/completion evidence. |
| Engineering quality and integration | 15 | Code is understandable, reasonably structured and integrated; setup, necessary persistence and sample data are reproducible. | Generally sound with minor structure/setup/integration problems. | Useful implementation with noticeable fragility or setup/integration gaps. | Hard to run or understand; substantial integration problems. | No assessable engineering quality. |
| AI supervision and engineering decisions | 20 | Specific human decisions show understanding of AI suggestions, sensible scope and evidence-based acceptance/correction; concise explanations are sufficient. | Credible oversight and decisions with minor gaps. | Some sound judgment, but important decisions are weakly supported. | Little meaningful oversight or mostly generic explanations. | No credible judgment evidence. |
| Demonstration and delivery | 15 | Clearly demonstrates the core workflow and relevant check, explains learning/limits, and provides a usable repository handover. A simple presentation is sufficient. | Clear demonstration/handover with minor gaps. | Understandable demonstration, but important behaviour or delivery information is unclear. | Difficult to follow or materially incomplete demonstration/handover. | No assessable demonstration or delivery. |
