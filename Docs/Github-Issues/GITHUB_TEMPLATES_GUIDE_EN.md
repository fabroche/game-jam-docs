# 🎯 GitHub Issue Templates Guide for Game Jam

## 📦 Content

You have received **4 professional templates** optimized for game jams:

1. **🎮 Feature Request** - For new features and mechanics
2. **🐛 Bug Report** - For reporting errors and problems
3. **🎨 Asset Request** - For requesting assets (models, animations, audio, UI)
4. **📐 Game Design Task** - For design tasks (level design, balancing, testing)

## 🚀 Installation in your Repository

### Option 1: Through GitHub web interface (Recommended)

1. **Go to your repository on GitHub**
   ```
   https://github.com/your-username/your-repo
   ```

2. **Navigate to Settings → Features**
   - Make sure "Issues" is enabled

3. **Create the templates folder**
   - In the root of your repository, create this structure:
   ```
   .github/
   └── ISSUE_TEMPLATE/
       ├── feature_request.md
       ├── bug_report.md
       ├── asset_request.md
       ├── design_task.md
       └── config.yml
   ```

4. **Copy the content**
   - Open each `.md` file I provided
   - Create the corresponding file on GitHub
   - Copy and paste the content

### Option 2: From local Git (Faster if you already have the repo cloned)

```bash
# From your repository root

# Create folder structure
mkdir -p .github/ISSUE_TEMPLATE

# Copy the files you downloaded
cp /path/to/.github/ISSUE_TEMPLATE/* .github/ISSUE_TEMPLATE/

# Commit and push
git add .github/
git commit -m "feat: add GitHub issue templates for game jam"
git push origin main
```

## 🎨 Customization

### 1. Edit config.yml

**IMPORTANT:** Update these links with your project's:

```yaml
contact_links:
  - name: 💬 General Question or Discussion
    url: https://github.com/YOUR-USERNAME/YOUR-REPO/discussions  # 👈 Change here
    
  - name: 📚 Project Documentation
    url: https://notion.so/YOUR-WORKSPACE  # 👈 Change here
    
  - name: 🎮 Game Jam Community
    url: https://discord.gg/YOUR-SERVER  # 👈 Change here
```

If you don't use any of these (Discord, Notion, Discussions), simply remove that section.

### 2. Customize Labels

The templates use these labels. **Create them in your repo:**

Go to: `Issues → Labels → New label`

| Label | Color | Description |
|-------|-------|-------------|
| 🎮 feature | `#0E8A16` | New functionality |
| 🐛 bug | `#D73A4A` | Error to fix |
| 🎨 art | `#FFA500` | Art assets |
| 🎵 audio | `#9C27B0` | Audio assets |
| 📐 design | `#1E90FF` | Design tasks |
| 🔴 P0-critical | `#B60205` | Critical priority |
| 🟠 P1-high | `#FF6B00` | High priority |
| 🟡 P2-medium | `#FFD700` | Medium priority |
| 🟢 P3-low | `#00FF00` | Low priority |
| 🚀 ready | `#0075CA` | Ready to work |
| 🔒 blocked | `#6A737D` | Blocked |
| 💻 code | `#000000` | Requires programming |
| 🎬 animation | `#E99695` | Requires animation |

**Tip:** You can create these labels automatically with a script. [See automation section](#label-automation).

### 3. Adjust Default Assignees

In each template, you can preconfigure assignees:

```yaml
assignees: 'your-programmer-username'
```

Or leave empty:
```yaml
assignees: ''
```

## 📋 How to Use the Templates

### Creating a New Issue

1. **Go to the Issues tab of your repo**
2. **Click "New Issue"**
3. **Select the appropriate template:**

```
🎮 Feature Request       →  To implement mechanics
🐛 Bug Report           →  To report errors
🎨 Asset Request        →  To request models/audio/UI
📐 Game Design Task     →  For design/testing/balancing
```

4. **Fill in the template** (don't delete sections, even if empty)
5. **Assign labels, milestone, assignee**
6. **Submit issue**

### Recommended Workflow

#### For Features (Programmer):

```markdown
1. Game Designer creates Issue with 🎮 Feature Request template
2. Define acceptance criteria clearly
3. List dependencies (needs assets?)
4. Assign to programmer
5. Programmer accepts and starts development
6. When done, mark subtasks as completed
7. Move to Testing (label or column in Project)
8. Game Designer tests according to template "Testing"
9. If OK → Close issue
   If bugs → Create Bug Report and link
```

#### For Assets (Modeler/Animator):

```markdown
1. Programmer or Designer creates 🎨 Asset Request
2. Specify technical details (polys, format, etc.)
3. Attach visual references
4. Assign to artist
5. Artist creates asset according to specs
6. Export according to template "Export Format"
7. Import to Unity and test
8. Check integration checklist
9. Notify it's ready (mention programmer)
10. Close issue
```

#### For Bugs:

```markdown
1. Anyone who finds a bug creates 🐛 Bug Report
2. Fill in steps to reproduce (VERY IMPORTANT)
3. Assign priority P0/P1/P2/P3
4. If P0-critical → Notify team immediately
5. Programmer investigates and fixes
6. Tester verifies it's fixed
7. Close issue
```

#### For Game Design:

```markdown
1. Designer creates 📐 Game Design Task
2. Specify type (Level Design, Balancing, Testing, etc.)
3. If testing → List test scenarios
4. Execute the task
5. Document results in the same issue
6. If generates necessary changes → Create Feature/Bug issues
7. Close issue when complete
```

## 🏷️ Label System

### Prioritization (use ONLY ONE per issue)

```
🔴 P0-critical  →  Blocks development, must fix NOW
🟠 P1-high      →  Important for MVP, high priority
🟡 P2-medium    →  Notable improvement, medium priority  
🟢 P3-low       →  Nice to have, low priority
```

**Game Jam Rule:** 
- If <24h remain → Only work on P0 and P1
- If <12h remain → Only P0

### Type (can have multiple)

```
🎮 feature      →  New functionality
🐛 bug          →  Error
🎨 art          →  Visual asset
🎵 audio        →  Audio asset
📐 design       →  Design task
```

### Status

```
🚀 ready        →  Ready to start
🔒 blocked      →  Blocked by dependencies
👀 in-review    →  Under review/testing
✅ tested       →  Tested and approved
```

### Required Role

```
💻 code         →  Requires programming
🎨 art-3d       →  Requires modeling
🎬 animation    →  Requires animation
📐 design       →  Requires game design
```

## 🔗 Integration with Notion

To maintain synchronization with Notion:

### In GitHub Issue:
```markdown
### Dependencies
- Notion: TASK-045
```

### In Notion:
```
GitHub Issue: #23
```

**Bidirectional link:** Always include the link from the other system.

## 📊 GitHub Projects (Kanban Board)

### Recommended Setup:

1. **Create a Project in your repo:**
   - Go to Projects → New Project
   - Choose "Board" template

2. **Suggested columns:**
   ```
   📋 Backlog  →  Issues not started
   📝 To Do    →  Prioritized for this sprint
   🔄 In Progress  →  In active development
   🧪 Testing  →  Waiting for testing/review
   ✅ Done     →  Completed
   ```

3. **Automation:**
   - Issue created → Goes to "Backlog"
   - Issue assigned → Goes to "To Do"
   - Issue closed → Goes to "Done"

4. **Workflow:**
   ```
   Backlog → To Do (during daily standup)
   To Do → In Progress (when you start working)
   In Progress → Testing (when you finish)
   Testing → Done (when approved)
   ```

## 🤖 Label Automation

### Script to create labels automatically

Create a file `create-labels.sh`:

```bash
#!/bin/bash

# Colors
RED="#B60205"
ORANGE="#FF6B00"
YELLOW="#FFD700"
GREEN="#00FF00"
BLUE="#0075CA"
PURPLE="#9C27B0"
BLACK="#000000"
GRAY="#6A737D"
PINK="#E99695"

# Your repo (CHANGE HERE)
REPO="your-username/your-repo"

# Types
gh label create "🎮 feature" --color "$GREEN" --description "New functionality" --repo $REPO
gh label create "🐛 bug" --color "$RED" --description "Error to fix" --repo $REPO
gh label create "🎨 art" --color "$ORANGE" --description "Art assets" --repo $REPO
gh label create "🎵 audio" --color "$PURPLE" --description "Audio assets" --repo $REPO
gh label create "📐 design" --color "$BLUE" --description "Design tasks" --repo $REPO

# Priorities
gh label create "🔴 P0-critical" --color "$RED" --description "Critical priority" --repo $REPO
gh label create "🟠 P1-high" --color "$ORANGE" --description "High priority" --repo $REPO
gh label create "🟡 P2-medium" --color "$YELLOW" --description "Medium priority" --repo $REPO
gh label create "🟢 P3-low" --color "$GREEN" --description "Low priority" --repo $REPO

# Status
gh label create "🚀 ready" --color "$BLUE" --description "Ready to work" --repo $REPO
gh label create "🔒 blocked" --color "$GRAY" --description "Blocked" --repo $REPO
gh label create "👀 in-review" --color "$YELLOW" --description "Under review" --repo $REPO
gh label create "✅ tested" --color "$GREEN" --description "Tested and approved" --repo $REPO

# Roles
gh label create "💻 code" --color "$BLACK" --description "Requires programming" --repo $REPO
gh label create "🎨 art-3d" --color "$ORANGE" --description "Requires modeling" --repo $REPO
gh label create "🎬 animation" --color "$PINK" --description "Requires animation" --repo $REPO

echo "✅ Labels created successfully!"
```

**Execute:**
```bash
chmod +x create-labels.sh
./create-labels.sh
```

**Requirement:** Have [GitHub CLI](https://cli.github.com/) installed.

## 💡 Tips and Best Practices

### ✅ DO:
- **Always use templates** - Don't create blank issues
- **Fill in all sections** - Even if you say "N/A"
- **Assign labels correctly** - Especially priority
- **Link related issues** - Use `#number` for auto-link
- **Close issues when TESTED** - Not just when code is done
- **Update issue during development** - Check boxes as you progress

### ❌ DON'T:
- Don't create duplicate issues (search first)
- Don't leave issues unassigned
- Don't use vague language ("fix the game", "improve graphics")
- Don't close bugs without verifying they're fixed
- Don't abuse P0-critical (reserve for real blockers)

### 🎯 During Game Jam:

**Day 1:**
- Create ~10-15 core feature issues
- Assign all with priorities
- Focus on P0 and P1

**Day 2:**
- Create bug issues as they're found
- Create missing asset issues
- Re-prioritize according to progress

**Day 3+ (if applicable):**
- Limit to P0 and P1 only
- Aggressively close P2 and P3 (move to "Post-Jam")

**Last 12 hours:**
- **NO new features**
- Only P0 and P1 bugs
- Focus on visible polish (UI, audio, juice)

## 📱 GitHub Mobile

Templates also work in GitHub mobile app, useful for:
- Reporting bugs on the go
- Creating asset issues while in Blender
- Reviewing and commenting on issues during breaks

## 🆘 Troubleshooting

### "I don't see templates when creating issue"
- Verify files are in `.github/ISSUE_TEMPLATE/`
- Wait 5-10 minutes (GitHub may take time to process)
- Check files have `.md` extension
- Verify YAML front matter is correct

### "Labels don't appear"
- Create labels first in `Issues → Labels`
- Names must match EXACTLY with template

### "I want to modify a template"
- Edit the file in `.github/ISSUE_TEMPLATE/`
- Commit and push
- Changes reflect immediately in new issues

## 🎓 Additional Resources

- [GitHub Issue Templates Documentation](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests/configuring-issue-templates-for-your-repository)
- [GitHub Projects Guide](https://docs.github.com/en/issues/planning-and-tracking-with-projects)
- [GitHub CLI](https://cli.github.com/)

---

## 📞 Frequently Asked Questions

**Q: Can I use these templates outside game jams?**
A: Yes! They're generic but optimized for fast agile development.

**Q: Do I need to use all 4 templates?**
A: No, use only what you need. Minimum recommended is Feature + Bug.

**Q: Can I add more templates?**
A: Yes, follow the same format and add them to `.github/ISSUE_TEMPLATE/`

**Q: Do they work with GitHub Free?**
A: Yes, all these features are free, including Projects.

---

**Good luck with your Game Jam!** 🎮🚀

If you have questions, open an issue using the appropriate template 😉
