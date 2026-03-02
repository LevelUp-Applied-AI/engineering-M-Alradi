[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/g7vj6YXc)
# AI.SPIRE Pre-Work — Phase 3: Engineering Practices

**GitHub Classroom Phase 3 repo.** Days 6–9.

Phase 3 covers PR hygiene, pytest, SQL, and Docker — the engineering practices that make code reviewable, testable, and deployable.

---

## Phase overview

| Day | PR | Topic |
|-----|----|-------|
| 6 | PR 5 | PR Hygiene: Template + Self-Review Checklist |
| 7 | PR 6 | First Tests: Make 5 Failing Tests Pass |
| 8 | PR 7 | SQLite Queries |
| 9 | PR 8 | Docker + Postgres Container Validation |

---

## Setup

Your venv and all packages from `requirements-prework.txt` should already be installed from Day 3. If you need to reinstall:

```bash
python -m venv .venv
source .venv/bin/activate   # Mac/Linux
# or: source .venv/Scripts/activate  (Windows Git Bash)
pip install -r requirements-prework.txt
```

---

## How to run

Follow these steps to get the project running and test everything:

1. Activate the virtual environment 
   - Windows:  
     ```bash
     source .venv/Scripts/activate
     ```  
   - Mac/Linux:  
     ```bash
     source .venv/bin/activate
     ```

2. Install dependencies  
   ```bash
   pip install -r requirements.txt

3. Run all tests
   ```bash
   pytest tests/ -v
