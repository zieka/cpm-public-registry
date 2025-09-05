# CPM Public Registry

A collection of useful Claude Code commands for common development workflows. This repository also serves as the default repository for the [CPM (Claude Package Manager)](https://www.npmjs.com/package/@zieka-tools/cpm) tool, which helps you manage and install Claude Code commands from this repo or others.

## Installation

Install CPM globally to manage Claude Code commands:

```bash
npm install -g @zieka-tools/cpm
```

## Getting Started with CPM

Run CPM without arguments to open the interactive TUI:

```bash
cpm
```

CPM allows you to browse, install, and manage commands from this repository or any other command repository you configure.

## Commands

This repository contains various Claude Code commands to automate and enhance your development workflow:

- **todo-finder** - Find TODO/FIXME comments and suggest priorities
- **update-pr** - Update PR description with commit summary
- **perf-scan** - Find performance bottlenecks and optimizations
- **extract-patterns** - Extract repeated code into reusable components
- **smart-rename** - Suggest better names based on usage context
- **issue** - Fix GitHub issue with tests and PR
- **clean-comments** - Clean up code comments in PR or staged changes

## Usage

These commands are available as slash commands in Claude Code. Simply type `/` followed by the command name to use them.

## Contributing

### Command Header Standard

All commands in this repository follow a standardized header format for optimal Claude Code integration:

```yaml
---
name: command-name
description: Action verb + what it does (<60 chars)
args: none|optional|required
---
```

#### Why This Format?

1. **Fast Autocomplete** - Descriptions under 60 characters ensure quick loading in Claude Code's slash command menu
2. **Clear Expectations** - The `args` field immediately indicates whether arguments are needed
3. **Action-Oriented** - Starting descriptions with action verbs improves discoverability
4. **Clean Separation** - Headers contain only metadata, while detailed documentation goes in the body

#### Example Command Structure

```markdown
---
name: example-command
description: Analyze code and suggest improvements
args: optional
---

# Example Command

Brief explanation of what this command does.

## Arguments

- `$1`: Path to analyze (defaults to current directory)
- `--flag`: Optional configuration flag

## Workflow

Step-by-step instructions for Claude...
```

### Adding New Commands

When contributing new commands:

1. Follow the header standard above
2. Keep descriptions concise and action-oriented
3. Document all arguments clearly in the body
4. Provide clear workflow instructions
5. Test your command thoroughly before submitting

### Submitting Changes

1. Create a new branch for your changes
2. Follow the existing code style and conventions
3. Test your commands thoroughly
4. Submit a pull request with a clear description of changes

## License

[Add your license information here]