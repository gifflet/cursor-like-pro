# Git Conventions and Workflow Guidelines 🔄

This rule provides comprehensive guidelines for Git usage, including commit messages, branch naming, and workflow processes using Conventional Commits.

## Overview

These conventions ensure consistency in Git operations across the project, following industry best practices and the Conventional Commits specification.

## Key Features

- **Commit Message Format**: Follows Conventional Commits specification
- **Branch Naming Convention**: Structured naming patterns
- **Protected Branches**: Guidelines for main/master branch protection
- **MCP Git Integration**: Cursor-specific Git operations
- **Language Requirement**: All Git-related text must be in English

## Commit Types

- `feat`: New features
- `fix`: Bug fixes
- `docs`: Documentation changes
- `style`: Code style changes
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Test-related changes
- `chore`: Build process or auxiliary tools
- `ci`: CI configuration changes

## Branch Naming

```
<type>/<short-description>
# or with ticket number
<type>/<ticket-number>-<short-description>
```

Examples:
- `feat/add-google-auth`
- `fix/PROJ-456-handle-null-responses`

## Workflow Best Practices

1. Never commit directly to protected branches
2. Create feature branches for all changes
3. Keep branches updated with main
4. Use Pull Requests for all changes
5. Require code reviews
6. Use squash merging

## MCP Git Usage

Special integration with Cursor's Model Context Protocol for Git operations:

```python
# Check current branch
mcp_git_git_status(repo_path=".")

# Create and switch to feature branch
mcp_git_git_create_branch(
    repo_path=".",
    branch_name="feat/my-feature",
    base_branch="main"
)

# Make commits
mcp_git_git_add(repo_path=".", files=["path/to/file"])
mcp_git_git_commit(
    repo_path=".",
    message="feat(component): add new feature"
)
```

## Pre-commit Hooks

Recommended hooks:
- Commit message format validation
- Code linting
- Test execution
- Branch naming validation
- Protected branch checks 