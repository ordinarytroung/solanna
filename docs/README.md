# Documentation Index

Welcome to the **Solanna** documentation hub. This directory contains all documentation, drafts, and research materials for the project.

## 📚 Documentation Structure

```
docs/
├── README.md                 # This file - Documentation index
├── drafts/                   # Work-in-progress drafts (agent/collaborator workspace)
├── research/                 # Research notes, experiments, analysis
└── agent_tasks/              # Agent task definitions and outputs
```

---

## 📄 Document Catalog

### Core Documentation

| Document | Location | Description |
|----------|----------|-------------|
| **Main Paper** | `../paper/main.tex` | Springer LNCS manuscript source |
| **Compiled PDF** | `../paper/main_final.pdf` | Final compiled manuscript |
| **Supplementary** | `../paper/supplementary.tex` | Supplementary material |
| **Bibliography** | `../paper/references.bib` | BibTeX references |
| **Figures** | `../paper/figures/` | PDF figures (8 files) |

### Research & Development

| Document | Status | Location |
|----------|--------|----------|
| Experimental Design | 📝 Draft | `research/experimental_design.md` |
| Data Pipeline | ✅ Complete | `../backend/app/helpers/` |
| Model Training | ✅ Complete | `../backend/app/models/` |
| Evaluation Results | ✅ Complete | `../data/evaluation/` |
| Ablation Studies | ✅ Complete | `research/ablation_studies.md` |

### Agent Workspace (AI-Collaborator)

| Category | Purpose | Location |
|----------|---------|----------|
| Draft Manuscripts | Agent-generated drafts | `drafts/` |
| Research Notes | Literature reviews, notes | `research/` |
| Task Definitions | Structured agent tasks | `agent_tasks/` |
| Task Outputs | Agent task outputs | `agent_tasks/outputs/` |

---

## 🔧 Quick Reference

### For Human Contributors

| Task | Command |
|------|---------|
| Start paper edit | `git checkout -b paper/feature-name` |
| Compile paper | `cd paper && pdflatex main.tex && bibtex main && pdflatex main.tex && pdflatex main.tex` |
| View PDF | `open paper/main_final.pdf` (macOS) / `xdg-open paper/main_final.pdf` (Linux) |
| Create draft | `git checkout -b docs/draft/section-name` |

### For AI Agents

| Task | Command |
|------|---------|
| Create draft | Write to `docs/drafts/$(date +%Y%m%d)-topic.md` |
| Research notes | Append to `research/topic-notes.md` |
| Task definition | Create `agent_tasks/task-<id>-description.md` |

### For Reviewers

| Task | Location |
|------|----------|
| Review paper draft | `git checkout paper/branch-name` |
| Review agent output | Check `docs/drafts/` and `agent_tasks/outputs/` |
| Verify compilation | `cd paper && pdflatex main.tex` |

---

## 📋 Documentation Standards

### File Naming Conventions

| Type | Pattern | Example |
|------|---------|---------|
| Drafts | `YYYYMMDD-topic.md` | `20250610-conformal-methodology.md` |
| Research notes | `topic-notes.md` | `conformal-notes.md` |
| Agent tasks | `task-N-description.md` | `task-1-add-conformal-section.md` |
| Outputs | `task-N-output-YYYYMMDD.md` | `task-1-output-20250610.md` |

### Content Standards

| Requirement | Standard |
|-------------|----------|
| Headers | ATX style (`#`, `##`, `###`) |
| Code blocks | Language specified |
| Links | Relative paths preferred |
| Figures | Reference from `../paper/figures/` |
| Citations | Use `[@key]` format |

---

## 📋 Maintenance Checklist

### Monthly
- [ ] Review and archive old drafts (`docs/drafts/`)
- [ ] Update research notes with new findings
- [ ] Verify all links still work
- [ ] Check for broken references in paper

### Per Release
- [ ] Update documentation for new features
- [ ] Regenerate figures if data changed
- [ ] Update citation counts
- [ ] Verify all citations in paper have DOIs

---

## 🔗 Quick Links

| Resource | Link |
|----------|------|
| **GitHub Repository** | https://github.com/ordinarytroung/solanna |
| **Overleaf Project** | [Link to Overleaf] |
| **Springer LNCS Guidelines** | https://www.springer.com/gp/computer-science/lncs |
| **CITATION.cff** | `../CITATION.cff` |
| **Contributing Guide** | `../CONTRIBUTING.md` |
| **Code of Conduct** | `../CODE_OF_CONDUCT.md` |
| **License** | `../LICENSE` |

---

## 📝 Change Log

| Date | Author | Change |
|------|--------|--------|
| 2025-06-10 | System | Initial documentation index created |

---

*Last updated: 2025-06-10*