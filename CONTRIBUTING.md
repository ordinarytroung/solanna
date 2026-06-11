# Contributing Guidelines

Thank you for your interest in contributing to **Solanna: Event-Aware Stock Prediction Framework**. This document provides guidelines for contributing to this academic research project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How to Contribute](#how-to-contribute)
- [Development Setup](#development-setup)
- [Branch Strategy](#branch-strategy)
- [Commit Message Conventions](#commit-message-conventions)
- [Pull Request Process](#pull-request-process)
- [Paper-Specific Guidelines](#paper-specific-guidelines)
- [Code Standards](#code-standards)
- [Review Process](#review-process)

## Code of Conduct

This project adheres to the [Contributor Covenant Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to datttruong.uit@gmail.com.

## How to Contribute

### Types of Contributions Welcome

1. **Paper improvements**: Typo fixes, clarification, additional references, improved figures
2. **Code improvements**: Bug fixes, performance optimizations, new features
3. **Documentation**: README updates, tutorials, examples, API documentation
5. **Testing**: Unit tests, integration tests, validation scripts
6. **Reproducibility**: Docker files, environment specifications, dependency management

### Before You Start

1. Check existing [issues](https://github.com/ordinarytroung/solanna/issues) and [discussions](https://github.com/ordinarytroung/solanna/discussions)
2. For major changes, open an issue first to discuss the approach
3. Fork the repository and create a feature branch

## Development Setup

### Prerequisites

- Python 3.11+
- Node.js 18+
- Docker & Docker Compose
- LaTeX (TeX Live or MiKTeX) for paper compilation

### Quick Start

```bash
# Clone repository
git clone https://github.com/ordinarytroung/solanna.git
cd solanna

# Backend setup
cd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
pip install -r requirements-research.txt

# Frontend setup
cd ../src
npm install

# Paper compilation
cd ../paper
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

### Docker Development

```bash
docker-compose up -d
# Access services at localhost ports
```

## Branch Strategy

```
main                    # Protected branch - production ready
├── feature/*           # New features (e.g., feature/add-conformal-plots)
├── fix/*               # Bug fixes (e.g., fix/citation-style)
├── docs/*              # Documentation updates
├── paper/*             # Paper-specific changes
├── chore/*             # Maintenance (deps, CI, configs)
└── docs/drafts/*       # Agent/collaborator drafts (not merged directly)
```

### Branch Naming

| Type | Pattern | Example |
|------|---------|---------|
| Feature | `feature/short-description` | `feature/add-conformal-plots` |
| Bug fix | `fix/short-description` | `fix/citation-format` |
| Documentation | `docs/short-description` | `docs/update-readme-citation` |
| Paper edits | `paper/section-action` | `paper/methods-add-conformal` |


## Commit Message Conventions

Follow [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types

| Type | Description |
|------|-------------|
| `feat` | New feature |
| `fix` | Bug fix |
| `docs` | Documentation only |
| `style` | Formatting, no logic change |
| `refactor` | Code restructuring |
| `perf` | Performance improvement |
| `test` | Adding tests |
| `chore` | Maintenance, build, deps |
| `paper` | Paper manuscript changes |

### Examples

```
feat(paper): add conformal prediction section
fix(figures): correct axis labels in Figure 3
docs: update README with citation format
chore(deps): update numpy to 1.26.0
paper/methods: add conformal prediction methodology
```

## Pull Request Process

### Before Submitting

1. **Self-review**: Ensure changes compile, tests pass, formatting is correct
2. **Update documentation**: README, docstrings, comments
2. **Run tests**: `pytest` (backend), `npm test` (frontend), `pdflatex` (paper)
3. **Check formatting**: `black`, `isort` (Python), `prettier` (TypeScript)

### PR Requirements

| Requirement | Description |
|-------------|-------------|
| **Title** | Conventional commit format: `type(scope): description` |
| **Description** | What, why, how. Link related issues. |
| **Tests** | All existing tests pass; new tests for new features |
| **Documentation** | Updated for API changes, new features |
| **Paper changes** | Must compile (0 errors, 0 warnings) |
| **Figures** | PDF format only, referenced in text |

### Review Process

1. **Automated checks**: CI must pass (LaTeX compile, tests, linting)
2. **Human review**: At least 1 approving review required
3. **Paper changes**: Require explicit approval from corresponding author
4. **Merge**: Squash and merge (or rebase and merge)

### Branch Protection (Enforced)

- ✅ Require PR reviews (1+)
- ✅ Require status checks (CI passes)
- ✅ Require branches up to date
- ✅ Dismiss stale reviews on new commits
- ❌ No force push to main
- ❌ No direct pushes to main

## Paper-Specific Guidelines

### Paper Structure

The manuscript follows Springer LNCS format (`llncs.cls`):

```
paper/
├── main.tex              # Main manuscript
├── references.bib        # Bibliography (BibTeX)
├── supplementary.tex     # Supplementary material
├── supplementary_appendix.tex
├── figures/              # PDF figures only
├── llncs.cls             # Springer template
└── splncs04.bst          # Bibliography style
```

### Editing Guidelines

| Rule | Rationale |
|------|-----------|
| Edit `main.tex` only via PR | Version control, review |
| Use `paper/figures/` PDFs only | Springer requires PDF/EPS |
| Cite with `\cite{key}` | Consistent bibliography |
| Cross-reference with `\ref{}` | Automatic numbering |
| No hardcoded numbers | Use `\ref{}`, `\pageref{}` |

### Adding Figures

1. Generate/export as **PDF** (vector preferred)
2. Place in `paper/figures/`
2. Reference in text: `\includegraphics[width=0.8\textwidth]{figures/your_figure.pdf}`
3. Add `\caption{...}` and `\label{fig:label}`
4. Reference in text: `Figure~\ref{fig:label}`

### Bibliography

- Use BibTeX: `references.bib`
- Keys: `author_year` or `firstauthor_year`
- Required fields: author, title, journal/booktitle, year, doi/url
- Use `@article`, `@inproceedings`, `@book`, `@misc` appropriately

### LaTeX Compilation

```bash
cd paper
pdflatex -interaction=nonstopmode main.tex
bibtex main
pdflatex -interaction=nonstopmode main.tex
pdflatex -interaction=nonstopmode main.tex
```

**Must compile with 0 errors** (warnings acceptable for overfull boxes).

## Code Standards

### Python (Backend)

- **Style**: Black (line-length 100), isort
- **Types**: Type hints required for public APIs
- **Docstrings**: Google style for public functions
- **Tests**: pytest, >80% coverage for new code

```bash
# Format
black --line-length 100 backend/
isort backend/

# Lint
flake8 backend/
mypy backend/
```

### TypeScript/React (Frontend)

- **Style**: Prettier, ESLint
- **Types**: Strict mode, no `any`
- **Components**: Functional, hooks-based

```bash
# Format
npm run format  # prettier --write

# Lint
npm run lint    # eslint
```

### LaTeX (Paper)

- **Encoding**: UTF-8
- **Line length**: ≤ 120 chars (soft)
- **Encoding**: No raw Unicode in math mode

## Review Process

### For Reviewers

| Checklist Item | Required |
|----------------|----------|
| Code compiles / paper compiles | ✅ Yes |
| Tests pass | ✅ Yes |
| Documentation updated | ✅ Yes |
| Follows style guide | ✅ Yes |
| No security issues | ✅ Yes |
| Paper: figures referenced | For paper PRs |

### For Authors

- Respond to reviews within 2 business days
- Address all comments (fix or justify)
- Keep PRs focused and small (<500 lines when possible)
- Rebase onto latest main before merging

## Getting Help

- **Issues**: [GitHub Issues](https://github.com/ordinarytroung/solanna/issues)
- **Discussions**: [GitHub Discussions](https://github.com/ordinarytroung/solanna/discussions)
- **Email**: datttruong.uit@gmail.com (corresponding author)

---

## Quick Reference

### Common Commands

```bash
# Paper compile
cd paper && pdflatex main.tex && bibtex main && pdflatex main.tex && pdflatex main.tex

# Backend tests
cd backend && pytest -v

# Frontend tests
cd src && npm test

# Full CI locally
docker-compose -f docker-compose.yml -f docker-compose.ci.yml up --abort-on-container-exit
```

### Useful Links

- [Springer LNCS Guidelines](https://www.springer.com/gp/computer-science/lncs)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Contributor Covenant](https://www.contributor-covenant.org/)
- [Semantic Versioning](https://semver.org/)