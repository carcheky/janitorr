# Conventional Commits - Quick Reference

## Format

```
<type>[(<scope>)]: <subject>

[optional body]

[optional footer]
```

**Note**: Scope is optional. Both `feat: add feature` and `feat(api): add feature` are valid.

## Common Types

| Type | Use Case | Example | Version Impact |
|------|----------|---------|----------------|
| `feat` | New feature | `feat: add user authentication` | Minor (0.X.0) |
| `fix` | Bug fix | `fix: resolve null pointer in cleanup` | Patch (0.0.X) |
| `docs` | Documentation only | `docs: update installation guide` | None |
| `style` | Code formatting | `style: fix indentation in main.kt` | None |
| `refactor` | Code restructuring | `refactor: simplify database queries` | None |
| `perf` | Performance improvement | `perf: optimize image loading` | Patch (0.0.X) |
| `test` | Adding tests | `test: add unit tests for cleanup service` | None |
| `build` | Build system changes | `build: update gradle to 8.5` | None |
| `ci` | CI/CD changes | `ci: add docker build workflow` | None |
| `chore` | Maintenance | `chore: update dependencies` | None |
| `revert` | Revert previous commit | `revert: revert feat: add user auth` | Depends |

## Examples

### ✅ Valid Commits

```bash
feat: add Plex media server support
fix: resolve symlink deletion issue
docs: update Docker setup guide
chore: update dependencies to latest versions
refactor: simplify cleanup algorithm
test: add integration tests for Jellyfin
perf: improve database query performance
style: format code according to ktlint rules
ci: add automated release workflow
build: upgrade Kotlin to 2.0.0
```

### ✅ Valid Commits with Scope

```bash
feat(media): add Plex integration
fix(cleanup): resolve deletion of symlinked files
docs(wiki): update configuration examples
chore(deps): bump Spring Boot to 3.2.0
refactor(api): simplify error handling
test(servarr): add Sonarr integration tests
```

### ✅ Breaking Changes

```bash
# Method 1: Using ! after type/scope
feat(api)!: change response format from XML to JSON

# Method 2: Using BREAKING CHANGE in footer
feat(api): change response format

BREAKING CHANGE: API responses are now JSON instead of XML
```

### ❌ Invalid Commits (Will be Rejected)

```bash
Initial plan                          # No type, no colon
WIP: working on feature              # WIP is not a valid type
Updated files                        # No type
Fixed bug                            # No colon
FEAT: add feature                    # Type must be lowercase
feat add feature                     # Missing colon
Feature: add authentication          # "Feature" is not a valid type
```

## Rules

1. **Type must be lowercase**: `feat:` not `FEAT:` or `Feat:`
2. **Type must be from the allowed list**: build, chore, ci, docs, feat, fix, perf, refactor, revert, style, test
3. **Must have a colon**: `feat:` not `feat`
4. **Subject should not start with uppercase**: `feat: add feature` not `feat: Add feature`
5. **No period at the end of subject**: `feat: add feature` not `feat: add feature.`
6. **Subject must not be empty**: `feat:` alone is invalid
7. **Header max length**: 100 characters

## Testing Your Commit Message

```bash
# Test locally before committing
echo "your commit message here" | npx commitlint

# Example
echo "feat: add new feature" | npx commitlint
# ✔ found 0 problems (PASS)

echo "Initial plan" | npx commitlint
# ✖ subject may not be empty
# ✖ type may not be empty (FAIL)
```

## Common Scenarios

### Adding a feature
```bash
git commit -m "feat: add support for Tautulli integration"
```

### Fixing a bug
```bash
git commit -m "fix: resolve memory leak in cleanup scheduler"
```

### Updating documentation
```bash
git commit -m "docs: add troubleshooting section to wiki"
```

### Updating dependencies
```bash
git commit -m "chore: update all dependencies to latest versions"
```

### Refactoring code
```bash
git commit -m "refactor: extract common logic to utility class"
```

### Adding tests
```bash
git commit -m "test: add unit tests for media library service"
```

### Multiple changes in one commit
Use the most significant type:
```bash
# If you added a feature AND added tests for it
git commit -m "feat: add Plex support with comprehensive tests"
```

## When in Doubt

1. **Read the full guide**: [CONTRIBUTING.md](CONTRIBUTING.md)
2. **Check the official spec**: https://www.conventionalcommits.org/
3. **Ask in your PR**: If unsure, ask before committing
4. **Use `feat:` or `chore:`**: When really unsure, these are safe defaults
   - `feat:` for new functionality
   - `chore:` for maintenance tasks

## Why Conventional Commits?

1. **Automatic versioning**: Semantic release automatically determines version numbers
2. **Automatic changelog**: CHANGELOG.md is generated from commit messages
3. **Clear history**: Easy to understand what changed and why
4. **Consistency**: All contributors follow the same format
5. **Tooling**: Many tools integrate with conventional commits

---

**Remember**: Every commit message tells a story. Make it a good one! 📝

See also:
- [docs/COMMIT-REFERENCE.md](docs/COMMIT-REFERENCE.md) - Extended reference
- [CONTRIBUTING.md](CONTRIBUTING.md) - Full contribution guide
- [.commitlintrc.js](.commitlintrc.js) - Configuration file
