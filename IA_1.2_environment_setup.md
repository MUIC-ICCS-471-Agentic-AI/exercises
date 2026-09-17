# Assignment 2 — Set Up and Verify Your Development Environment

## Assignment Type

Individual setup exercise. **Formative; 10-point rubric for feedback.**

## Purpose and duration

Set up the tools you will use throughout ICCS471, then provide **actual evidence from your computer** that Git, Python 3.12 through `uv`, a small `uv` project, VS Code, and GitHub Copilot Agent are ready. This assignment checks the environment; later assignments provide their own repository and development workflows.

Start during the class setup period. Allow **45–60 minutes total**, depending on downloads, and finish at home if needed. Complete **Assignment 1 (the no-AI time capsule) before opening Copilot** so that your baseline answers remain your own.

These are **Windows 10/11 (64-bit) instructions**. Mac/Linux students should install the same tools and adapt the commands to their operating system. If you already have a tool, keep it if it passes the checks below.

> **Commands:** Use Windows **PowerShell**, opened from Start or from **Terminal → New Terminal** in VS Code. Select PowerShell if VS Code opens a different shell. Copy only the commands inside code blocks, press Enter, and wait for each to finish. Do not type a displayed `PS>` prompt.

## What you need to demonstrate

| Component | Success condition |
| --- | --- |
| Personal GitHub account | You can sign in and use the **same account** in VS Code |
| VS Code and GitHub Copilot | VS Code opens; **GitHub Copilot** and its **Copilot Chat** companion are installed/active |
| Git | `git --version` prints a version |
| `uv` and Python | `uv --version` prints a version; `uv` runs **Python 3.12.x** |
| Your own practice `uv` project | `uv sync` succeeds and `uv run python ...` works inside the project |
| Copilot | A **local Copilot → Agent** request works in VS Code |

**Copilot Free is enough to begin.** A paid Copilot Pro subscription and GitHub Education approval are not prerequisites. Apply for the student benefit using the later section, but the approval decision is outside your control and is **not graded** here.

## Part 1 — Install and sign in

### 1. GitHub personal account

1. Visit [github.com](https://github.com/) and sign in to your personal account, or create one and verify its email address.
2. Open the profile menu at the upper right and note the signed-in username. Use **this same account** for Copilot and GitHub Education. Do not make a second course account if your existing personal account works.

### 2. VS Code and extensions

1. Install **VS Code Stable for Windows** from the [official download page](https://code.visualstudio.com/download). The normal **User Installer** is appropriate for most students.
2. Open VS Code. Select **Extensions** on the left, or press `Ctrl+Shift+X`. Search for **GitHub Copilot**, published by **GitHub**, and install it if VS Code has not already installed/enabled it during Copilot setup. Confirm that **GitHub Copilot Chat** is also installed and enabled; it is the companion that supplies Chat and the agent workflow. VS Code may add both during sign-in, so check before installing anything twice.

The **Python** extension from Microsoft is recommended for interpreter selection and Python editing, but it is **not required** for the Agent exercise or this assignment's grade. You do not need **Pylance** or the **Ruff VS Code extension**. A later exercise may run Ruff or pytest as project tools through `uv run`.

### 3. Git for Windows

1. Install [Git for Windows](https://git-scm.com/download/win) using its usual defaults, including availability from the command line and other software.
2. Close existing PowerShell and VS Code terminal windows. Open a new PowerShell and run:

   ```powershell
   git --version
   ```

   **Expected:** `git version` followed by a version number.

### 4. `uv` and Python 3.12

`uv` manages the Python version for the course. You do **not** need a separate Python 3.12 installer from python.org or a change to your Windows default Python.

1. Run the [official `uv` Windows installer](https://docs.astral.sh/uv/getting-started/installation/) in PowerShell:

   ```powershell
   powershell -ExecutionPolicy Bypass -c "irm https://astral.sh/uv/install.ps1 | iex"
   ```

   Wait for it to finish. This command changes execution policy for the installer process, not your permanent settings.
2. Close PowerShell and VS Code terminals. Open a fresh PowerShell and run the following **one line at a time**:

   ```powershell
   uv --version
   uv python install 3.12
   uv run --no-project --python 3.12 python --version
   ```

   **Expected:** a `uv` version and `Python 3.12.` followed by a patch number. A different result from plain `python --version` does not matter; use `uv` commands for this course.

### 5. Copilot Free and Agent mode

1. In VS Code, select the Copilot icon in the status bar and **Use AI Features**. If the control has moved, open **Chat** and follow its **Set up Copilot** or **Sign in** prompt.
2. Choose **Sign in with GitHub**. Authorize using the account from Step 1, then return to VS Code. Choose **Copilot Free** if offered. An existing Copilot Student or other active plan on the same account also works.
3. In Chat, select the **Copilot** *local session target* and **Agent** as the agent/mode. Choose **Auto** for the model and **Manual** for permissions if asked. The placement of these controls can vary by VS Code version. If Chat or Agent is missing, revisit **Extensions** and confirm that **GitHub Copilot Chat** is enabled, then restart/update VS Code Stable.

A visible Agent option is useful, but the short request in Part 2 confirms that it actually works. If Copilot asks you to pay, reports an access restriction, or says your allowance is exhausted, keep the exact message and contact the instructor. **Do not buy a plan for this assignment.**

## Part 2 — Create a practice project and verify the setup

This is a **new, separate practice project**. Do not run `uv init` inside any instructor-provided repository.

1. Open PowerShell. From your user folder, create and enter the project. Run **one line at a time**:

   ```powershell
   cd $env:USERPROFILE
   uv init --no-package --python 3.12 ICCS471_uv_practice
   cd ICCS471_uv_practice
   uv sync
   ```

   If a folder named `ICCS471_uv_practice` already exists, choose a different unused name in **both** the `uv init` and `cd` commands. `--no-package` keeps this example a simple application. `uv sync` creates its local `.venv` environment.
2. In that project folder, run these readiness commands and **retain the input commands and their actual outputs**:

   ```powershell
   git --version
   uv --version
   uv run python --version
   uv run python -c "print('ICCS471 setup OK')"
   ```

   **Expected:** Git and `uv` version numbers, `Python 3.12.x`, and `ICCS471 setup OK`.
3. In VS Code select **File → Open Folder** and open `ICCS471_uv_practice`. If you chose to install the optional Microsoft Python extension and want editor support, press `Ctrl+Shift+P`, run **Python: Select Interpreter**, and select the interpreter in the project's `.venv`. On Windows its path ends in `.venv\Scripts\python.exe`. If it does not appear, reopen the picker after `uv sync`. The terminal checks work without this extension.
4. Open **Chat** in this project with **Copilot → Agent** selected. Send **one small, read-only request**:

   > Inspect this project without editing files or running terminal commands. What Python version is selected in `.python-version`, and what file declares the project's Python requirement?

   Check its answer against `.python-version` and `pyproject.toml` yourself. It should identify `3.12` and `pyproject.toml`. The purpose is to confirm that your account can actually run a local Agent request, **not** to grade the quality of the answer. Stop it if it tries to make changes.

For later projects, `pyproject.toml` declares project requirements and dependencies; `.python-version` selects the project's default Python version; `uv.lock` records resolved dependencies; and `.venv` holds the local environment. Run `uv run ...` from the **project root**. An assignment will tell you when to use `uv add PACKAGE_NAME` or `uv python pin 3.12`; do not change an instructor project just to make this practice check pass.

## Part 3 — Request the student Copilot benefit

GitHub currently calls the verified-student plan **Copilot Student** (sometimes described informally as “Copilot Pro for students”). GitHub Education verification and Copilot activation are separate steps. **Submit an application if eligible; approval and activation are not required by this assignment's deadline.** If you cannot submit it, record the actual blocker and your next action.

1. With the **same personal GitHub account**, visit [GitHub Education benefits](https://github.com/settings/education/benefits). Under GitHub Education select **Start an application**, complete the form, and submit it. If GitHub requests an academic email, add and verify your university email in [GitHub email settings](https://github.com/settings/emails) first. Follow GitHub's instructions for proof of current enrollment.
2. Check your application status at the Education benefits page. If you are already verified, you do not need to apply again.
3. **After approval**, return to the benefits page. Under **Free GitHub developer resources for students and teachers**, select **Learn more** and follow the prompts to activate **Copilot Student**. Check the plan in [Copilot settings](https://github.com/settings/copilot) and sign back into VS Code if needed.

The benefit may take **several days** after verification to appear. If only paid checkout is shown, do not purchase it; follow [GitHub's student troubleshooting guidance](https://docs.github.com/en/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-students). **Do not put proof-of-enrollment documents, your academic email address, or an Education application screenshot in your assignment evidence.** You only need to state your status in words: *already verified*, *application submitted/pending*, or *blocked* (brief reason and next action).

## Submission Requirements

Submit **one PDF** to the **Assignment 2** post in Google Classroom by its displayed deadline. Create a document containing your full name, student ID, and the following evidence, then export it as PDF:

1. **Terminal/PowerShell evidence:** Provide the **commands and actual outputs** from Part 2, Step 2. You may use **screenshots of your terminal, a copied text transcript, or both**. The four commands and their outputs must be legible and identifiable; do not submit only isolated version numbers. Include a line stating whether `uv sync` succeeded (you may also show its output).
2. **VS Code evidence:** A screenshot showing **GitHub Copilot / GitHub Copilot Chat** installed or enabled, and a screenshot of the **Copilot local Agent conversation** after the read-only request. You may place both on one PDF page if readable. The conversation should show the selected **Agent** mode and the returned answer. Your GitHub username may be obscured if you wish. No screenshot of the optional Python extension is required.
3. **Student benefit status:** One sentence using one of the status descriptions in Part 3. No verification document or approval screenshot is needed.
4. **Any blocker:** If a check failed, show the command and exact error or a screenshot, and state which steps you completed. Submit partial evidence instead of inventing a successful output.

Filename: `ICCS471_EnvironmentSetup_[FirstName]_[FirstThreeLettersOfLastName].pdf`  
Example for **Narin Sombat**: `ICCS471_EnvironmentSetup_Narin_Som.pdf`

**AI policy:** You may use Copilot or other AI to troubleshoot installation, but the submitted evidence must come from **your own machine and account**. Do not fabricate command output, screenshots, account status, or a successful Agent request. Do not share passwords, access tokens, private files, or other people's information with an AI tool or in the submission.

## Rubric — 10 points

| Criterion | Excellent | Good | Satisfactory | Not Acceptable / No Submission |
| --- | --- | --- | --- | --- |
| **Git and `uv` readiness (2 pts)** | **2:** Both version commands and actual outputs are legible. | **1.5:** Both tools work; one output is incomplete. | **1:** One tool works or is clearly evidenced. | **0–0.5:** Neither is established. |
| **Python 3.12 project (3 pts)** | **3:** `uv sync`, Python 3.12, and the print check all succeed in the new project. | **2:** Project runs with 3.12; one check is missing. | **1:** Some project setup works, but the version or run check is missing or fails. | **0:** No usable project evidence. |
| **VS Code and Copilot Agent (3 pts)** | **3:** Copilot Chat is enabled; a local Agent request returns in the project. | **2:** Copilot Chat is enabled; Agent request is blocked with an exact error. | **1:** Copilot installation is shown, but Agent access is not established. | **0:** Neither is evidenced. |
| **Evidence and submission (2 pts)** | **2:** Clear commands/results, correct PDF and student details; benefit status or specific blocker is reported without private documents. | **1.5:** Fully assessable with one minor omission. | **1:** Several gaps, but the setup can still be assessed. | **0–0.5:** Evidence is missing, unreliable, or cannot be assessed. |

**Maximum: 10 points.**

The rubric measures **verified setup**, not whether GitHub has approved the student benefit by the deadline. If an external access restriction blocks you, submit the exact error for review; do not pay or fabricate a result.

## Troubleshooting

| Symptom | First action |
| --- | --- |
| `git` or `uv` is “not recognized” | Close and reopen both VS Code and PowerShell, then retry. If needed, rerun the installer and check its command-line/PATH choice or reported install location. |
| Plain `python` opens Microsoft Store or shows another version | Use `uv run --no-project --python 3.12 python --version` for general setup, and `uv run python --version` inside the practice project. |
| `uv` cannot download Python or packages | Check the connection, retry, and try another network if the current one blocks it. Preserve the full error. |
| `uv sync` cannot find `pyproject.toml` | Run `pwd`; enter the practice project folder containing `pyproject.toml` and retry. |
| VS Code selects the wrong interpreter (optional Python extension) | Run `uv sync`, then select `.venv\Scripts\python.exe` via **Python: Select Interpreter**. Terminal `uv run` commands do not depend on this selection. |
| Copilot Agent is missing or the request fails | Check that **GitHub Copilot Chat** is enabled; restart/update VS Code Stable, verify the GitHub account, select the local **Copilot** target and **Agent**, and record the exact access/allowance message. |
| Education is approved but Copilot Student is absent | Revisit Education benefits and select **Learn more**; activation may lag approval by several days. Do not complete a paid checkout. |

If you need help, give the instructor the **step**, **command or screen**, **complete error**, and **Windows version**. Never send a password, token, or student verification document.

## Official References

| Topic | Documentation |
| --- | --- |
| VS Code | [Download](https://code.visualstudio.com/download); [Copilot setup](https://code.visualstudio.com/docs/setup/copilot); [GitHub Copilot extension](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot); [Copilot Chat companion](https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat); [agents in VS Code](https://code.visualstudio.com/docs/agents/overview); [optional Python extension guide](https://code.visualstudio.com/docs/python/python-tutorial) |
| GitHub Education | [Apply as a student](https://docs.github.com/en/education/about-github-education/github-education-for-students/apply-to-github-education-as-a-student); [Education benefits](https://github.com/settings/education/benefits) |
| Copilot | [Activate Copilot Student](https://docs.github.com/en/copilot/how-tos/copilot-on-github/set-up-copilot/enable-copilot/set-up-for-students); [start Copilot Free](https://docs.github.com/en/copilot/how-tos/manage-your-account/get-started-with-a-copilot-plan); [plan features](https://docs.github.com/en/copilot/get-started/plans) |
| Git | [Git for Windows](https://git-scm.com/download/win) |
| `uv` | [Installation](https://docs.astral.sh/uv/getting-started/installation/); [Python installation](https://docs.astral.sh/uv/guides/install-python/); [projects](https://docs.astral.sh/uv/guides/projects/); [Python version files](https://docs.astral.sh/uv/concepts/python-versions/) |
| Python 3.12 | [Python 3.12.14 release page](https://www.python.org/downloads/release/python-31214/) — explains why recent Python 3.12 releases have no python.org binary installer. |
