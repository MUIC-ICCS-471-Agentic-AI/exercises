# ICCS471 — Individual Assignment: Two Elevators, Different Priorities

**20 points · Individual assignments component · Copilot or Claude permitted**

An eight-floor office building has two elevators. When someone calls an elevator, should the system favour quick pickup, use an existing journey, or avoid delaying people already aboard?

Design a small dispatch policy, justify it with scenarios, and use **two implementation agents and one reviewer** to build and examine it. Different policies can earn full marks. We assess whether your reasoning is coherent and your implementation follows it.

You will implement two functions: `dispatcher.py → choose_elevator(...)` selects an elevator according to your policy; `app.py → run_scenarios(...)` displays the scenarios and decisions. The data structures, eligibility rules and tests are provided.

Allow about **75 minutes**. Use the supplied `elevator_lab` folder. Submit by the deadline in Classroom.

## 1. Think through the policy — 15 minutes

Read SPEC.md and inspect scenarios.py. The building has floors 1–8, with floor 1 as the lobby. Each elevator has a model safety capacity of **8 people × 65 kg = 520 kg**. Scenarios supply a simulated sensor reading, `load_kg`. A car needs room for another assumed 65 kg: `load_kg + 65 <= 520`. Each scenario asks for one decision from a snapshot.

Think about **S1**, then **S2 or S3**. These are independent snapshots, not successive moments in one journey.

| Scenario | Elevator A | Elevator B | New caller | Question to consider |
|---|---|---|---|---|
| **S1 — Passing or idle?** | Floor 8, moving down; load 130 kg; scheduled stop: floor 1. | Floor 4, idle; load 0 kg; no scheduled stops. | Floor 5, wants to go down. | Use A's existing journey or send the nearer B? |
| **S2 — Heavier load** | Floor 8, moving down; load 325 kg; scheduled stop: floor 1. | Floor 4, idle; load 0 kg; no scheduled stops. | Floor 5, wants to go down. | Should A's heavier load affect your preference? |
| **S3 — Stop already scheduled** | Floor 8, moving down; load 130 kg; scheduled stops: floor 5, then floor 1. | Floor 4, idle; load 0 kg; no scheduled stops. | Floor 5, wants to go down. | Does A's existing stop at floor 5 affect your preference? |

Both elevators are eligible in all three cases. Your policy determines which one to select.

Add one valid **S6 scenario of your own** in scenarios.py. Copy an existing `Scenario(...)` entry, rename it S6, and change a meaningful detail such as load, direction or scheduled stops. Keep the five supplied scenarios. Predict the outcome before running it. Your case need not produce a different selection if you can explain why.

Complete **POLICY.md yourself before implementation**: priorities, exact selection rule, tie-breaker and predictions for your three cases. Briefly describe another defensible policy that could choose differently in a scenario. You may ask AI to challenge your ideas, but make and explain your own decisions.

> **Example of justification — one possible priority:** “I prefer using an elevator already travelling past the caller because it avoids activating the idle elevator. I accept an additional stop for passengers aboard. This aims to reduce additional movement; it does not prove lower energy consumption.”
>
> You may choose a different priority. Explain the benefit and the cost of your own choice.

Load divided by 65 estimates occupancy; it does not establish an exact headcount. Eligibility is fixed by SPEC.md and rules.py. Your freedom is choosing **among eligible elevators**. Distance, stops and occupancy can inform your policy; do not present them as measured waiting time or energy savings.

## 2. Plan and delegate — 20 minutes

Create your own GitHub repository and commit the starter and your initial policy before implementation. Fill in PLAN.md; its brackets are prompts for your own short plan.

| Role | Work | Files it may edit |
|---|---|---|
| Dispatcher builder | Implement your policy using the supplied eligibility helper | dispatcher.py |
| Display builder | Present scenarios, call the dispatcher and display the decision/reason | app.py |
| Reviewer | Inspect the combined code and examine policy tradeoffs | Read-only |

Follow the **Start in Copilot or Claude** instructions in PROMPTS.md: open the project folder and chat, confirm your Python command, then paste the delegation prompt. For automatic delegation, check that two actual worker executions appear. For manual coordination, use a separate fresh chat for each role. Give both builders the shared specification, your policy, plan and code. Sequential worker runs are fine. If automatic setup takes more than five minutes, switch to separate sessions. Both routes can earn full marks.

## 3. Integrate, review and experiment — 25 minutes

1. Wait for both builders to finish. If they edited your project directly, inspect those changes; if they worked elsewhere, integrate their two files. Run `python -m unittest -v` using your confirmed Python command (`py` on Windows if needed), and inspect the actual terminal result.
2. Use **PROMPTS.md → Reviewer: after integration**, or its separate-session reviewer prompt, to inspect the **current combined implementation** against SPEC.md and POLICY.md. It should distinguish a coding defect, an inconsistent policy and an accepted tradeoff.
3. Run `python app.py`, substituting your confirmed Python command as above. Compare the actual selections and reasons with your three predictions. Investigate any mismatch. Make or delegate a correction if justified, then rerun the tests and scenarios.
4. Decide whether the outcomes serve your stated priority. Explain one benefit and one cost or limitation using a concrete scenario. A policy can be implemented correctly and still reveal an undesirable tradeoff.

> **Example follow-up to a reviewer:** “You suggest choosing the nearer idle elevator. Check whether that is required by my written policy or is an alternative preference. Identify the relevant rule before recommending a change.”

If review changes your mind about the policy, record why and update the policy and implementation together. Preserve the original reasoning in your commit history or a short evidence note. Do not change a prediction merely to match unexplained code.

The supplied tests enforce shared behaviour, **not a preferred answer for scenarios where both elevators are eligible**. Passing them does not establish that the program follows your own policy; your scenario checks supply that evidence. Keep SPEC.md, models.py, rules.py and test_contract.py unchanged.

## 4. Record and submit — 15 minutes

Complete EVIDENCE.md with short bullets and the three-case results table. Include one brief output excerpt or screenshot for each builder and the reviewer. For automatic workers, show the separate worker runs. Full transcripts are unnecessary.

Commit the checked work. **Submit your GitHub repository link and final commit hash in Classroom.** Include the program, supplied files, completed POLICY.md, PLAN.md, EVIDENCE.md and any linked screenshots. Make the repository accessible to the lecturer.

Your policy reasoning and explanations must be your own. Discussing ideas and setup is allowed; do not plagiarise another student's code or records. AI implementation is permitted and expected. Record incomplete work or remaining uncertainty honestly.

## Rubric — 20 points

| Criterion | 5 — Strong | 4 — Competent | 2–3 — Partial | 1 — Limited | 0 — Missing |
|---|---|---|---|---|---|
| Policy and reasoning | Clear, implementable priorities and tie-breaker; three justified predictions including an original case; a meaningful alternative and explicit tradeoff. | Coherent policy and scenarios with a minor explanation gap. | Useful reasoning, but rules, predictions or tradeoffs have notable gaps or inconsistencies. | Mainly unsupported preferences or vague efficiency claims. | No assessable policy. |
| Delegation and integration | Credible two-builder and separate-reviewer workflow, clear ownership, short plan and an integrated application. | Clear workflow with a minor handoff or recording gap. | Some coordination, but separation, evidence or integration is incomplete. | Little evidence of the intended workflow. | No assessable delegation. |
| Implementation and verification | Shared rules respected; implementation follows the written policy; three predicted/actual outcomes and supplied test results support that conclusion. | Mostly correct implementation with a minor defect or evidence gap. | Substantial work, but important behaviour, policy fidelity or checking is incomplete. | Mostly stubs or unverified claims. | No meaningful implementation or checks. |
| Review judgement and learning | Checks a specific concern and makes a justified decision; uses observed outcomes to assess the policy's benefit/cost and explains one coordination lesson. | Sound reflection with a minor supporting detail missing. | Some relevant judgement, but generic or incompletely supported. | Mainly repeats an AI opinion. | No assessable judgement. |

You do not need to find a defect to earn full marks: a checked no-defect conclusion is valid. Automatic and manually coordinated routes are assessed equally. Marks do not depend on matching the lecturer's preferred policy, using a paid model or adding features.
