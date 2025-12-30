# Data Lab

**Hands-on tutorials for data product builders** | [RepublicOfData.io](https://republicofdata.io)

Build real things. Learn by doing. Zero friction.

---

## About

**Data Lab** is a collection of Google Colab notebooks that extend [Data Report](https://datareport.republicofdata.io/)—the newsletter for data product builders—into hands-on learning experiences.

When you read about a technique in Data Report, Data Lab lets you build it yourself in 15-30 minutes. No setup required—just click and code.

### Philosophy

- **Zero Friction**: Every tutorial runs with one click in Google Colab. No accounts, no installations, no configuration.
- **Learn by Doing**: Tutorials focus on building real, working code you can adapt for your own projects.
- **Editorial Integration**: Each tutorial connects to a Data Report story, adding depth to concepts you've already read about.

---

## Creating a Tutorial

Want to contribute a tutorial? Here's how:

### 1. Copy the Template

```bash
cp templates/tutorial-template.ipynb tutorials/your-topic-name.ipynb
```

### 2. Edit in Colab

Open your notebook in Google Colab to develop and test:

```
https://colab.research.google.com/github/republicofdata-io/data-lab/blob/YOUR-BRANCH/tutorials/your-topic-name.ipynb
```

### 3. Follow the Structure

The template has 6 required sections:

1. **Header**: Title, Data Lab branding, Colab badge, description
2. **Setup**: Pinned dependencies (`!pip install package==1.2.3`)
3. **Introduction**: Learning objectives, prerequisites, estimated time
4. **Content**: Numbered sections with explanations and runnable code
5. **Summary**: Key takeaways, what the reader built
6. **Next Steps**: Related tutorials, Data Report link

### 4. Test End-to-End

Before submitting:
- Open in a fresh Colab session (not cached)
- Run all cells top-to-bottom
- Verify all outputs are correct

### 5. Submit a PR

Include:
- Tutorial notebook in `tutorials/`
- Updated README index entry
- Link to related Data Report story (if applicable)

### Naming Convention

Use kebab-case with descriptive names:
- `tool-calling-agents.ipynb`
- `rag-basics.ipynb`
- `semantic-search-intro.ipynb`

**Avoid**: `tutorial1.ipynb`, `my_notebook.ipynb`, `test.ipynb`

### Colab Badge Format

```markdown
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/republicofdata-io/data-lab/blob/main/tutorials/YOUR-NOTEBOOK.ipynb)
```

---

## Tutorial Standards

Every Data Lab tutorial must meet these quality standards:

### Time & Scope
- [ ] Completes in **15-30 minutes**
- [ ] Focused on **one clear concept**
- [ ] No unnecessary tangents

### Dependencies
- [ ] All packages have **pinned versions** (e.g., `pandas==2.0.3`)
- [ ] No external accounts required beyond Google
- [ ] No API keys the reader must provision

### Code Quality
- [ ] All cells **run top-to-bottom** without modification
- [ ] One task per code cell
- [ ] Clear comments explaining the code

### Content
- [ ] Connected to a **Data Report story** or concept
- [ ] Written for data practitioners (assumes basic Python familiarity)
- [ ] Working code the reader can adapt

### Difficulty Levels

| Level | Description |
|-------|-------------|
| **Beginner** | No Python experience needed beyond basic familiarity |
| **Intermediate** | Comfortable with Python basics (loops, functions, imports) |
| **Advanced** | Data engineering experience (APIs, data pipelines, SQL) |

---

## Tutorials

Find a tutorial that interests you and click the **Open in Colab** badge to start learning.

| Tutorial | Description | Difficulty | Time | Updated | Open |
|----------|-------------|------------|------|---------|------|
| *Coming soon* | Tutorials are being developed. Check back or [subscribe to Data Report](https://datareport.republicofdata.io/) for updates. | — | — | — | — |

---

## Archived Tutorials

Tutorials that are no longer maintained are moved here. They may still work but are not actively updated.

**Why tutorials get archived:**
- Library updates cause breaking changes that can't be easily fixed
- Superseded by a newer tutorial on the same topic
- Related Data Report content is no longer available

| Tutorial | Description | Difficulty | Time | Archived |
|----------|-------------|------------|------|----------|
| *None yet* | No tutorials have been archived. | — | — | — |

---

## Maintenance

### Deprecation Process

When a tutorial needs to be deprecated:

1. **Move the file**: `mv tutorials/old-tutorial.ipynb tutorials/archive/`
2. **Update the README**: Remove from Tutorials table, add to Archived Tutorials table
3. **Document the reason**: Note why the tutorial was archived (date in Archived column)

### Archival Criteria

A tutorial may be archived when:
- Library updates break the tutorial and fixes aren't straightforward
- A newer tutorial covers the same topic better
- The related Data Report content is no longer available

---

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

*Data Lab is a project by [RepublicOfData.io](https://republicofdata.io)*
