# Quickstart: Repository Structure & README

**Feature**: 001-repo-structure
**Date**: 2025-12-30

## Overview

This quickstart guides you through setting up and using the Data Lab repository structure.

## Prerequisites

- GitHub account
- Google account (for Colab access)
- Git installed locally

## Setup (One-Time)

### 1. Clone the Repository

```bash
git clone https://github.com/republicofdata-io/data-lab.git
cd data-lab
```

### 2. Verify Structure

```bash
ls -la
# Expected:
# README.md
# LICENSE
# templates/
# tutorials/
```

## Common Tasks

### Creating a New Tutorial

1. **Copy the template**:
   ```bash
   cp templates/tutorial-template.ipynb tutorials/your-topic-name.ipynb
   ```

2. **Open in Colab** for editing:
   - Push to a branch
   - Open `https://colab.research.google.com/github/republicofdata-io/data-lab/blob/your-branch/tutorials/your-topic-name.ipynb`

3. **Fill in the template sections**:
   - Update title and description in header
   - Add pinned dependencies in setup cell
   - Write tutorial content
   - Test by running all cells top-to-bottom

4. **Update README index**:
   - Add entry to the Tutorials table
   - Include Colab badge link

5. **Submit PR** for review

### Viewing a Tutorial

1. **From README**: Click the "Open in Colab" badge
2. **Direct URL**: `https://colab.research.google.com/github/republicofdata-io/data-lab/blob/main/tutorials/NOTEBOOK.ipynb`

### Archiving a Tutorial

1. Move file:
   ```bash
   mv tutorials/old-tutorial.ipynb tutorials/archive/
   ```

2. Update README:
   - Remove from main Tutorials table
   - Add to Archived Tutorials section

3. Commit with message explaining deprecation reason

## Validation Checklist

Before submitting a new tutorial:

- [ ] Filename follows `topic-name.ipynb` convention
- [ ] All dependencies pinned with versions
- [ ] Completes in 15-30 minutes
- [ ] All cells run without error in fresh Colab session
- [ ] Header includes Data Lab branding
- [ ] Related Data Report story identified (if applicable)
- [ ] README index entry added with Colab badge

## Troubleshooting

### Colab Badge Not Working

Verify URL format:
```
https://colab.research.google.com/github/{owner}/{repo}/blob/{branch}/{path}
```

### Notebook Won't Run

- Check all dependencies are pinned
- Ensure no local file references
- Test in fresh Colab session (not cached)

## Next Steps

After completing setup:
1. Create your first tutorial using `/speckit.specify` for the template feature
2. Review the [Data Lab Constitution](../../.specify/memory/constitution.md) for quality standards
