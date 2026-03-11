# AGENTS.md — AI4CM Repository

## Project Overview

**AI4CM** (Artificial Intelligence for Communication and Marketing) is a course repository for data science exercises using Python. It provides a pre-configured Conda/Mamba environment and Jupyter notebooks for hands-on practice.

## Repository Structure

```
ai4cm/
├── environment.yml          # Mamba environment definition
├── README.md                # Student-facing setup guide
├── AGENT.md                 # This file
├── setup/
│   ├── test_notebook.ipynb  # Environment verification notebook
│   ├── test_script.py       # Environment verification Python script
│   └── test_data.csv        # Sample CSV used by the tests
├── quick-guide/
│   ├── git.md               # Mini guide: Git commands
│   └── terminal.md          # Mini guide: Terminal (bash/zsh and PowerShell)
├── 01-lesson/
│   └── {model-name}.ipynb   # Lesson 1 exercise notebooks
├── 02-lesson/
│   └── {model-name}.ipynb   # Lesson 2 exercise notebooks
└── ...                      # One directory per lesson
```

## Environment

The project uses a **Mamba/Conda** environment managed via `environment.yml`.

- **Environment name**: `ai4cm-env`
- **Python version**: 3.14
- **Key dependencies**: `numpy`, `pandas`, `matplotlib`, `scikit-learn`, `seaborn`, `duckdb`, `ipykernel`
- **Channel**: `conda-forge`

### Create / activate the environment

```bash
# Create (first time)
mamba env create -f environment.yml

# Activate
mamba activate ai4cm-env

# Update after changes to environment.yml
mamba env update -f environment.yml --prune
```

### Run a script directly (without activating first)

```bash
mamba run -n ai4cm-env python setup/test_script.py
```

## Conventions

- All notebooks (`.ipynb`) and scripts (`.py`) are intended to be run with the `ai4cm-env` kernel/interpreter.
- The `setup/` folder contains **verification files** used to confirm the environment is working correctly — do not delete them.
- The `quick-guide/` folder contains **student-facing markdown guides** (Git, terminal basics). Keep these beginner-friendly and OS-agnostic where possible.
- Documentation lives in `README.md` (main setup guide for students) and the `quick-guide/` files. Prefer markdown for all explanatory content.
- Use `mamba` (not `conda`) for all package management commands to keep consistency with the toolchain.

## Editor Configuration

A `.vscode/` folder is included with recommended settings. When opening the project in VS Code or Antigravity, accept the prompt to install recommended extensions (Python, Jupyter).

Select the **`ai4cm-env`** kernel when working with notebooks:

- Top-right corner → **Select Kernel** → `ai4cm-env`

## Adding Exercises

Each lesson's exercises live in a dedicated top-level directory named after the lesson number:

```
{number}-lesson/
└── {analysis-name}.ipynb
```

**Convention:**

- `{number}` — zero-padded lesson number (e.g. `01`, `02`, `10`)
- `{analysis-name}` — short, lowercase, hyphen-separated description of the notebook's topic (e.g. `linear-regression`, `data-exploration`)

**Example** — adding the first lesson on linear regression:

```bash
mkdir 01-lesson
touch 01-lesson/linear-regression.ipynb
```

Keep one notebook per topic/model within a lesson folder. If a lesson covers multiple topics, add one notebook per topic:

```
02-lesson/
├── decision-tree.ipynb
└── random-forest.ipynb
```

All notebooks should use the `ai4cm-env` kernel (see [Editor Configuration](#editor-configuration) above).

# Test and verify

After any edit or create a new notebook file, check if the definition is a valid json.
