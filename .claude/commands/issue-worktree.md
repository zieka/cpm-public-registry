---
name: issue-worktree
description: Fix GitHub issue with tests and PR using git worktree
args: required
---

# Issue Command

Analyze and fix a GitHub issue with automated workflow.

## Arguments

- `$1` or `$ISSUE_NUMBER`: GitHub issue number to fix

## Workflow

Follow these steps:
 - 1. Ensure that .worktrees/ is in the .gitignore file.  If not add it. 
 - 2. Create a git worktree for the issue
 - 3. Use `gh issue view` to get the issue details 
 - 4. Take time to think about the problem described in the issue
 - 5. Read and follow the projects CLAUDE.md file
 - 6. Write and run tests to verify the fix
 - 7. Ensure code passes linting and type checking
 - 8. Create a commit using conventional commit message
 - 9. Create a draft PR using the gh cli
   - PR body message should have two sections `Problem` and `Solution`
     - Problem should also start with `- fixes #<ISSUE_NUMBER>`
     - SHOULD NOT mention claude code or embed any links to claude code
     - Solution section should be a hierarchical list of key changes
     - Solution section can optionally provide a performance impact section with assumptions, benchmarks, trade-offs, and other relevant information
   - IMPORTANT: do not sign the commit as authored by claude

Remember to use the GitHub CLI (gh) for all GitHub-related tasks.