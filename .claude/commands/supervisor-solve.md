---
name: supervisor-solve
description: Multi-agent supervisor workflow requiring tmux
args: required
---

# Supervisor Workflow

# IMPORTANT: The user has elected to use /supervisor The following instructions MUST be followed!

## Notes:
- use single quotes instead of double quotes in the git commit command 

## First create a plan file in the .local directory:
 `.local/{name}.plan.md`

## Add .local/ and .worktrees/ to .gitignore if they are not there and commit this change separately.

## Phase 1: Analysis & Planning
1. **Analyze the request**: Break down the problem into its core components
2. **Explore the codebase**: Read through relevant files to understand the current implementation
3. **Create execution plan**: Document the approach in the plan file `.local/{name}.plan.md` with:
   - Clear, actionable todo items with checkboxes
   - Estimated complexity/risk level for each task
   - Dependencies between tasks
   - Files that will be modified

## Phase 2: Plan Approval
4. **Present the plan**: Share the complete plan and wait for your approval before proceeding
5. **Address feedback**: Incorporate any requested changes to the plan

## Phase 3: Worker spawning and assignment
1. Create a tmux session with the name of the plan file (e.g., `tmux new-session -d -s $SESSION_NAME`)
2. Select one or multiple task that can be solved by one agent.
--Convention: If multiple tasks are dependent on each other, they should be solved by the same agent. If a task is independent, it should be solved by a separate agent.
3. For each selected task to be assigned:
   - Run `git worktree add ".worktrees/$TASK" -b "$TASK"`
   - Build the agent prompt like this: `"Accomplish $TASK_TEXT and then commit the changes"`
   - Make a new window in the tmux session with an agent: `tmux new-window -t $SESSION_NAME 'claude "$PROMPT"'`
4. For every agent you launch, update the task plan file with a status, the tmux session and window, and keep updating as you get new info from the Tmux windows.
   - Continue to supervise each agent by monitoring the tmux windows and responding to their requests
   - When you are satisfied with the work and believe the agent is complete merge the git worktree with your branch

## Phase 4: Documentation & Review
- When a task is completed in the tmux session window merge the changes and delete the worktree.
- **Update task plan**: Add a "Review" section to plan file `.local/{name}.plan.md` containing:
   - Summary of all changes made
   - Final file list (what was actually modified)
   - Any deviations from the original plan and why
   - Potential follow-up improvements or considerations
   - Testing recommendations

## Key Principles
- **Incremental progress**: Small, focused changes over large rewrites
- **Transparency**: Clear communication at every step
- **Reversibility**: Changes should be easy to undo if needed
- **Minimal impact**: Touch as few files as possible
- **Validation**: Get approval before starting implementation

# End of Supervisor Workflow

$ARGUMENTS