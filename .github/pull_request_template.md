=================
## What changed 
=================

- Added a PR template at `.github/pull_request_template.md` to make PRs easier to read and review.  
- Added `docs/pr-checklist.md` with my personal pre-PR self-checks.  
- Updated `README.md` with clear instructions on how to run the project and tests.

=================
## Why 
=================

- So reviewers can quickly understand what changed and why.  
- To make sure PRs are consistent, easy to verify, and don’t sneak in unrelated changes.  
- To give anyone a smooth setup on a fresh machine.

=================
## How to test
=================

1. Activate the virtual environment:  
   - Windows: `source .venv/Scripts/activate`  
   - Mac/Linux: `source .venv/bin/activate`  
2. Install dependencies: `pip install -r requirements-prework.txt`  
3. Run all tests: `pytest tests/ -v`  
   - Everything should pass with no errors or warnings.  
4. Optionally, follow the “How to run” section in the README to verify the project works.

=================
## Scope
=================

- [ ] This PR only adds the PR template, checklist, and README updates — nothing else.

=================
## Checklist 
=================

- [ ] Title is clear and under 72 characters

- [ ] Description explains what changed, why, and how to test

- [ ] Tests added or updated (or a note explaining why not)

- [ ] README updated if setup or runtime behavior changed
    
- [ ] All tests pass locally
