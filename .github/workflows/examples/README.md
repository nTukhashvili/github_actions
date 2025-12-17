# GitHub Actions Workflow Examples 📚

This directory contains annotated examples of GitHub Actions workflows for educational purposes.

## Quick Reference

| Example | File | Use Case |
|---------|------|----------|
| 1. Basic CI | `01-basic-ci.yml` | Simple test automation |
| 2. Matrix Strategy | `02-matrix-strategy.yml` | Multi-version/platform testing |
| 3. Scheduled Jobs | `03-scheduled-cron.yml` | Cron-based automation |
| 4. Docker Build | `04-docker-build.yml` | Container image CI/CD |
| 5. Multi-Environment | `05-deploy-environments.yml` | Staged deployments |
| 6. Release Automation | `06-release-automation.yml` | Automated releases |
| 7. Security Scanning | `07-security-scanning.yml` | Security & code quality |
| 8. GitHub Pages | `08-github-pages.yml` | Static site deployment |
| 9. Reusable Workflows | `09-reusable-workflow.yml` | DRY workflow templates |
| 10. Conditional Logic | `10-conditional-jobs.yml` | Advanced conditions |

## Key Concepts

### Triggers (`on:`)
```yaml
on:
  push:           # When code is pushed
  pull_request:   # When PR is opened/updated
  schedule:       # Cron-based schedule
  workflow_dispatch:  # Manual trigger
  workflow_call:  # Called by other workflows
```

### Job Dependencies
```yaml
jobs:
  build:
    runs-on: ubuntu-latest
  
  deploy:
    needs: build  # Waits for build to complete
```

### Matrix Strategy
```yaml
strategy:
  matrix:
    os: [ubuntu-latest, windows-latest]
    node: [16, 18, 20]
```

### Conditions
```yaml
if: github.ref == 'refs/heads/main'
if: github.event_name == 'pull_request'
if: contains(github.event.head_commit.message, '[deploy]')
if: always()    # Run even if previous steps fail
if: failure()   # Run only if previous steps fail
if: success()   # Run only if previous steps succeed
```

### Secrets & Variables
```yaml
env:
  API_KEY: ${{ secrets.API_KEY }}
  NODE_ENV: production
```

### Artifacts
```yaml
# Upload
- uses: actions/upload-artifact@v4
  with:
    name: my-artifact
    path: dist/

# Download
- uses: actions/download-artifact@v4
  with:
    name: my-artifact
```

## GitHub Actions Syntax Cheat Sheet

### Context Variables
| Context | Description |
|---------|-------------|
| `github.ref` | Full ref (e.g., `refs/heads/main`) |
| `github.sha` | Commit SHA |
| `github.actor` | User who triggered the workflow |
| `github.event_name` | Event that triggered (push, pull_request, etc.) |
| `github.repository` | Repository name (owner/repo) |
| `github.workspace` | Workspace directory path |

### Common Actions
| Action | Purpose |
|--------|---------|
| `actions/checkout@v4` | Clone repository |
| `actions/setup-python@v5` | Install Python |
| `actions/setup-node@v4` | Install Node.js |
| `actions/cache@v4` | Cache dependencies |
| `actions/upload-artifact@v4` | Save build outputs |
| `actions/download-artifact@v4` | Retrieve artifacts |

## Best Practices

1. **Use specific action versions** (`@v4` not `@latest`)
2. **Cache dependencies** for faster builds
3. **Use matrix builds** for multi-platform testing
4. **Protect sensitive data** with GitHub Secrets
5. **Use environments** for deployment approvals
6. **Fail fast** with proper error handling
7. **Keep workflows DRY** with reusable workflows

## Getting Started

1. Copy an example to `.github/workflows/`
2. Rename it (e.g., `ci.yml`)
3. Modify as needed
4. Commit and push!

## Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow Syntax Reference](https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions)
- [GitHub Actions Marketplace](https://github.com/marketplace?type=actions)
- [Context and Expression Syntax](https://docs.github.com/en/actions/learn-github-actions/contexts)


