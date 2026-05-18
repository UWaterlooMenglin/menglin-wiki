# Copilot CLI Instructions for menglin-wiki

This document provides guidelines for working with the ROS2 and other wiki content in this repository. These instructions are automatically loaded when using GitHub Copilot CLI.

## Project Overview

**Goal:** Build an evolving Obsidian vault that documents learning journey from beginner to experienced developer, showcasing systematic knowledge management for portfolio purposes.

**Structure:** 
- `@raw\` - Source documentation (never modify)
- `@ROS2\`, other wiki folders - Enriched wiki files with technical content, quick references, and internal Obsidian links

---

## ROS2 Wiki Workflow

### Core Principles

1. **Never modify `@raw\` content** - Source documents are read-only reference material
2. **Synthesize and enrich** - Transform raw docs into structured, actionable wiki content
3. **Task-driven with learning-path foundation** - Start beginner-friendly, evolve toward task-driven as expertise grows
4. **Obsidian linking** - Connect relevant content using `[[filename]]` and `[[filename#Heading]]`
5. **Portfolio-ready** - Every section should demonstrate systematic thinking and technical depth

### Content Organization

**Main wiki file:** `ROS2/ROS2-wiki.md`

**Structure (never change):**
1. What is ROS 2? - Intro and key concepts
2. Quick Start - 5-minute setup with working example
3. Installation - Platform-specific guides
4. **Popular Commands** - Task-organized quick reference (most frequently updated)
5. ROS Learning Path - Structured progression
6. Learning Resources - Official docs + community links
7. Core Concepts - Reference material (grows over time)
8. Troubleshooting - Common issues
9. Content Workflow - Meta documentation

### Content Updates

**When to add/update:**
- New commands discovered → Update Popular Commands section (add task category if needed)
- Learned new concept → Add to Core Concepts or create `ROS2-concepts-<topic>.md`
- Tutorial completed → Create `ROS2-tutorial-<task>.md` with link from Learning Path
- Common issue encountered → Add to Troubleshooting section

**When to create new files:**
- If a concept explanation exceeds 300 lines in main wiki
- If multiple sections link to the same concept
- If creating a deep-dive tutorial or example

**File naming convention:**
- Main: `ROS2-wiki.md`
- Concepts: `ROS2-concepts-<topic>.md` (e.g., `ROS2-concepts-nodes.md`)
- Tutorials: `ROS2-tutorial-<task>.md` (e.g., `ROS2-tutorial-first-package.md`)
- Examples: `ROS2-example-<pattern>.md` (e.g., `ROS2-example-pub-sub.md`)

### Linking Strategy

**Internal links use Obsidian syntax:**
```markdown
[[filename]]              # Link to entire file
[[filename#Heading]]      # Link to specific section
[[#Local Heading]]        # Link to section in current file
```

**Guidelines:**
- Link similar concepts together
- From commands → Link to relevant concept explanation
- From learning path → Link to resources and practical sections
- Cross-wiki links → Link between ROS2, other frameworks, computer science basics (as vault grows)

### Evolution Markers

Use these tags to mark content maturity level:
- `[Beginner]` - Suitable for first learning, minimal prerequisites
- `[Intermediate]` - Builds on beginner knowledge, requires practice
- `[Advanced]` - Deep technical content, assumes experience
- Remove markers as content becomes foundational/universal

### Synthesis from @raw\ Content

When incorporating raw documentation:
1. **Extract key information** - Don't copy verbatim
2. **Organize by purpose** - Group by task, not by source file
3. **Add examples** - Include command examples where applicable
4. **Create links** - Connect to related concepts in wiki
5. **Cite source** - If specific content comes from raw docs, mention the source in comments

**Example workflow:**
```
Raw doc: "Ubuntu (deb packages) — ROS 2 Documentation"
↓
Extract: Installation steps, setup commands, verification steps
↓
Add to: Installation > Ubuntu - Desktop section
↓
Create links: To Quick Start, Popular Commands (setup section)
↓
Preserve: Original file unchanged in @raw\ROS2\
```

---

## General Wiki Guidelines

### Technical Content Standards

- **Include examples** - Code snippets, command examples, configuration samples
- **Show purpose** - Why use this? What problem does it solve?
- **Document edge cases** - Common gotchas, platform differences, version-specific behavior
- **Add troubleshooting** - Common errors and solutions

### Writing Style

- **Concise and scannable** - Use bullet points, tables, headings
- **Progressive disclosure** - Start simple, add complexity gradually
- **Action-oriented** - Focus on "how to do X" not just "what is X"
- **First-person notes** - Add personal learning notes as you progress

### Portfolio Presentation

This wiki demonstrates:
- ✅ Systematic approach to documentation
- ✅ Ability to synthesize complex information
- ✅ Learning progression tracking
- ✅ Knowledge organization skills
- ✅ Technical depth and breadth

Maintain quality across all sections to showcase these strengths to employers.

---

## Commands to Remember

**View current wiki:**
```bash
cat ROS2/ROS2-wiki.md | less
```

**Check for broken links:**
```bash
grep -r "\[\[" ROS2/ | grep -v "^Binary"
```

**See all wiki files:**
```bash
find . -name "*wiki*.md" -o -name "*concepts*.md" -o -name "*tutorial*.md"
```

**Commit wiki updates:**
```bash
git add ROS2/
git commit -m "docs: [section] - Brief description of changes"
```

---

## Quick Checklist for Wiki Updates

Before committing changes:
- [ ] Obsidian links use correct syntax `[[filename#Heading]]`
- [ ] No modifications to `@raw\` files
- [ ] Examples and commands are copy-paste ready
- [ ] Related content is linked together
- [ ] New sections fit into existing structure
- [ ] Writing is concise and scannable
- [ ] Commands tested (if possible)

---

## Future Multi-Wiki Strategy

As your vault grows with other topics (not just ROS):
- Create separate wiki files: `<Topic>/<Topic>-wiki.md`
- Link across wikis when concepts overlap
- Eventually compound wikis may emerge that tie concepts together
- Each wiki follows same principles: synthesize, link, evolve

Example:
```
Robotics Wiki (future compound):
├── ROS2-wiki.md
├── Computer Vision-wiki.md
├── Control Theory-wiki.md
└── Robotics-compound.md (ties all together)
```

---

**Last Updated:** 2026-05-18  
**Version:** 1.0  
**Author Note:** These instructions ensure consistency as the wiki evolves. Update them if workflow changes.
