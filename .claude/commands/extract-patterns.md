---
name: extract-patterns
description: Detect repeated code patterns and extract them into reusable functions/components
---

# Extract Patterns Command

Analyzes your codebase to identify repeated code patterns and suggests extracting them into reusable functions or components.

## Usage

Run this command to analyze files for repeated patterns:

```bash
/extract-patterns [path] [--threshold=3] [--min-lines=5]
```

## Parameters

- `path`: File or directory to analyze (defaults to current directory)
- `--threshold`: Minimum number of repetitions to consider (default: 3)
- `--min-lines`: Minimum lines of code to consider as a pattern (default: 5)

## What it does

1. Scans the specified files for repeated code blocks
2. Identifies common patterns like:
   - Repeated API call structures
   - Similar validation logic
   - Duplicated error handling
   - Repeated component structures
3. Suggests extracting patterns into:
   - Utility functions
   - Custom hooks (for React)
   - Helper classes
   - Shared components
4. Shows before/after examples of the refactoring

## Example

```bash
/extract-patterns src/components --threshold=2 --min-lines=10
```

This will find code patterns repeated at least twice with 10+ lines in the components directory.