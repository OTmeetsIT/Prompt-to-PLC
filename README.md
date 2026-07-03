# OT Meets IT — Episode 3: Prompt to PLC

## About This Project

This repository is the companion project for **OT Meets IT Episode 3 — Prompt to PLC**,
demonstrating an AI-assisted PLC development workflow using Claude Code, CodeSys, and GitHub.

The workflow takes a plain-language topic, generates a full Software Functional Requirements
document, produces validated IEC 61131-3 Structured Text code, and writes it into a
CodeSys project file — all driven by an AI coding agent.

---

## How to Use This Repository

### Prerequisites
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- CodeSys V3.5 installed with the CodeSys MCP configured
- Git configured with access to this repository
- The `Template_750_8111.project` file present in `/project/`

### Getting Started

1. Create a new repository from this template (see "Using This as a Template" below),
   then clone it:
   ```bash
   git clone https://github.com/OTmeetsIT/<your-new-repo>.git
   cd <your-new-repo>
   ```

2. Open Claude Code in the project directory:
   ```bash
   claude
   ```

3. Claude Code will automatically read `CLAUDE.md` and initialize the workflow.

4. Provide your SFR topic when prompted and let the agent run the workflow.

---

## Repository Structure

```
/<your-new-repo>/
├── CLAUDE.md                  ← AI agent workflow instructions (auto-read by Claude Code)
├── .gitignore                 ← excludes generated project files and IDE artifacts
├── README.md                  ← this file
├── /sfr/                      ← generated SFR documents
├── /code/                     ← generated declaration and program files
└── /project/                  ← CodeSys project files (working copies gitignored)
```

---

## Using This as a Template

This repo (`Prompt-to-PLC`) is the reusable template. Each new PLC project should live in
its own repository created from it, rather than being added as another topic here.

1. On GitHub, mark this repo as a template: **Settings → General → Template repository**
   (check the box). This only needs to be done once.
2. For each new project, create a fresh repo from the template:
   - Via the GitHub UI: click **Use this template → Create a new repository** on this repo's page.
   - Via the CLI: `gh repo create <new-project-name> --template OTmeetsIT/Prompt-to-PLC --clone`
3. `Template_750_8111.project` and the directory structure come with the new repo automatically.
4. Clone the new repo and start a Claude Code session there — one topic per repo.

### Updating the Template

GitHub template repos are a **one-time copy**, not a linked fork — improvements made here
(e.g. edits to `CLAUDE.md`) do **not** propagate automatically to repos already created from
this template. To pull in an update:

```bash
# from inside an existing project repo
git remote add template https://github.com/OTmeetsIT/Prompt-to-PLC.git
git fetch template
git checkout template/main -- CLAUDE.md README.md
git commit -m "chore: sync CLAUDE.md/README.md from template"
```

This pulls specific files from the template's history without merging its unrelated commit
history or touching your project's `/sfr/`, `/code/`, or `/project/` contents.

---

## What Gets Committed to GitHub

| File | Committed? |
|---|---|
| `CLAUDE.md` | Yes |
| `README.md` | Yes |
| `.gitignore` | Yes |
| `sfr/{topic}_SFR.md` | Yes |
| `code/{topic}_declaration.txt` | Yes |
| `code/{topic}_program.txt` | Yes |
| `project/Template_750_8111.project` | Yes |
| `project/{topic}_v1.project` | **No** (gitignored) |
| `project/*.opt` | **No** (gitignored) |

The text files are the source of truth. The project file is a build artifact.

---

## Video Series

- **Episode 1** — Introduction to OT Meets IT concepts
- **Episode 2** — Setting up the environment and tools
- **Episode 3** — Prompt to PLC: AI-assisted PLC development workflow (this repo)
