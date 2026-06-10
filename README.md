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

1. Clone this repository:
   ```bash
   git clone https://github.com/OTmeetsIT/PLC_AI_traffic_light.git
   cd PLC_AI_traffic_light
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
/PLC_AI_traffic_light/
├── CLAUDE.md                  ← AI agent workflow instructions (auto-read by Claude Code)
├── .gitignore                 ← excludes generated project files and IDE artifacts
├── README.md                  ← this file
├── /sfr/                      ← generated SFR documents
├── /code/                     ← generated declaration and program files
└── /project/                  ← CodeSys project files (working copies gitignored)
```

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
