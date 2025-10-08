# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is an nbdev project that creates a simple playing card API. nbdev is a literate programming framework where Python code is written in Jupyter notebooks and then exported to Python modules.

**Key Architecture:**
- Source code lives in Jupyter notebooks under `nbs/` directory
- Notebooks are exported to Python modules in `nbdev_card/` directory
- The `nbs/` notebooks are the **source of truth** - edit notebooks, not the generated Python files
- `index.ipynb` generates the README.md file

**Core Components:**
- `nbs/00_card.ipynb` → `nbdev_card/card.py`: Defines the `Card` class with suit and rank
- `nbs/01_deck.ipynb` → `nbdev_card/deck.py`: Defines the `Deck` class with shuffle, pop, remove methods
- `nbs/index.ipynb` → `README.md`: Project documentation

## Development Commands

**Primary workflow:**
```bash
nbdev_prepare  # Export notebooks to Python, run tests, build docs
```

This command runs:
- `nbdev_export`: Convert notebooks to Python modules
- `nbdev_test`: Run tests defined in notebooks
- `nbdev_clean`: Clean notebooks of extraneous metadata
- `nbdev_readme`: Generate README from index.ipynb

**Individual commands:**
```bash
nbdev_export        # Export notebooks to Python modules only
nbdev_test          # Run tests only
nbdev_clean         # Clean notebook metadata
nbdev_preview       # Preview documentation locally
```

## Python Version

This project requires Python 3.9+ (min_python = 3.9 in settings.ini). **Do not use Python 3.14** - it has compatibility issues with fastcore/nbdev dependencies. Use Python 3.10, 3.11, or 3.12.

## Installation

Install in development mode:
```bash
pip install -e .
```

## Important Files

- `settings.ini`: nbdev configuration (project name, version, author, etc.)
- `nbs/`: Source notebooks (edit these)
- `nbdev_card/`: Generated Python modules (do not edit directly)
- `_proc/`: Processed notebooks during build
- `_docs/`: Generated documentation

## Workflow

1. Edit notebooks in `nbs/` directory
2. Run `nbdev_prepare` to export, test, and update all files
3. Commit both notebooks and generated files
