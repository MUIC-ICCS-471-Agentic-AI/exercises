# Assignment 1.4 — Booking Lab Evidence Record

## Assignment Type

Individual, formative written record based on **Assignment 1.3 — First Controlled Agentic Workflow: Room Booking**. **5-point rubric for feedback; this is not a separate percentage of the course grade.**

Allow approximately **15–20 minutes after working on Assignment 1.3**. Create a Markdown file named **`EVIDENCE.md` in the root of your own Assignment 1.3 repository**. Submit a direct link to that file.

## Purpose and task

Assignment 1.3 produces the code and tests. Here you account for your own decisions and checks: what you asked for, what you accepted or corrected, what the evidence supports, and what remains uncertain. Use the structure below closely. Write **approximately 200–350 words of your own answers in total**, excluding headings, prompts, and identifying details.

### Copy this template into `EVIDENCE.md`

Replace **every bracketed prompt** with your own account. Do not keep whatever are in the brackets. Keep the headings and the claim → evidence structure. Remove the bracketed instructions before publishing. Do not leave blank sections.

```markdown
# Booking Lab Evidence Record

**Name:** [Your full name]
**Student ID:** [Your student ID]
**Repository:** [Link to your own public booking-lab repository]

## Goal
[What booking behavior were you asked to change?]

## Constraints / Out of Scope
[Which code and test files could you change? What behavior had to remain intact?]

## Key Decision and Agent Claim
[Describe one part of Copilot's plan or implementation you checked and deliberately accepted, revised, or rejected. Why? If you made no correction, explain a choice you consciously accepted.]

[State one concrete claim Copilot made about the repository or its work. What file, code, or result did you inspect to check it? Was the claim accurate?]

## Verification: Claim → Evidence
- **Claim:** [What specific behavior did you want to establish?]
- **Command or test I ran:** [Give the actual command or test.]
- **Actual result:** [What happened, including a failure and subsequent correction if relevant?]
- **What this supports:** [What does this result give you reason to believe?]

## Manual Validation
[What happened when you personally ran demo.py? What did it show beyond the original four baseline tests?]

## Remaining Uncertainty
[Name one plausible booking case, limitation, or risk that your checks did not fully establish.]
```

You may consult your code, terminal history, and Copilot conversation while recalling events. **Report what actually happened.** You do not need to invent a rejected plan, failure, or correction. If Assignment 1.3 was blocked, use the same headings to describe how far you got, the exact blocker, which checks you actually ran, and what remains unknown. Never report a command as successful unless you ran it.

Screenshots and a full chat transcript are **not required**. Give concrete file references, commands, and results in your own words.

## AI Policy

**No generative AI assistance for the written answers.** Do not ask Copilot or another AI tool to draft, rewrite, paraphrase, or polish `EVIDENCE.md`. Ordinary spell-check is allowed. You may quote a short agent claim where useful, but your account of what you checked and concluded must be your own.

## Publish and Submit

**In short, create EVIDENCE.md file in your repo from assignment 1.3 and push it to your GitHub repo. Then post the link to the file into your submission private comment**. But here's the long version ->

1. In VS Code, open **your cloned `booking-lab` folder** from Assignment 1.3. Create **`EVIDENCE.md` at the repository root**, alongside `README.md`, rather than inside `booking_app` or `tests`. Paste the template and replace every bracketed prompt with your answers. Save the file.
2. In the VS Code **PowerShell terminal**, check that you are in that repository, then commit and push the file to your own GitHub repository. Run each command separately:

   ```powershell
   git status
   git add EVIDENCE.md
   git commit -m "Add booking lab evidence record"
   git push origin main
   ```

   Before committing, `git status` should show your new `EVIDENCE.md`. If it also shows unexpected code changes, inspect them before proceeding; the commands above add only the evidence file. Assignment 1.3 has already set `origin` to **your own** repository.
3. Open your public repository on GitHub. Select `EVIDENCE.md` on the `main` branch and confirm the complete rendered document is visible. Copy the **direct URL to the file** from your browser. Its form is:

   `https://github.com/YOUR-USERNAME/YOUR-REPOSITORY/blob/main/EVIDENCE.md`

4. Post that **direct file URL** in a **private comment on the Assignment 4 post in Google Classroom** by its displayed deadline. Confirm that the comment appears; if Classroom offers **Mark as done**, use it after posting. Submit the Markdown file link, **not a PDF or the repository home page**.

If you could not create or publish your Assignment 1.3 repository, post your exact blocker in the Assignment 4 private comment and contact the instructor. Do not fabricate a published file.

## Rubric — 5 points

| Criterion | Excellent | Good | Satisfactory | Not Acceptable / No Submission |
| --- | --- | --- | --- | --- |
| **Human judgment and agent claim (2 pts)** | **2:** States the task boundary, explains a real plan or implementation decision, and checks a specific agent claim against an identified source. | **1.5:** Decision and claim check are present, with a minor gap in reasoning or scope. | **1:** Mentions a decision or claim check, but the account is vague or only one is adequately addressed. | **0–0.5:** No meaningful evidence of personal judgment or claim checking. |
| **Verification and validation evidence (2 pts)** | **2:** Links a specific claim to a check personally run and its actual result; distinguishes that evidence from direct demo behavior. | **1.5:** Accurate checks and results, with a minor gap in what they establish. | **1:** Some real checks are reported, but results or their meaning are unclear. | **0–0.5:** Checks are absent, unsupported, or presented as completed without evidence. |
| **Limits and submission (1 pt)** | **1:** Names a credible uncertainty; student-authored `EVIDENCE.md` follows the template, is public and readable, and its direct file link is submitted. | **0.75:** Credible uncertainty and assessable file, with one minor omission. | **0.5:** Limitation or publication details are incomplete, but the record remains assessable. | **0:** No assessable file or material misrepresentation. |

**Maximum: 5 points.**
