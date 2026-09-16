# Project Log

This log records what was done, how it was tested, what happened, and what the next small step is. Keep entries short and factual. It does not need to be polished.

## 2026-09-13 - Local Git setup

Goal:
Set up local version control for the project and save the initial planning documents.

What I changed:
- Initialized the project as a local Git repository.
- Renamed the default branch to `main`.
- Added `README.md`, `.gitignore`, and `docs/references.md`.
- Added the project plan in Markdown and Word formats.
- Created the first commit: `docs: add initial project plan`.

Test performed:
- Ran `git status` to confirm the working tree was clean after the commit.

Expected result:
The project should be tracked locally by Git with all initial files committed.

Actual result:
The project is now tracked locally on the `main` branch.

Problem and diagnosis:
- The GitHub remote repository has not been created or connected yet.
- The project exists only locally for now.

Next smallest step:
Create a private GitHub repository and push the local `main` branch.

---

## 2026-09-16 - GitHub setup and hardware research

Goal:
Create a private GitHub backup and collect reliable references for the planned
breadboard-to-FPGA build.

What I changed:
- Created the private GitHub repository
  `haoting-qiu/breadboard-to-fpga-8bit-cpu` and connected it as `origin`.
- Pushed the local `main` branch to GitHub.
- Added official datasheets for the identified 74LS/74HC devices, AT28C16,
  NE555, and Arduino Nano.
- Added official Tang Nano 9K, GOWIN EDA, and Logisim-evolution resources.
- Transcribed the seller's component list into `docs/kit-inventory.md`.
- Compared the two candidate kits against the available tutorials and parts
  lists. The final purchase has not yet been recorded.

Test performed:
- Checked the Git remote address and confirmed that `main` pushed successfully.
- Confirmed that the repository was synchronized after the documentation
  commits.
- Used manufacturer or project-maintainer pages for the references that could
  be identified confidently.

Expected result:
The project should have an off-device private backup and a traceable starting
point for checking components and technical information.

Actual result:
The private GitHub repository is synchronized, and the known hardware and tool
references are documented.

Problem and diagnosis:
- The exact kit product page and tutorial link have not yet been recorded.
- The manufacturer and complete marking of the listed `74LS219` are unknown,
  so no datasheet was assigned to it.
- Seller quantities and part markings cannot be verified until the package
  arrives.

Next smallest step:
After choosing the kit, save its product/tutorial link and purchase manifest in
the repository.

---

## Template

Copy this block for each new work session.

```markdown
## YYYY-MM-DD - Short session title

Goal:
What was the one main thing I wanted to accomplish?

What I changed:
- What did I build, edit, wire, test, read, or document?
- Keep this factual and specific.

Test performed:
- What did I do to check whether it worked?
- Include commands, measurements, inputs, expected outputs, or observations when useful.

Expected result:
What did I expect to happen?

Actual result:
What actually happened?

Problem and diagnosis:
- What went wrong?
- What do I think caused it?
- What evidence supports that guess?

Next smallest step:
What is the next action that should take 30 minutes or less?
```
