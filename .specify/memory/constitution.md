<!--
SYNC IMPACT REPORT
==================
Version Change: 0.0.0 → 1.0.0 (MAJOR - initial ratification)

Added Sections:
- I. Zero Friction
- II. Tutorial Quality
- III. Editorial Integration
- IV. Simplicity
- Technical Constraints
- Content Workflow

Templates Requiring Updates:
- .specify/templates/plan-template.md ✅ (Constitution Check section compatible)
- .specify/templates/spec-template.md ✅ (no constitution-specific changes needed)
- .specify/templates/tasks-template.md ✅ (no constitution-specific changes needed)

Follow-up TODOs: None
==================
-->

# Data Lab Constitution

## Core Principles

### I. Zero Friction

Every tutorial MUST work with "click and run" in Google Colab. Users MUST NOT need:
- External accounts beyond Google
- CLI tools, Docker, or local environment setup
- Complex prerequisites or manual configuration
- Paid services or API keys they must provision

**Rationale**: Data Lab exists to bridge the gap between reading and doing. Any friction between "I want to try this" and "I'm running code" defeats the purpose. Colab's zero-setup environment is the only acceptable platform for Release 01.

### II. Tutorial Quality

Each tutorial MUST:
- Complete in 15-30 minutes for a typical practitioner
- Include pinned library versions to prevent silent breakage
- Provide working code that users can adapt for their own projects
- Connect directly to a real Data Report story or concept

Tutorials MUST NOT:
- Require prior knowledge beyond basic Python familiarity
- Leave users with broken or incomplete code at any checkpoint
- Include unnecessary tangents or "nice to know" sections

**Rationale**: Tutorials are extensions of editorial content. They must respect the reader's time and deliver on the promise of hands-on learning. Quality over quantity—one excellent tutorial beats three mediocre ones.

### III. Editorial Integration

Data Lab tutorials MUST integrate with Data Report through standardized callouts:

```markdown
---
**Data Lab:** [Tutorial title]
→ [Open in Colab](link)
---
```

Tutorials MUST:
- Be tightly coupled to specific editorial content
- Extend the reading experience into doing
- Be optional depth, not required reading

Tutorials MUST NOT:
- Be created without a corresponding editorial hook
- Require reading to understand the associated article

**Rationale**: Data Lab is not a standalone course platform. It's a complement to Data Report that adds hands-on depth where readers want to go deeper. Tutorials without editorial context are out of scope.

### IV. Simplicity

Start simple. Resist complexity.

- Colab only—no multi-platform support
- Native Colab interface—no custom UI or branding beyond notebook headers
- No user accounts, progress tracking, or gamification
- No paywalled content
- Measure engagement via Substack link clicks only

**Rationale**: This is a bet on whether readers want hands-on content, not a platform build. The small batch (1-2 weeks) limits investment while testing the hypothesis. Scope creep kills small bets.

## Technical Constraints

### Platform
- **Notebooks**: Google Colab (mandatory, no alternatives in Release 01)
- **Storage**: GitHub repository (`data-lab`)
- **Analytics**: Substack link click tracking
- **Format**: Markdown callouts in Data Report drafts

### Repository Structure
```
data-lab/
├── README.md           # Project overview, tutorial index
├── templates/          # Reusable notebook template
│   └── tutorial-template.ipynb
└── tutorials/          # Published tutorials
    └── [topic-name].ipynb
```

### Notebook Requirements
- Pinned dependency versions in first cell
- Data Lab branding in header cell
- Clear section structure with runnable checkpoints
- No cells that require manual intervention to run

## Content Workflow

### Creating a New Tutorial

1. **Editorial Hook**: Identify a Data Report section that warrants hands-on depth
2. **Scope Check**: Verify tutorial can complete in 15-30 minutes
3. **Draft**: Create notebook using template
4. **Test**: Run notebook end-to-end in fresh Colab session
5. **Integrate**: Add Data Lab callout to Data Report draft
6. **Publish**: Commit to `data-lab` repository

### Maintenance

- Quarterly review of all tutorials for library compatibility
- Broken tutorials MUST be fixed or deprecated within one week of discovery
- Deprecated tutorials MUST be clearly marked, not silently removed

## Governance

This constitution governs all Data Lab development. Amendments require:
1. Documentation of proposed change
2. Rationale for why change is necessary
3. Impact assessment on existing tutorials
4. Version increment following semantic versioning

All contributions MUST verify compliance with these principles before merge. The simplicity principle takes precedence when in doubt—if it adds complexity without clear reader value, it's out of scope.

**Version**: 1.0.0 | **Ratified**: 2025-12-30 | **Last Amended**: 2025-12-30
