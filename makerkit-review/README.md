# makerkit-review

Makerkit-specific code quality reviewer for TypeScript, React, Next.js, and Supabase architectures.

## Features

Comprehensive PR review with 7 specialized agents:

| Agent | Focus | Model |
|-------|-------|-------|
| **code-quality-reviewer** | Makerkit architecture, TypeScript strict, RLS, i18n | sonnet |
| **code-reviewer** | General code quality, bug detection, CLAUDE.md compliance | opus |
| **code-simplifier** | Code clarity and maintainability | opus |
| **comment-analyzer** | Comment accuracy and technical debt prevention | inherit |
| **pr-test-analyzer** | Test coverage quality and completeness | inherit |
| **silent-failure-hunter** | Error handling and silent failure detection | inherit |
| **type-design-analyzer** | Type design, invariants, and encapsulation | inherit |

## Installation

```bash
claude --plugin-dir /path/to/makerkit-review
```

## Usage

### Full review (all agents)

```
/makerkit-review:review-pr
```

### Specific review aspects

```
/makerkit-review:review-pr makerkit,types
/makerkit-review:review-pr errors,tests
/makerkit-review:review-pr code
```

### Available review aspects

- `comments` - Code comment accuracy
- `tests` - Test coverage quality
- `errors` - Silent failure detection
- `types` - Type design analysis
- `code` - General code quality
- `makerkit` - Makerkit-specific standards
- `simplify` - Code simplification
- `all` - Run all applicable reviews (default)

## Author

lets-forge
