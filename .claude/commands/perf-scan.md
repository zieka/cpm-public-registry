---
name: perf-scan
description: Identify performance bottlenecks and optimization opportunities in your code
---

# Performance Scan Command

Analyzes your code for performance hotspots and suggests optimizations.

## Usage

```bash
/perf-scan [path] [--depth=deep|quick] [--framework=react|vue|node|general]
```

## Parameters

- `path`: File or directory to analyze (defaults to current directory)
- `--depth`: Analysis depth - 'quick' for common issues, 'deep' for comprehensive scan (default: quick)
- `--framework`: Target framework-specific optimizations (default: general)

## What it detects

### Algorithm Issues
- O(n²) or worse complexity in nested loops
- Inefficient array operations (.filter().map() chains)
- Unnecessary sorting operations
- Repeated calculations that could be memoized

### React/Vue Specific
- Missing React.memo() on pure components
- useEffect dependencies causing re-renders
- Inline function definitions in render
- Large lists without virtualization
- Unnecessary state updates

### Database/API
- N+1 query problems
- Missing database indexes (based on query patterns)
- Synchronous operations that could be parallel
- Unbatched API calls

### Memory Issues
- Memory leaks from event listeners
- Large objects kept in closure scope
- Unnecessary data duplication

## Output

The command generates a report with:
- **Critical** 🔴 Issues causing significant slowdowns
- **Warning** 🟡 Opportunities for optimization  
- **Info** 🔵 Best practice suggestions

Each issue includes:
- Location (file:line)
- Impact assessment
- Suggested fix with code example
- Estimated performance improvement

## Example

```bash
/perf-scan src/ --depth=deep --framework=react
```

This performs a deep scan of React code in the src directory for performance issues.