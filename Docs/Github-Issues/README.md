# GitHub Issue Templates Guide

> Professional issue templates for game jam workflows

## Overview

This section contains comprehensive guides for setting up and using GitHub Issue Templates optimized for Unity 6 game jam projects. The templates streamline task management, bug tracking, asset requests, and design tasks.

## Documentation (Available in multiple languages)

| Language | File | Description |
|----------|------|-------------|
| English | [GITHUB_TEMPLATES_GUIDE_EN.md](./GITHUB_TEMPLATES_GUIDE_EN.md) | Complete setup guide in English |
| Español | [GITHUB_TEMPLATES_GUIDE_ES.md](./GITHUB_TEMPLATES_GUIDE_ES.md) | Guía completa de configuración en español |
| Italiano | [GITHUB_TEMPLATES_GUIDE_IT.md](./GITHUB_TEMPLATES_GUIDE_IT.md) | Guida completa alla configurazione in italiano |

## Included Templates

### 🎮 Feature Request
For implementing new gameplay mechanics, systems, and functionalities.

**What's included:**
- Feature description section
- Acceptance criteria checklist
- Dependencies tracking
- Technical subtasks
- Asset requirements
- Implementation notes
- Testing guidelines

### 🐛 Bug Report
For tracking and fixing errors discovered during development.

**What's included:**
- Problem description
- Steps to reproduce
- Expected vs actual behavior
- Screenshots/video support
- Technical information
- Possible cause analysis
- Priority assignment

### 🎨 Asset Request
For requesting 3D models, animations, audio, and UI elements.

**What's included:**
- Asset type categorization (Model, Animation, Audio, UI)
- Technical specifications (polycount, format, duration)
- Visual references
- Export format checklist
- Unity integration steps
- Performance considerations

### 📐 Game Design Task
For level design, game balancing, playtesting, and design documentation.

**What's included:**
- Task type classification
- Design objectives
- Implementation details
- Testing scenarios
- Balance considerations
- Documentation requirements

## Quick Setup

1. **Choose your language** and open the corresponding guide
2. **Follow the installation instructions** to copy templates to your repository
3. **Create the required labels** (automation script provided in the guide)
4. **Configure GitHub Projects** for kanban board workflow
5. **Start using templates** for all issues!

## Label System

The templates use a comprehensive label system:

### Priority Labels
- 🔴 **P0-critical** - Blocks development, must be fixed immediately
- 🟠 **P1-high** - Important for MVP, high priority
- 🟡 **P2-medium** - Notable improvement, medium priority
- 🟢 **P3-low** - Nice to have, low priority

### Type Labels
- 🎮 **feature** - New functionality
- 🐛 **bug** - Error to fix
- 🎨 **art** - Art assets
- 🎵 **audio** - Audio assets
- 📐 **design** - Design tasks

### Status Labels
- 🚀 **ready** - Ready to start
- 🔒 **blocked** - Blocked by dependencies
- 👀 **in-review** - Under review/testing
- ✅ **tested** - Tested and approved

### Role Labels
- 💻 **code** - Requires programming
- 🎨 **art-3d** - Requires 3D modeling
- 🎬 **animation** - Requires animation
- 📐 **design** - Requires game design

## Workflow Integration

These templates integrate seamlessly with:

- **Notion** - Link GitHub issues to Notion tasks for complete documentation
- **GitHub Projects** - Use kanban boards for visual task management
- **Git Commits** - Reference issues in commit messages for automatic linking
- **Pull Requests** - Link PRs to issues for complete traceability

## Game Jam Specific Features

The templates are optimized for game jam constraints:

- **Time-boxed workflows** - Quick creation with all essential information
- **Priority-based** - Clear P0-P3 system for rapid decision making
- **Role-specific** - Tailored for Game Designer, Programmer, 3D Modeler, and Animator
- **Dependency tracking** - Prevent blocking between team members
- **Scope management** - Built-in checklists to prevent scope creep

## Benefits

### For Game Designers
- Clear feature specifications
- Structured design documentation
- Easy playtesting coordination
- Balance tracking

### For Programmers
- Technical requirements clarity
- Dependency management
- Bug reproduction steps
- Testing criteria

### For 3D Artists
- Precise technical specifications
- Export format guidelines
- Performance budgets
- Integration checklists

### For Animators
- Animation requirements
- Frame counts and timing
- Rig specifications
- Export settings

## Best Practices

1. **Always use templates** - Don't create blank issues
2. **Fill all sections** - Even if you write "N/A"
3. **Assign labels correctly** - Especially priority labels
4. **Link related issues** - Use `#number` for auto-linking
5. **Close when tested** - Not just when code is done
6. **Update during development** - Check off boxes as you progress

## Game Jam Timeline

### Day 1
- Create ~10-15 issues for core features
- Assign all with priorities
- Focus on P0 and P1

### Day 2
- Create issues for bugs as found
- Create issues for missing assets
- Re-prioritize based on progress

### Last 24 Hours
- Limit to P0 and P1 only
- Close P2 and P3 aggressively

### Last 12 Hours
- **NO new features**
- Only P0 and P1 bugs
- Focus on visible polish

## Support

For detailed setup instructions, automation scripts, troubleshooting, and advanced workflows, see the complete guide in your preferred language above.

## Repository Structure

```
.github/
└── ISSUE_TEMPLATE/
    ├── feature_request.md
    ├── bug_report.md
    ├── asset_request.md
    ├── design_task.md
    └── config.yml
```

All template files are included in the guides and ready to copy to your repository.

---

**Choose your language guide above to get started!**
