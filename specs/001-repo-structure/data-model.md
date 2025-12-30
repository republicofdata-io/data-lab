# Data Model: Repository Structure & README

**Feature**: 001-repo-structure
**Date**: 2025-12-30

## Overview

This feature involves static content (Markdown, Jupyter notebooks) rather than a database-backed application. The "data model" here describes the metadata schema for tutorials as represented in the README index and notebook headers.

## Entities

### Tutorial

A Google Colab notebook providing hands-on learning on a specific topic.

**Attributes**:

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| title | string | Yes | Human-readable tutorial name |
| filename | string | Yes | Notebook filename (`topic-name.ipynb`) |
| description | string | Yes | One-line description (max 100 chars) |
| difficulty | enum | Yes | `Beginner` / `Intermediate` / `Advanced` |
| estimated_time | string | Yes | Completion time (e.g., "20 min") |
| data_report_link | url | No | Link to related Data Report story |
| colab_link | url | Yes | Generated from filename |
| status | enum | Yes | `active` / `archived` |
| last_updated | date | Yes | Last modification date |

**Difficulty Levels**:
- **Beginner**: No Python experience needed beyond basic familiarity
- **Intermediate**: Comfortable with Python basics (loops, functions, imports)
- **Advanced**: Data engineering experience (APIs, data pipelines, SQL)

**Filename Convention**: `topic-name.ipynb` (kebab-case, descriptive)
- Good: `tool-calling-agents.ipynb`, `rag-basics.ipynb`
- Bad: `tutorial1.ipynb`, `my_notebook.ipynb`

### Template

A reusable notebook structure that authors copy when creating new tutorials.

**Attributes**:

| Attribute | Type | Required | Description |
|-----------|------|----------|-------------|
| version | string | Yes | Template version (e.g., "1.0") |
| sections | list | Yes | Required sections in order |
| branding | object | Yes | Data Lab header content |

**Required Sections** (in order):
1. Header (Markdown): Title, branding, badge, description
2. Setup (Code): Pinned dependencies
3. Introduction (Markdown): Learning objectives, prerequisites, time
4. Content (Mixed): Tutorial body with numbered sections
5. Summary (Markdown): Key takeaways
6. Next Steps (Markdown): Related content, Data Report link

### Tutorial Index

The README table listing all available tutorials.

**Table Schema**:

| Column | Source | Notes |
|--------|--------|-------|
| Tutorial | title + link to file | Markdown link |
| Description | description | Max 100 chars |
| Difficulty | difficulty | Badge or text |
| Time | estimated_time | e.g., "20 min" |
| Open | colab_link | Colab badge |

**Index Sections**:
- **Active Tutorials**: Current, maintained tutorials
- **Archived Tutorials**: Deprecated tutorials (separate section)

## State Transitions

### Tutorial Lifecycle

```
┌─────────────┐
│   Draft     │  (in author's local/branch)
└──────┬──────┘
       │ PR merged
       ▼
┌─────────────┐
│   Active    │  (in tutorials/, listed in main index)
└──────┬──────┘
       │ Deprecated (broken, outdated, superseded)
       ▼
┌─────────────┐
│  Archived   │  (moved to tutorials/archive/, listed in archive index)
└─────────────┘
```

**Archival Criteria**:
- Library incompatibility that cannot be easily fixed
- Superseded by newer tutorial on same topic
- Related Data Report content no longer available
- Quarterly review identifies maintenance burden

## Relationships

```
Tutorial Index (README.md)
    │
    ├── references → Tutorial (tutorials/*.ipynb)
    │                    │
    │                    └── based_on → Template (templates/tutorial-template.ipynb)
    │
    └── references → Archived Tutorial (tutorials/archive/*.ipynb)
```

## Validation Rules

### Tutorial Validation

1. Filename MUST match pattern: `^[a-z0-9]+(-[a-z0-9]+)*\.ipynb$`
2. Title MUST be present in first markdown cell
3. Setup cell MUST contain pinned versions (e.g., `package==1.2.3`)
4. Estimated time MUST be 15-30 minutes (per constitution)
5. All code cells MUST be runnable top-to-bottom without error

### Index Validation

1. Every `.ipynb` in `tutorials/` MUST have an index entry
2. Every `.ipynb` in `tutorials/archive/` MUST have an archive index entry
3. Colab links MUST use correct URL pattern
4. No orphan entries (index references non-existent file)

## Notes

- This is a documentation structure, not a database schema
- Metadata is embedded in README (human-maintained) and notebook cells
- No automated validation tooling in Release 01 (manual review only)
- Future releases may add CI checks for validation rules
