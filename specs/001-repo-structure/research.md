# Research: Repository Structure & README

**Feature**: 001-repo-structure
**Date**: 2025-12-30

## Research Topics

### 1. Google Colab Badge Format

**Decision**: Use standard Colab badge with GitHub-hosted notebook links

**Format**:
```markdown
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/USERNAME/REPO/blob/main/tutorials/NOTEBOOK.ipynb)
```

**URL Pattern**:
- Badge image: `https://colab.research.google.com/assets/colab-badge.svg`
- Link target: `https://colab.research.google.com/github/{owner}/{repo}/blob/{branch}/{path}`

**Rationale**: This is the official Google Colab badge format. It provides instant recognition for users familiar with Colab and requires no additional dependencies.

**Alternatives Considered**:
- Custom badge via shields.io — Rejected: adds complexity, less recognizable
- GitHub Action for auto-generation — Rejected: overkill for small repo, violates Simplicity principle

**Sources**:
- [Google Colab GitHub Demo](https://github.com/googlecolab/colabtools/blob/main/notebooks/colab-github-demo.ipynb)
- [Open in Colab Generator](https://openincolab.com/)

---

### 2. Jupyter Notebook Template Structure

**Decision**: Use 6-section template structure optimized for tutorials

**Template Sections**:
1. **Header Cell** (Markdown): Title, Data Lab branding, Colab badge, description
2. **Setup Cell** (Code): Pinned dependencies with `!pip install` commands
3. **Introduction** (Markdown): What you'll learn, prerequisites, estimated time
4. **Tutorial Content** (Mixed): Numbered sections with explanations and runnable code
5. **Summary** (Markdown): Key takeaways, what you built
6. **Next Steps** (Markdown): Related tutorials, Data Report link, further reading

**Rationale**: Follows Jupyter best practices while enforcing Data Lab constitution requirements (15-30 min completion, pinned versions, runnable checkpoints). Structure ensures consistency across all tutorials.

**Key Principles Applied**:
- Each code cell = one task (avoid long cells)
- Markdown headers for navigation
- Self-contained (no external file dependencies)
- All cells runnable top-to-bottom without modification

**Alternatives Considered**:
- Minimal template (title + content only) — Rejected: inconsistent quality
- Complex template with TOC extension — Rejected: Colab doesn't support all extensions

**Sources**:
- [Jupyter Notebook Best Practices](https://towardsdatascience.com/jupyter-notebook-best-practices-f430a6ba8c69)
- [STScI Style Guide](https://github.com/spacetelescope/style-guides/blob/master/guides/jupyter-notebooks.md)
- [Jupytemplate](https://github.com/xtreamsrl/jupytemplate)

---

### 3. License Selection

**Decision**: MIT License

**Rationale**:
- Permissive: allows commercial use, modification, distribution
- Simple: easy to understand, no copyleft obligations
- Standard: widely recognized in educational/tutorial content
- Compatible: works with any libraries tutorials might use

**Full Text**: Standard MIT License with copyright holder "RepublicOfData.io"

**Alternatives Considered**:
- CC-BY-4.0 — Better for pure documentation but less clear for code
- Apache 2.0 — More complex, patent clauses unnecessary for tutorials
- Unlicense — Too permissive, no attribution requirement

---

### 4. README Structure

**Decision**: Single README with distinct sections

**Sections**:
1. **Header**: Project name, tagline, badges
2. **About**: What is Data Lab, relationship to RepublicOfData.io/Data Report
3. **Tutorials**: Table with title, description, difficulty, Colab link
4. **Archived Tutorials**: Separate section for deprecated content
5. **Creating a Tutorial**: How to use the template, contribution workflow
6. **Tutorial Standards**: Quality checklist (from constitution)
7. **License**: MIT

**Rationale**: Serves all three user stories (author, reader, maintainer) in one scannable document. Tutorial index table enables quick discovery (SC-002: 2 minutes).

**Index Table Format**:
```markdown
| Tutorial | Description | Difficulty | Time | Open |
|----------|-------------|------------|------|------|
| [Title](tutorials/name.ipynb) | One-line description | Beginner | 20 min | [![Open In Colab](badge)](link) |
```

---

## Unresolved Items

None. All research questions resolved.

## Dependencies Identified

- GitHub repository hosting
- Google Colab (free tier)
- No external services or APIs
