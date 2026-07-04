# OT Meets IT — Episode 3: Prompt to PLC

## About This Project

This repository is the companion project for **OT Meets IT Episode 3 — Prompt to PLC**,
demonstrating an AI-assisted PLC development workflow using Claude Code, CodeSys, and Git.

The workflow takes a plain-language description of what you want to build, collaborates with
you to produce a Software Functional Requirements document, generates validated IEC 61131-3
Structured Text code, and writes it into a CodeSys project file — all driven by an AI coding
agent, entirely on your local machine.

---

## How to Use This Repository

### Prerequisites
- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- CodeSys V3.5 installed with the CodeSys MCP configured
- Git installed locally
- The `new-codesys-project` skill installed at `~/.claude/skills/new-codesys-project/`
  (bootstraps new projects from this template — see "Using This as a Template" below)

### Getting Started

1. Create an empty directory named after your new project and `cd` into it:
   ```bash
   mkdir my-new-project && cd my-new-project
   ```

2. Start Claude Code there:
   ```bash
   claude
   ```

3. Run the bootstrap skill:
   ```
   /new-codesys-project
   ```
   This clones this template's files into the current directory and sets it up as a fresh,
   independent, **local-only** git repo — no GitHub account or remote required.

4. Claude Code will automatically read the new `CLAUDE.md` and initialize the workflow
   (Phase 0).

5. Describe what you want to build when asked (Phase 1) and work through the workflow with
   the agent.

---

## Repository Structure

```
/my-new-project/
├── CLAUDE.md                  ← AI agent workflow instructions (auto-read by Claude Code)
├── .gitignore                 ← excludes generated project files and IDE artifacts
├── README.md                  ← this file
├── /sfr/                      ← generated SFR documents
├── /code/                     ← generated declaration and program files
└── /project/                  ← CodeSys project files (working copies gitignored)
```

---

## Using This as a Template

This repo (`Prompt-to-PLC`) is the reusable template. Each new PLC project gets its own
independent, local-only git repo bootstrapped from it via the `/new-codesys-project` skill
(see "Getting Started" above) — no GitHub repo or remote is created, and new projects are
never added as another topic here.

### Updating the Template

Since a new project's repo is detached from this template at creation time, future
improvements made here (e.g. edits to `CLAUDE.md`) don't automatically appear in projects
already bootstrapped from it. To pull in an update:

```bash
# from inside an existing project repo
git remote add template https://github.com/OTmeetsIT/Prompt-to-PLC.git
git fetch template
git checkout template/main -- CLAUDE.md README.md
git commit -m "chore: sync CLAUDE.md/README.md from template"
git remote remove template
```

This pulls specific files from the template's history without merging its unrelated commit
history or touching your project's `/sfr/`, `/code/`, or `/project/` contents.

### Publishing a Project to GitHub (Optional)

Projects created from this template are local-only by default. If you later want to back a
project up or collaborate on it, add a remote and push whenever you're ready:

```bash
git remote add origin <your-new-repo-url>
git push -u origin main
```

---

## What Gets Committed

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
