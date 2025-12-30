# Tasks: Repository Structure & README

**Input**: Design documents from `/specs/001-repo-structure/`
**Prerequisites**: plan.md, spec.md, research.md, data-model.md

**Tests**: No automated tests requested. Validation is manual (README renders correctly, Colab links work).

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Path Conventions

This is a content repository with flat structure:

```text
data-lab/
├── README.md
├── LICENSE
├── templates/
│   └── tutorial-template.ipynb
└── tutorials/
    └── archive/
```

---

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Create repository structure and foundational files

- [x] T001 Create `tutorials/` directory at repository root
- [x] T002 [P] Create `tutorials/archive/` subdirectory for deprecated tutorials
- [x] T003 [P] Create `templates/` directory at repository root
- [x] T004 Create LICENSE file with MIT License (copyright: RepublicOfData.io) at repository root

**Checkpoint**: Directory structure exists, ready for content creation

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Core content that MUST be complete before user stories can be validated

**⚠️ CRITICAL**: The notebook template (T005) is required before User Story 1 can be completed

- [x] T005 Create `templates/tutorial-template.ipynb` with 6-section structure:
  - Header cell (Markdown): Data Lab branding, title placeholder, Colab badge placeholder, description
  - Setup cell (Code): `!pip install` with version pinning example
  - Introduction cell (Markdown): Learning objectives, prerequisites, estimated time placeholders
  - Content section (Mixed): Numbered section structure with code/markdown pattern
  - Summary cell (Markdown): Key takeaways placeholder
  - Next Steps cell (Markdown): Related tutorials, Data Report link placeholders

**Checkpoint**: Template ready - README can now reference it for contribution guidelines

---

## Phase 3: User Story 1 - Tutorial Author Creates New Tutorial (Priority: P1) 🎯 MVP

**Goal**: Enable authors to create tutorials following documented structure

**Independent Test**: Clone repo, follow README instructions, create tutorial using template—no questions needed

### Implementation for User Story 1

- [x] T006 [US1] Create README.md header section with:
  - Project title "Data Lab"
  - Tagline connecting to RepublicOfData.io
  - Brief description of hands-on tutorials for data product builders

- [x] T007 [US1] Create README.md "About" section explaining:
  - What is Data Lab
  - Relationship to Data Report newsletter
  - Zero-friction philosophy (Colab-based, click-and-run)

- [x] T008 [US1] Create README.md "Creating a Tutorial" section with:
  - Step-by-step workflow (copy template → edit → test → PR)
  - Link to template file
  - Naming convention (`topic-name.ipynb`, kebab-case)
  - Colab badge format example from research.md

- [x] T009 [US1] Create README.md "Tutorial Standards" section with:
  - Quality checklist from constitution (15-30 min, pinned versions, runnable)
  - Difficulty level definitions (Beginner/Intermediate/Advanced)
  - Editorial integration requirement (Data Report connection)

**Checkpoint**: Author can clone repo, read README, use template to create tutorial

---

## Phase 4: User Story 2 - Reader Discovers Available Tutorials (Priority: P2)

**Goal**: Enable readers to find and open tutorials quickly

**Independent Test**: Visit repository, identify interesting tutorial, open in Colab within 2 minutes

### Implementation for User Story 2

- [x] T010 [US2] Create README.md "Tutorials" section with:
  - Empty table structure matching data-model.md schema:
    | Tutorial | Description | Difficulty | Time | Open |
  - Placeholder row explaining "Tutorials coming soon" for empty state
  - Colab badge format for future tutorials

- [x] T011 [US2] Create README.md "Archived Tutorials" section with:
  - Explanation of archive purpose
  - Empty table structure (same schema as active tutorials)
  - Note about why tutorials get archived

**Checkpoint**: Reader sees tutorial index (empty initially), understands how to access tutorials

---

## Phase 5: User Story 3 - Maintainer Reviews Repository Health (Priority: P3)

**Goal**: Enable maintainers to audit tutorial status quickly

**Independent Test**: Open README, identify all tutorials and their status within 3 minutes

### Implementation for User Story 3

- [x] T012 [US3] Add "Last Updated" column to tutorial index tables in README.md
- [x] T013 [US3] Add maintenance notes to README.md:
  - Quarterly review cadence
  - Archival criteria (broken, outdated, superseded)
  - Deprecation process (move to archive, update index)

**Checkpoint**: Maintainer can audit repo health from README alone

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Final validation and refinements

- [x] T014 Add LICENSE section to README.md footer with MIT license notice
- [x] T015 Validate README.md renders correctly on GitHub (check formatting, tables, links)
- [x] T016 Validate template notebook opens in Colab without errors
- [x] T017 Run quickstart.md validation: clone repo, follow all documented workflows

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - can start immediately
- **Foundational (Phase 2)**: Depends on Setup (T001-T003) - BLOCKS User Story 1
- **User Story 1 (Phase 3)**: Depends on Foundational (T005 template)
- **User Story 2 (Phase 4)**: Depends on User Story 1 (README structure exists)
- **User Story 3 (Phase 5)**: Depends on User Story 2 (tutorial index exists)
- **Polish (Phase 6)**: Depends on all user stories complete

### User Story Dependencies

- **User Story 1 (P1)**: Requires template (T005). Creates README foundation.
- **User Story 2 (P2)**: Requires README from US1. Adds tutorial index sections.
- **User Story 3 (P3)**: Requires index from US2. Adds maintenance metadata.

### Within Each User Story

- Create section structure first
- Add content details second
- Validate independently before next story

### Parallel Opportunities

- **Phase 1**: T002, T003, T004 can run in parallel after T001
- **Phase 3**: T006, T007, T008, T009 could theoretically run in parallel but all modify README.md (use sequential to avoid conflicts)
- **Phase 4**: T010, T011 modify same file (sequential)

---

## Parallel Example: Phase 1 Setup

```bash
# After T001 creates tutorials/:
Task: "Create tutorials/archive/ subdirectory"  # T002
Task: "Create templates/ directory"              # T003
Task: "Create LICENSE file"                      # T004
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup (directories + license)
2. Complete Phase 2: Foundational (notebook template)
3. Complete Phase 3: User Story 1 (README for authors)
4. **STOP and VALIDATE**: Can an author create a tutorial using only the documentation?
5. Demo if ready

### Incremental Delivery

1. Setup + Foundational → Repository skeleton ready
2. User Story 1 → Authors can contribute (MVP!)
3. User Story 2 → Readers can discover tutorials
4. User Story 3 → Maintainers can audit health
5. Polish → Final validation

### Single Developer Strategy

Execute sequentially: T001 → T002 → T003 → T004 → T005 → T006 → ... → T017

Commit after each phase completion.

---

## Notes

- This is a content/documentation feature, not application code
- All tasks create or modify Markdown or Jupyter notebook files
- No automated tests—validation is manual per Testing field in plan.md
- README.md is modified across multiple tasks; execute sequentially to avoid conflicts
- Template notebook (T005) is the most complex task; reference research.md for structure
