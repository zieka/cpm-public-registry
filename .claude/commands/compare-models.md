---
name: compare-models
description: Compare outputs of two models in parallel using tmux
args: required
---

# Arguments
- the user should specify in the arguments two models to compare and a task to perform
- example: `opus vs sonnet "make a function to reverse a linked list"`

# Model Comparison Workflow

## Add .worktrees/ to .gitignore if they are not there and commit this change separately.

## Notes:
- use single quotes instead of double quotes in the git commit command

## Run Two Workers
1. Create a tmux session with the name of the describing the task (e.g., `tmux new-session -d -s $SESSION_NAME`)
2. Create a window for each model (see the $ARGUMENTS to know which models to use):
   - Run `git worktree add ".worktrees/$TASK-$MODEL" -b "$TASK-$MODEL"`
   - Make a new window in the tmux session with an agent running the model and on the original prompt:
     `tmux new-window -t $SESSION_NAME 'claude "$PROMPT" --model $MODEL'`