---
name: smart-rename
description: Suggest better variable and function names based on usage context and conventions
---

# Smart Rename Command

Analyzes your code and suggests more descriptive, consistent names for variables, functions, and classes based on their actual usage and project conventions.

## Usage

```bash
/smart-rename [path] [--style=camelCase|snake_case|kebab-case] [--aggressive=true|false]
```

## Parameters

- `path`: File or directory to analyze (defaults to current file)
- `--style`: Naming convention to enforce (auto-detects if not specified)
- `--aggressive`: If true, suggests more opinionated changes (default: false)

## What it analyzes

### Variable Names
- Single-letter variables (except loop counters)
- Generic names like `data`, `temp`, `obj`, `val`
- Misleading names that don't match usage
- Abbreviated names that could be clearer

### Function Names
- Functions starting with `get` that don't return values
- Boolean functions not starting with `is/has/should`
- Functions doing more than their name suggests
- Inconsistent verb usage (fetch vs get vs load)

### Project Conventions
- Detects existing naming patterns in your codebase
- Maintains consistency with team conventions
- Respects domain-specific terminology

## Naming Rules Applied

1. **Booleans**: Should start with `is`, `has`, `should`, `can`, `will`
2. **Functions**: Start with verbs describing action
3. **Constants**: UPPER_SNAKE_CASE for true constants
4. **Collections**: Plural names for arrays/lists
5. **Callbacks**: Prefix with `on` or `handle`
6. **Private members**: Prefix with underscore (if convention exists)

## Output Format

```
📝 Suggested Renames:

src/utils/helper.js:15
  ❌ const d = new Date();
  ✅ const currentDate = new Date();
  Reason: Single-letter variable should be descriptive

src/api/user.js:42  
  ❌ function processData(x) { ... }
  ✅ function validateUserProfile(userData) { ... }
  Reason: Function name should describe specific action; parameter needs context

src/components/Button.jsx:8
  ❌ const flag = props.disabled;
  ✅ const isDisabled = props.disabled;
  Reason: Boolean variable should start with 'is'
```

## Interactive Mode

When run, the command offers options to:
- Apply all suggestions
- Review each suggestion individually
- Generate a report without changes
- Create a naming conventions document

## Example

```bash
/smart-rename src/ --style=camelCase --aggressive=false
```

This analyzes the src directory and suggests naming improvements following camelCase convention.