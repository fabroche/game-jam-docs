# 📚 Technical Documentation - Unity 6 Game Jam Team

## Table of Contents
1. [Team Operations](#1-team-operations)
2. [Task Management (Notion + GitHub Issues)](#2-task-management-notion--github-issues)
3. [Game Design Document (GDD) for Game Jams](#3-game-design-document-gdd-for-game-jams)
4. [Operational Action Plan](#4-operational-action-plan)
5. [Appendices and Resources](#5-appendices-and-resources)

---

## 1. Team Operations

### 1.1 Fundamental Principles

#### Golden Rule: "Done is Better than Perfect"
In a game jam, a functional and simple game **always** beats an ambitious unfinished project.

#### Constant Communication
- **Daily Stand-ups:** 10-15 minutes at the start of each day
  - What did I do yesterday?
  - What will I do today?
  - Do I have any blockers?
  
- **Communication Channel:** Use Discord/Slack with specific channels:
  - `#general` - General coordination
  - `#art-assets` - Share models/animations
  - `#code` - Technical problems
  - `#design` - Mechanics and feedback
  - `#builds` - Playable versions

### 1.2 Workflow by Role

```
┌─────────────────────────────────────────────────────────┐
│                    GAME DESIGNER                        │
│  Define concept → Document mechanics → Level design    │
└───────────────────┬─────────────────────────────────────┘
                    ↓
        ┌───────────┴───────────┐
        ↓                       ↓
┌───────────────┐       ┌───────────────┐
│  3D MODELER   │       │  PROGRAMMER   │
│ Create assets │←──────│ Specify       │
│               │       │ needs         │
└───────┬───────┘       └───────┬───────┘
        ↓                       ↓
┌───────────────┐       ┌───────────────┐
│   ANIMATOR    │       │  INTEGRATION  │
│ Rig and anim  │──────→│  IN UNITY     │
└───────────────┘       └───────┬───────┘
                                ↓
                        ┌───────────────┐
                        │ GAME DESIGNER │
                        │ Testing/Level │
                        │   Design      │
                        └───────────────┘
```

### 1.3 Dependency Management

#### Critical Dependencies (Block work)
```
Modeler → Animator → Programmer
   ↓
If the modeler doesn't deliver the character,
the animator CAN'T rig it,
the programmer CAN'T integrate it.
```

**Solution: Temporary Assets (Placeholders)**

**Programmer:**
```csharp
// ALWAYS use placeholders to avoid blocking yourself
// Instead of waiting for the final model:

public class PlayerController : MonoBehaviour
{
    // Placeholder: Unity cube with capsule collider
    // Replace when final model arrives
    
    [Header("References - REPLACE WITH FINAL MODEL")]
    public GameObject visualModel; // Assign cube temporarily
    
    void Start()
    {
        if (visualModel == null)
        {
            Debug.LogWarning("⚠️ Using placeholder - replace with final model");
            CreatePlaceholder();
        }
    }
    
    void CreatePlaceholder()
    {
        GameObject placeholder = GameObject.CreatePrimitive(PrimitiveType.Cube);
        placeholder.transform.SetParent(transform);
        visualModel = placeholder;
    }
}
```

**Modeler:**
- Create a cube/cylinder with correct dimensions FIRST
- Send it to programmer on Day 1
- Work on detailed model in parallel

**Animator:**
- Use Mixamo characters as placeholder
- Export generic animations that work with any humanoid rig

### 1.4 Key Meetings

#### Day 0: Kickoff (2-3 hours)
- Brainstorming the concept
- Define realistic scope
- Assign initial tasks
- Setup repository and Notion

#### Days 1-3: Daily Check-ins (15 min)
- In the morning or afternoon (depending on availability)
- Stand-up format

#### Day 4-5: Internal Playtesting (1 hour)
- Everyone plays the build
- Note bugs and improvements
- Prioritize fixes

#### Last Night: Code Freeze
- **6 hours before deadline:** NO MORE FEATURES
- Only critical fixes
- Continuous testing builds

### 1.5 Conflict Resolution

#### Priority Conflicts
```
Situation: Animator wants to make 10 animations,
programmer only has time to integrate 5.

Solution:
1. Game Designer prioritizes the 5 most important
2. Document the remaining 5 as "Post-Jam Features"
3. Move forward with priorities
```

#### Technical Conflict
```
Situation: Model is too heavy for performance target.

Solution:
1. Programmer measures FPS and identifies the problem
2. Modeler creates Low-Poly version in 1-2 hours
3. If no time, use free backup asset
```

**Escalation Rule:**
- If a problem takes >30 min to discuss → Consult advisor/mentor
- If a problem takes >2 hours to solve → Change approach

---

## 2. Task Management (Notion + GitHub Issues)

### 2.1 Why use both tools?

**Notion:** Design, planning, documentation
**GitHub Issues:** Bugs, technical features, development tracking

```
┌──────────────────────────────────────────────┐
│               NOTION                         │
│  - GDD                                       │
│  - Concept Art                               │
│  - Asset Lists                               │
│  - Meeting Notes                             │
│  - Level Design Sketches                     │
└──────────────────────────────────────────────┘
                    ↕️
        (Mutual reference)
                    ↕️
┌──────────────────────────────────────────────┐
│            GITHUB ISSUES                     │
│  - Feature Implementation                    │
│  - Bug Tracking                              │
│  - Code Reviews                              │
│  - Technical Documentation                   │
└──────────────────────────────────────────────┘
```

### 2.2 Notion Setup

#### Workspace Structure

```
Game Jam Project Workspace
│
├── 📄 Home / Dashboard
│   ├── Countdown Timer
│   ├── Quick Links
│   └── Team Contacts
│
├── 📋 Game Design Document
│   ├── Concept
│   ├── Mechanics
│   ├── Art Style
│   └── Audio
│
├── ✅ Task Board (Kanban)
│   ├── Backlog
│   ├── To Do
│   ├── In Progress
│   ├── Testing
│   └── Done
│
├── 📦 Asset Tracker
│   ├── Models
│   ├── Animations
│   ├── Audio
│   └── UI Elements
│
├── 🐛 Bug Log
│
├── 📅 Schedule & Milestones
│
└── 📚 Resources
    ├── Reference Images
    ├── Tutorials
    └── Asset Sources
```

#### Template: Task Card in Notion

```markdown
# [TASK-001] Implement Player Movement

**Role:** Programmer
**Priority:** 🔴 High
**Status:** In Progress
**Estimation:** 3 hours
**GitHub Issue:** #12

## Description
Implement basic movement system with WASD and jump with Space.

## Requirements
- [ ] Horizontal movement (A/D)
- [ ] Vertical movement (W/S)
- [ ] Jump system
- [ ] Camera rotation with mouse

## Dependencies
- Player placeholder model (TASK-005)

## Assets Needed
- None (use cube placeholder)

## Notes
Use CharacterController instead of Rigidbody for better control.

## References
- [Unity CharacterController Docs](link)
```

#### Database Properties in Notion

For the **Task Board**, create a database with these properties:

| Property | Type | Values |
|----------|------|--------|
| Task Name | Title | - |
| Assignee | Person | Team Members |
| Role | Select | Programmer, Modeler, Animator, Designer |
| Priority | Select | 🔴 High, 🟡 Medium, 🟢 Low |
| Status | Select | Backlog, To Do, In Progress, Testing, Done |
| Estimate | Number | Hours |
| Sprint | Select | Day 1, Day 2, Day 3, Day 4, Day 5, Polish |
| Tags | Multi-select | Core, Polish, Bug, Feature, Art, Code, Audio |
| GitHub Link | URL | - |

### 2.3 GitHub Issues Setup

#### Recommended Labels

```
Type:
🎮 feature        - New functionality
🐛 bug           - Error to fix
🎨 art           - Art assets
🎵 audio         - Audio assets
📚 documentation - Documentation
🔧 refactor      - Code improvement

Priority:
🔴 P0-critical   - Blocks development
🟠 P1-high       - Important for MVP
🟡 P2-medium     - Significant improvement
🟢 P3-low        - Nice to have

Status:
🚀 ready         - Ready to work
🔒 blocked       - Waiting for dependency
👀 in-review     - Under review
✅ tested        - Tested and approved

Role:
💻 code          - Requires programming
🎨 art-3d        - Requires modeling
🎬 animation     - Requires animation
📐 design        - Requires design
```

#### Template: Feature Issue

```markdown
## 🎮 Feature: Basic Combat System

### Description
Implement melee combat system with basic attack.

### Acceptance Criteria
- [ ] Player can press LMB to attack
- [ ] Attack animation plays correctly
- [ ] Attack deals damage to enemies within 2 unit radius
- [ ] There's a 0.5 second cooldown between attacks

### Dependencies
- #15 Animation integration
- Notion: TASK-023 (Attack animation)

### Technical Subtasks
- [ ] Create `MeleeAttack.cs` script
- [ ] Implement collision detection (OverlapSphere)
- [ ] Connect with Animator
- [ ] Add visual feedback (particle effect)

### Required Assets
- Animation: attack_01.fbx
- VFX: hit_spark prefab
- SFX: sword_swing.wav

### Implementation Notes
```csharp
// Example of enemy detection
Collider[] hits = Physics.OverlapSphere(attackPoint.position, attackRadius, enemyLayer);
```

### Estimation
4 hours

### Assigned to
@programmer-username

### Labels
`🎮 feature` `🟠 P1-high` `💻 code` `Day 2`
```

#### Template: Bug Issue

```markdown
## 🐛 Bug: Player falls through floor

### Problem Description
When player jumps near a ramp, sometimes falls through floor into the void.

### Steps to Reproduce
1. Start level 1
2. Go to the ramp near spawn
3. Jump 3-4 times in a row
4. Bug occurs ~50% of the time

### Expected Behavior
Player should collide correctly with the ground.

### Actual Behavior
Player goes through collider and falls.

### Screenshots/Video
[Attach screenshot or GIF]

### Technical Information
- Unity Version: 6.0
- Affected script: `PlayerController.cs`
- Collider: Capsule Collider on player
- Ground: Mesh Collider

### Possible Cause
Mesh Collider may not be convex. Verify configuration.

### Priority
🔴 P0-critical - Breaks gameplay

### Assigned to
@programmer-username

### Labels
`🐛 bug` `🔴 P0-critical` `💻 code`
```

### 2.4 Notion ↔ GitHub Integration Workflow

#### Process: Feature Task

```
1. Game Designer creates task in Notion
   └─→ "TASK-045: Add speed power-up"
   
2. Add details, references, sketch
   
3. Programmer creates Issue in GitHub
   └─→ "#45 Implement Speed Power-up"
   
4. Add GitHub link in Notion
   Notion: "GitHub Issue: #45"
   
5. GitHub Issue includes Notion link
   GitHub: "Design Doc: [Notion Link]"
   
6. Development in GitHub
   - Commits with "#45" for auto-link
   - Code review
   - Merge to dev branch
   
7. Update in Notion
   - Status: Testing
   - Build where it's available
   
8. Game Designer tests
   
9. If OK:
   - Notion: Status → Done
   - GitHub: Close Issue
```

#### Naming Convention

**Notion:**
```
[TASK-XXX] Clear Description
Examples:
- [TASK-001] Implement player movement
- [TASK-002] Model main character
- [TASK-003] Animate walk cycle
- [TASK-004] Design level 1
```

**GitHub:**
```
#XXX Description in English (optional but professional)
Examples:
- #001 Implement player movement
- #002 Create main character model
- #003 Animate walk cycle
- #004 Design level 1
```

**Commits:**
```
git commit -m "feat: add player jump (#001)"
git commit -m "fix: player falling through floor (#023)"
git commit -m "art: add main character model (#002)"
git commit -m "anim: export walk cycle (#003)"

Prefixes:
feat - New feature
fix - Bug fix
art - Art asset
anim - Animation
design - Design change
refactor - Code improvement
docs - Documentation
```

### 2.5 Recommended Daily Workflow

```
🌅 MORNING (9:00 - 9:15)
- Daily stand-up
- Review Notion Task Board
- Move tasks to "In Progress"
- Verify assigned GitHub Issues

💻 WORK (9:15 - 13:00)
- Develop tasks
- Frequent commits
- Update status in real-time

🍕 LUNCH (13:00 - 14:00)
- Break

💻 WORK (14:00 - 18:00)
- Continue development
- Code reviews
- Internal testing

📊 AFTERNOON (18:00 - 18:30)
- Update Notion with progress
- Close completed Issues
- Create Issues for found bugs
- Prepare build if milestone day

🌙 NIGHT (18:30+)
- Flexible time as needed
- In last days: crunch time (optional)
```

---

## 3. Game Design Document (GDD) for Game Jams

### 3.1 What is a GDD?

The **Game Design Document** is the master document that defines what your game is. In a game jam, it should be:
- ✅ Concise (5-10 pages maximum)
- ✅ Visual (sketches, references)
- ✅ Actionable (everyone knows what to do)
- ❌ NOT exhaustive (not an AAA production GDD)

### 3.2 GDD Structure for Game Jam

#### Complete Template

```markdown
# 🎮 [GAME NAME] - Game Design Document

## 📋 General Information

**Title:** [Game Name]
**Jam Theme:** [Theme if applicable]
**Genre:** [Platformer, Puzzle, Shooter, etc.]
**Platform:** PC (Windows/Mac/Linux)
**Game Duration:** 5-10 minutes
**Target Audience:** Casual players

**Team:**
- Game Designer: [Name]
- Programmer: [Name]
- 3D Modeler: [Name]
- Animator: [Name]

**Timeline:**
- Start: [Date]
- End: [Date]
- Duration: 48/72 hours

---

## 🎯 Game Concept

### High Concept (One-liner)
> "It's [Known Game] meets [Another Game], where [Unique Twist]"
>
> Example: "It's Super Mario meets Portal, where you use portals to overcome platforms"

### Core Loop (Central gameplay cycle)
```
1. Player [main action]
   ↓
2. This causes [consequence/challenge]
   ↓
3. Player must [solution/objective]
   ↓
4. Upon completion, gets [reward/progression]
   ↓
[Return to step 1 with higher difficulty]
```

**Example:**
```
1. Player explores the level
   ↓
2. Finds enemies blocking the path
   ↓
3. Must use combat or stealth to overcome them
   ↓
4. Gets key to open door to next level
   ↓
[Next level more difficult]
```

### Pillars (Design pillars)
The 3 fundamental elements that define your game:

1. **[Pillar 1]** - E.g.: "Fluid and satisfying movement"
2. **[Pillar 2]** - E.g.: "Tactical combat based on timing"
3. **[Pillar 3]** - E.g.: "Rewarded exploration"

---

## 🕹️ Mechanics

### Core Mechanics (Essential for MVP)

#### 1. Movement
- **WASD:** 8-directional movement
- **Space:** Jump (height: 2m, duration: 0.5s)
- **Shift:** Sprint (speed x1.5)
- **Mouse:** Camera control (3rd person)

**Technical References:**
- CharacterController
- Base speed: 5 m/s
- Gravity: -20 m/s²

#### 2. Combat
- **LMB:** Basic attack (cooldown: 0.7s)
- **RMB:** Block (reduces damage 50%)
- **Q:** Special ability (cooldown: 5s)

**Damage System:**
- Player HP: 100
- Base attack: 20 damage
- Enemy HP: 50

#### 3. [Another Core Mechanic]
[Detailed description]

### Secondary Mechanics (If there's time)

#### 1. Inventory System
- Capacity: 5 items
- Collectible items: Potions, keys

#### 2. [Another Secondary Mechanic]
[Description]

**⚠️ RULE:** If 24 hours or less remain, DO NOT implement secondary mechanics.

---

## 🎨 Art Direction

### Visual Style
**Reference:** [Link to moodboard in Notion/Pinterest]

**Descriptor:** Colorful low-poly with cell-shaded lighting

**Color Palette:**
- Primary: `#FF6B6B` (Red)
- Secondary: `#4ECDC4` (Turquoise)
- Accent: `#FFE66D` (Yellow)

### 3D Assets

#### Model List (Prioritized)

| Asset | Priority | Triangles | Status | Assignee |
|-------|----------|-----------|--------|----------|
| Player Character | P0 | <5k | To Do | Modeler |
| Enemy Type A | P0 | <3k | To Do | Modeler |
| Floor/Ground Tiles | P0 | <500 | To Do | Modeler |
| Decorative props | P2 | <1k | Backlog | Modeler |

**Performance Budget:**
- Total triangles on screen: <100k
- Draw calls target: <100

### Animations

#### Animation List (Prioritized)

| Animation | Character | Frames | Priority | Status |
|-----------|-----------|--------|----------|--------|
| Idle | Player | 30 | P0 | To Do |
| Walk | Player | 20 | P0 | To Do |
| Run | Player | 16 | P0 | To Do |
| Jump_Start | Player | 8 | P0 | To Do |
| Jump_Loop | Player | 8 | P0 | To Do |
| Jump_Land | Player | 8 | P1 | Backlog |
| Attack_01 | Player | 24 | P0 | To Do |
| Hit_React | Player | 12 | P1 | Backlog |
| Death | Player | 30 | P1 | Backlog |

**⚠️ MINIMUM VIABLE:**
- Idle
- Walk
- Jump (can be a single generic clip)
- Attack

### Audio

#### Needed SFX

| Effect | Trigger | Priority | Source |
|--------|---------|----------|--------|
| Footsteps | When walking | P1 | Freesound.org |
| Jump | When jumping | P1 | Freesound.org |
| Attack_Swing | When attacking | P0 | Mixkit |
| Hit_Impact | Hit enemy | P0 | Freesound.org |
| UI_Click | UI clicks | P2 | Kenney.nl |

#### Music

| Track | Use | Duration | Priority |
|-------|-----|----------|----------|
| Menu Theme | Main menu | 1-2 min loop | P2 |
| Gameplay | During game | 2-3 min loop | P1 |
| Victory | Upon winning | 15-30 sec | P2 |

**Sources:** Incompetech, OpenGameArt, Purple Planet

---

## 🗺️ Level Design

### Level Structure

```
GAME FLOW:
Main Menu → Tutorial → Level 1 → Level 2 → Victory Screen
```

### Level 1: Tutorial
**Objective:** Teach basic mechanics

**Layout:**
```
[START] → [Movement Section] → [Combat Section] → [Miniboss] → [END]
   |            (30s)                 (45s)             (1min)
   |__________________________________________________|
                    ~3 minutes total
```

**Elements:**
- Player spawn
- Instructive NPCs (optional)
- 3-5 practice enemies
- Easy miniboss

**Sketch:** [Link to image in Notion]

### Level 2: Main Challenge
**Objective:** Apply what was learned with higher difficulty

**Layout:** [Description or sketch]

**⚠️ SCOPE:** If time is tight, stay with 1 well-polished level.

---

## 👥 Enemies and NPCs

### Enemy Type A: "Goblin"
**Behavior:**
- Patrol between points A and B
- On detecting player (radius 10m) → Chase
- In range (2m) → Attack
- Lose sight 5s → Return to patrol

**Stats:**
- HP: 50
- Damage: 15
- Speed: 3 m/s
- Attack cooldown: 2s

**AI Script:** SimpleEnemyAI.cs (use NavMesh)

### Enemy Type B: [If there's time]
[Description]

---

## 🎯 Progression and Win/Lose Conditions

### Victory Condition
- Complete all levels
- Defeat final boss
- Collect all objects (if applicable)

### Defeat Condition
- Player HP reaches 0
- Fall into void (insta-kill)
- Timer (if applicable)

### Scoring System (Optional)
- Enemies defeated: +100 pts
- Remaining time: +10 pts/second
- Damage received: -5 pts

---

## 🖥️ UI/UX

### Screens

#### 1. Main Menu
**Elements:**
- Game title (logo)
- "Play" button
- "Options" button (optional)
- "Quit" button
- Team credits

#### 2. HUD (In-game)
**Elements:**
- HP bar (top left corner)
- Enemy counter (top right corner)
- Ability cooldowns (bottom center)
- Minimap (optional, only if time)

**Wireframe:** [Link to sketch in Notion]

#### 3. Pause Menu
**Elements:**
- "Resume"
- "Restart"
- "Main Menu"

#### 4. Game Over Screen
**Elements:**
- "YOU DIED" / "VICTORY"
- Score (optional)
- "Retry"
- "Main Menu"

---

## 📦 Assets and External Resources

### Asset Store / External Sources Assets

| Asset | Source | License | Use |
|-------|--------|---------|-----|
| [Example: TextMesh Pro] | Unity Package | Free | UI Text |
| [Low Poly Water] | Asset Store | Free | Water in levels |

### Third-Party Tools

- **ProBuilder:** Level design
- **DOTween:** UI animations
- **Cinemachine:** Camera control
- **NavMesh Components:** Enemy AI

---

## 🚀 Milestones and Deliverables

### Day 1: Foundation
**Deliverables:**
- [ ] Complete GDD
- [ ] Unity project configured
- [ ] Git repository initialized
- [ ] Placeholder character working
- [ ] Basic movement implemented

**Build Target:** Character walking in empty scene

### Day 2: Core Mechanics
**Deliverables:**
- [ ] Functional combat system
- [ ] Basic enemy AI
- [ ] Player model (low-poly)
- [ ] 3 core animations (idle, walk, attack)
- [ ] Level 1 blocked out (greybox)

**Build Target:** Core gameplay working

### Day 3: Content & Polish
**Deliverables:**
- [ ] All models integrated
- [ ] All animations
- [ ] Level 1 complete and playable
- [ ] Basic UI (menu, HUD)
- [ ] SFX integrated

**Build Target:** Alpha version playable from start to finish

### Day 4: Testing & Polish (If 72h+ Jam)
**Deliverables:**
- [ ] Critical bugs resolved
- [ ] Improved visual/audio feedback
- [ ] Difficulty balancing
- [ ] Level 2 (if time)
- [ ] Music integrated

**Build Target:** Beta version

### Last 6 Hours: Final Push
**Deliverables:**
- [ ] Build for all platforms
- [ ] itch.io page configured
- [ ] Trailer/Screenshots
- [ ] Last testing round
- [ ] Final submit

**🔒 CODE FREEZE 3 HOURS BEFORE DEADLINE**

---

## ⚠️ Risk Management

### Identified Risks

| Risk | Probability | Impact | Mitigation |
|------|------------|--------|------------|
| Scope Creep | High | High | Strict GDD, P0-P2 prioritization |
| Role blockers | Medium | High | Placeholders, daily communication |
| Last-minute bugs | High | Medium | Continuous testing, code freeze |
| Performance issues | Medium | High | 60 FPS target from day 1 |
| Merge conflicts | Medium | Medium | Feature branches, frequent merges |

### Contingency Plan

**If we lose 1 full day of development:**
- Cut secondary mechanics
- Reduce to 1 single level
- Use more free assets
- Simplify art

**If a member cannot continue:**
- Game Designer assumes level design/testing tasks
- Redistribute critical tasks
- Look for free replacement assets

---

## 📚 Technical Glossary

| Term | Definition |
|------|------------|
| Greybox/Blockout | Level built with cubes/basic shapes to test gameplay before final art |
| Placeholder | Temporary asset used to avoid blocking development |
| MVP | Minimum Viable Product - Minimum playable version |
| P0/P1/P2 | Priorities: P0 = Critical, P1 = High, P2 = Low |
| Code Freeze | Moment when features stop being added, only bugs are fixed |

---

## ✅ Pre-Submit Checklist

### 24 Hours Before
- [ ] Build works on all target platforms
- [ ] All P0 bugs resolved
- [ ] All P1 bugs resolved or documented
- [ ] Gameplay loop is satisfying and clear
- [ ] Controls are explained (in-game or on page)

### 12 Hours Before
- [ ] itch.io/GameJolt page complete
- [ ] Quality screenshots (minimum 5)
- [ ] Clear game description
- [ ] Team credits
- [ ] Third-party asset licenses

### 6 Hours Before - CODE FREEZE
- [ ] Final build compiled
- [ ] Build testing (30 min)
- [ ] Gameplay trailer or GIF (optional but recommended)

### 3 Hours Before
- [ ] Build uploaded to platform
- [ ] Verified working links
- [ ] Last visual bug review

### 1 Hour Before
- [ ] Final submit
- [ ] Confirmation screenshot
- [ ] Build backup locally
- [ ] Celebrate 🎉

---

**Version:** 1.0  
**Last Updated:** [Date]  
**Maintained by:** Game Designer
```

---

## 4. Operational Action Plan

### 4.1 Pre-Production (Before Jam)

#### 2 Weeks Before
```
✅ TECHNICAL SETUP
□ Install Unity 6 (everyone)
□ Install Blender (Modeler + Animator)
□ Configure Git + GitHub (everyone)
□ Create itch.io/GameJolt account
□ Test pipeline: Blender → Unity

✅ ORGANIZATION
□ Create Workspace in Notion
□ Import documentation templates
□ Configure Discord/Slack channels
□ Define availability schedules

✅ PRACTICE
□ Do Unity tutorial (Programmer)
□ Do Blender tutorial (Modeler + Animator)
□ Export test FBX (all roles)
□ Make a 2-hour micro-project (optional)
```

#### 1 Week Before
```
✅ PLANNING
□ Research jam theme (if announced)
□ Prepare reference and inspiration list
□ Prepare backup free asset list
□ Do dry-run of kickoff meeting

✅ TOOLS
□ Download useful plugins (ProBuilder, DOTween)
□ Prepare common code libraries
□ Configure Notion/GitHub templates
□ Test communication tools
```

#### 1 Day Before
```
✅ FINAL PREPARATION
□ Sleep well (crucial)
□ Verify all software works
□ Have food/drinks ready
□ Silence non-essential notifications
□ Mentality: "Done > Perfect"
```

### 4.2 Day by Day (48-hour Jam)

#### 🌅 DAY 1: FOUNDATION (0-24h)

##### Hour 0-3: Kickoff & Planning
```
🎯 OBJECTIVES:
- Define game concept
- Create simplified GDD
- Assign initial tasks

⏰ TIMELINE:
00:00 - 00:30 | Brainstorming (everyone together)
  - Jam theme
  - 5 quick ideas
  - Vote for 1

00:30 - 01:30 | Concept refinement
  - Define core loop
  - Identify core mechanics
  - Quick level design sketches

01:30 - 02:30 | Documentation in Notion
  - Game Designer writes base GDD
  - Rest of team adds their role section

02:30 - 03:00 | Task Breakdown
  - Create all tasks in Notion
  - Assign priorities
  - Identify critical dependencies
  - Create GitHub Issues for programming

📦 DELIVERABLES:
□ Complete GDD (80% done)
□ Notion task board populated
□ GitHub Issues created
□ Level design sketches
```

##### Hour 3-8: Setup & First Playable
```
👨‍💻 PROGRAMMER:
□ Create Unity 6 project
□ Configure Git (.gitignore, README)
□ Install essential packages
□ Create test scene
□ Implement basic movement (WASD)
□ Create character placeholder (cube)
□ InputSystem / old Input setup
□ First commit & push

🎨 MODELER:
□ Create character placeholder (cylinder with proportions)
□ Export to Unity for programmer to use
□ Research final character references
□ Begin main character modeling
□ Create color palette

🎬 ANIMATOR:
□ Look for Mixamo character as placeholder
□ Export basic animations (idle, walk, run)
□ Practice export to Unity with placeholder
□ Prepare to rig real model when ready
□ Research rigging tutorials if needed

🎮 GAME DESIGNER:
□ Finalize GDD (100%)
□ Create level 1 greybox in Unity (cubes)
□ Document controls in detail
□ Prepare reference moodboard
□ Create testing checklist

📦 DELIVERABLE: Cube that moves in greybox level
```

##### Hour 8-12: Core Mechanics
```
👨‍💻 PROGRAMMER:
□ Implement jump system
□ Implement camera rotation
□ Create base enemy script (simple AI)
□ Implement basic combat system
□ Setup colliders and layers
□ Integrate placeholder animations

🎨 MODELER:
□ Finish main character (>60% progress)
□ Create simple enemy model
□ Create basic level props (platforms, obstacles)
□ Export to Unity

🎬 ANIMATOR:
□ If model is >60%, begin rigging
□ If not, continue refining placeholder animations
□ Prepare Animation Controller in Unity

🎮 GAME DESIGNER:
□ Iterate greybox with team feedback
□ Begin basic UI (Main Menu sketch)
□ Test early mechanics
□ Document first bugs

📦 DELIVERABLE: Character that jumps, functional camera, basic enemy
```

##### Hour 12-18: Integration
```
👨‍💻 PROGRAMMER:
□ Integrate character model (if ready)
□ Connect animations
□ Implement health system (HP)
□ Implement damage system
□ Create HUD UI (health bar)
□ Control polish

🎨 MODELER:
□ Finalize main character (100%)
□ Basic texturing
□ Create enemy variants (if time)
□ Additional props

🎬 ANIMATOR:
□ Complete character rigging
□ Export final animations
□ Configure Animator Controller
□ Animation events (if applicable)

🎮 GAME DESIGNER:
□ Level design of 50% of level 1
□ Enemy placement
□ Difficulty testing
□ Adjust balance

📦 DELIVERABLE: Final animated character, functional enemy, 50% of level
```

##### Hour 18-24: First Playable Build
```
👨‍💻 PROGRAMMER:
□ Implement Main Menu
□ Pause system
□ Game Over screen
□ Prepare first build
□ Integration testing

🎨 MODELER:
□ Polish existing assets
□ Create secondary assets
□ Help with level design if finishing early

🎬 ANIMATOR:
□ Secondary animations (attack, hit reaction)
□ Animation transitions
□ Timing polish

🎮 GAME DESIGNER:
□ Complete level 1 (100% greybox or with art)
□ SFX integration (placeholder audio)
□ Exhaustive testing
□ Document bugs in GitHub

📦 DELIVERABLE: First playable build from start to finish

🎉 END OF DAY 1
□ 30-min review meeting
□ Build compiled and shared with team
□ Everyone plays the build
□ Make priority list for tomorrow
□ SLEEP (crucial for day 2)
```

#### 🌞 DAY 2: CONTENT & POLISH (24-48h)

##### Hour 24-30: Wake Up & Polish Sprint
```
☕ 24:00 - 24:30 | Morning Review
- Play day 1 build
- Identify 3 critical improvements
- Reprioritize tasks according to progress

👨‍💻 PROGRAMMER:
□ Fix critical bugs
□ Implement audio/visual feedback
□ Particle effects
□ Screen shake
□ Improve game juice

🎨 MODELER:
□ Missing high-priority assets
□ Improve texturing
□ Decorative props
□ Skybox/Environment

🎬 ANIMATOR:
□ Missing animations
□ Improve transitions
□ IK (if time)
□ Facial animations (if applicable and time)

🎮 GAME DESIGNER:
□ Iterate level design with art
□ Add details and polish
□ Integrate real SFX
□ Continuous testing
```

##### Hour 30-36: Feature Complete
```
🎯 OBJECTIVE: All P0 and P1 features implemented

👨‍💻 PROGRAMMER:
□ Last critical features
□ Settings menu (audio volume, etc)
□ Save system (if applicable)
□ Build optimization

🎨 MODELER:
□ All models finalized
□ LODs (if necessary)
□ Final props

🎬 ANIMATOR:
□ All animations exported
□ Timing fine-tuning
□ Help with level 2 if time

🎮 GAME DESIGNER:
□ Level 2 (if time) or polish level 1
□ Music integration
□ Tutorial prompts
□ Victory screen

📦 DELIVERABLE: Feature complete build
```

##### Hour 36-42: Bug Fixing & Balancing
```
🐛 EVERYONE: Focus on stability

□ Intensive playtesting (everyone plays)
□ Document bugs in GitHub
□ Prioritize by severity
□ Fixing sprint

👨‍💻 PROGRAMMER: Fix technical bugs
🎨 MODELER: Fix visual bugs, optimization
🎬 ANIMATOR: Fix animation bugs
🎮 GAME DESIGNER: Balancing, tutorials

⚠️ CRITICAL: Do not add new features
```

##### Hour 42-46: Final Polish
```
✨ POLISH CHECKLIST:
□ Menus work perfectly
□ No obvious visual bugs
□ No critical gameplay bugs
□ Game feels satisfying
□ SFX/Music are at correct levels
□ UI is readable and clear
□ Controls are responsive

👨‍💻 PROGRAMMER:
□ Compile builds for all platforms
□ Test each build
□ Final optimization

🎮 GAME DESIGNER:
□ High-quality screenshots
□ Gameplay GIF
□ Short trailer (30-60s) if time
□ Prepare itch.io description
```

##### Hour 46-48: SUBMISSION
```
⏰ 46:00 - CODE FREEZE
❌ NO MORE CODE CHANGES

46:00 - 47:00 | Final Build & Testing
□ Compile final build
□ Test on clean computer (if possible)
□ Verify no last-minute bugs

47:00 - 47:30 | itch.io Setup
□ Upload build
□ Write description
□ Add screenshots/GIFs
□ Add controls
□ Add team credits
□ Verify game is public

47:30 - 47:45 | Final Testing
□ Download your own game from itch.io
□ Verify it works
□ Have other team members test it

47:45 - 48:00 | SUBMIT
□ Submit to game jam
□ Confirmation screenshot
□ Share link in Discord/Community
□ CELEBRATE 🎉🎉🎉

🎊 POST-JAM
□ Thank the community
□ Play others' submissions
□ Give feedback
□ Rest
```

### 4.3 Contingency Strategies

#### If Running Behind (Hour 30+)

```
🚨 SCOPE CUT DECISION TREE:

Running >6 hours behind?
└─ YES → Cut level 2 completely
        Focus on 1 polished level

Running >12 hours behind?
└─ YES → Cut secondary mechanics
        Only maintain P0

Running >18 hours behind?
└─ YES → EMERGENCY MODE
        ├─ Cut ALL non-core features
        ├─ Use free assets instead of own
        ├─ Reduce animations to minimum
        └─ Goal: Functional loop in 1 level
```

#### If a Member Drops Out

```
MODELER ABSENT:
└─ Use Asset Store/Kenney.nl assets
└─ Animator helps with modeling if knows Blender
└─ More minimalist aesthetic

ANIMATOR ABSENT:
└─ Use Mixamo animations
└─ Programmer integrates pre-made animations
└─ Modeler helps if knows rigging

PROGRAMMER ABSENT:
└─ CRITICAL - Very difficult to recover
└─ Urgently seek external help
└─ Consider using no-code tools (Bolt, PlayMaker)

GAME DESIGNER ABSENT:
└─ Programmer assumes director role
└─ Simplify design to maximum
└─ Everyone contributes to level design
```

### 4.4 Workflow Optimizations

#### Parallel Work Techniques

```
MAXIMUM PARALLELIZATION:

DAY 1 - HOURS 3-12:
┌─────────────────┐  ┌─────────────────┐
│   PROGRAMMER    │  │    MODELER      │
│  Code with      │  │  Model with     │
│  Placeholder    │  │  References     │
└────────┬────────┘  └────────┬────────┘
         │                    │
         └────────┬───────────┘
                  ↓
         ┌────────────────┐
         │    ANIMATOR    │
         │  Placeholder   │
         │   Mixamo       │
         └────────┬───────┘
                  │
                  ↓
         ┌────────────────┐
         │ GAME DESIGNER  │
         │   Greybox      │
         └────────────────┘

NOBODY IS BLOCKED - EVERYONE PROGRESSES
```

#### Unblocking Techniques

```
TECHNIQUE 1: "Assume and Mock"
- Programmer doesn't have model? → Use cube
- Animator doesn't have rig? → Use Mixamo
- Designer doesn't have assets? → Use ProBuilder

TECHNIQUE 2: "Degraded Version"
- No time for 10 enemies? → 1 enemy x10
- No time for cutscene? → Text screen
- No time for music? → SFX only

TECHNIQUE 3: "Good Enough"
- Animation 80% good? → Ship it
- Level not perfect? → Ship it
- Model has small visual bug? → Ship it
```

### 4.5 Crisis Communication

#### When Things Get Tough

```
🔥 HOUR 36 - Still missing P0 features

1. CALL EMERGENCY MEETING (15 min)
   - Everyone stops working
   - Video call or Discord

2. HONEST EVALUATION
   - What P0 features are missing?
   - How many real hours remain?
   - Is it realistic to finish everything?

3. COLLECTIVE DECISION
   - Vote on what to cut
   - Redistribute tasks
   - New clear plan

4. EXECUTE WITHOUT LOOKING BACK
   - Don't lament decisions
   - Focus on what WILL be done
   - Keep morale high
```

#### Phrases to Keep Team Motivated

```
❌ AVOID:
- "We're not going to finish"
- "This is impossible"
- "We should have..."

✅ USE:
- "We're doing well, let's keep going"
- "This is what we can achieve"
- "Let's adjust and continue"
- "We learn for next time"
- "The game will be good this way"
```

---

## 5. Appendices and Resources

### 5.1 Useful Code Snippets

#### Player Movement Controller (Basic)

```csharp
using UnityEngine;

public class PlayerController : MonoBehaviour
{
    [Header("Movement")]
    public float moveSpeed = 5f;
    public float sprintMultiplier = 1.5f;
    public float jumpForce = 5f;
    
    [Header("Ground Check")]
    public Transform groundCheck;
    public float groundDistance = 0.2f;
    public LayerMask groundMask;
    
    private CharacterController controller;
    private Vector3 velocity;
    private bool isGrounded;
    private float gravity = -20f;
    
    void Start()
    {
        controller = GetComponent<CharacterController>();
    }
    
    void Update()
    {
        // Ground check
        isGrounded = Physics.CheckSphere(groundCheck.position, groundDistance, groundMask);
        
        if (isGrounded && velocity.y < 0)
        {
            velocity.y = -2f; // Small negative to keep grounded
        }
        
        // Input
        float horizontal = Input.GetAxis("Horizontal");
        float vertical = Input.GetAxis("Vertical");
        
        Vector3 move = transform.right * horizontal + transform.forward * vertical;
        
        // Sprint
        float currentSpeed = Input.GetKey(KeyCode.LeftShift) ? moveSpeed * sprintMultiplier : moveSpeed;
        
        controller.Move(move * currentSpeed * Time.deltaTime);
        
        // Jump
        if (Input.GetButtonDown("Jump") && isGrounded)
        {
            velocity.y = Mathf.Sqrt(jumpForce * -2f * gravity);
        }
        
        // Apply gravity
        velocity.y += gravity * Time.deltaTime;
        controller.Move(velocity * Time.deltaTime);
    }
}
```

#### Simple Enemy AI

```csharp
using UnityEngine;
using UnityEngine.AI;

public class SimpleEnemyAI : MonoBehaviour
{
    public float detectionRange = 10f;
    public float attackRange = 2f;
    public float attackCooldown = 2f;
    public int damage = 15;
    
    private Transform player;
    private NavMeshAgent agent;
    private float lastAttackTime;
    
    void Start()
    {
        player = GameObject.FindGameObjectWithTag("Player").transform;
        agent = GetComponent<NavMeshAgent>();
    }
    
    void Update()
    {
        float distanceToPlayer = Vector3.Distance(transform.position, player.position);
        
        if (distanceToPlayer <= detectionRange)
        {
            agent.SetDestination(player.position);
            
            if (distanceToPlayer <= attackRange)
            {
                if (Time.time >= lastAttackTime + attackCooldown)
                {
                    Attack();
                    lastAttackTime = Time.time;
                }
            }
        }
    }
    
    void Attack()
    {
        Debug.Log("Enemy attacks player!");
        // Implement damage to player
        // player.GetComponent<PlayerHealth>().TakeDamage(damage);
    }
}
```

#### Health System

```csharp
using UnityEngine;
using UnityEngine.UI;

public class Health : MonoBehaviour
{
    public int maxHealth = 100;
    public int currentHealth;
    public Slider healthBar; // Assign from inspector
    
    void Start()
    {
        currentHealth = maxHealth;
        UpdateHealthBar();
    }
    
    public void TakeDamage(int damage)
    {
        currentHealth -= damage;
        currentHealth = Mathf.Clamp(currentHealth, 0, maxHealth);
        
        UpdateHealthBar();
        
        if (currentHealth <= 0)
        {
            Die();
        }
    }
    
    public void Heal(int amount)
    {
        currentHealth += amount;
        currentHealth = Mathf.Clamp(currentHealth, 0, maxHealth);
        UpdateHealthBar();
    }
    
    void UpdateHealthBar()
    {
        if (healthBar != null)
        {
            healthBar.value = (float)currentHealth / maxHealth;
        }
    }
    
    void Die()
    {
        Debug.Log(gameObject.name + " died!");
        // Implement death logic
        Destroy(gameObject);
    }
}
```

### 5.2 Git Cheat Sheet for Game Jams

```bash
# INITIAL SETUP (Day 0)
git init
git remote add origin <repo-url>
git add .
git commit -m "Initial project setup"
git push -u origin main

# DAILY WORKFLOW
# 1. Before starting to work
git pull origin main

# 2. Work on your code

# 3. See what changes you made
git status

# 4. Add your changes
git add .
# Or specifically:
git add Assets/Scripts/PlayerController.cs

# 5. Commit with descriptive message
git commit -m "feat: add player jump (#001)"

# 6. Push to GitHub
git push origin main

# BRANCHES (Recommended for more experienced teams)
# Create branch for your feature
git checkout -b feature/player-combat

# Work on the branch...

# Merge to main when ready
git checkout main
git merge feature/player-combat

# EMERGENCIES
# Forgot to pull and there are conflicts
git pull origin main
# Resolve conflicts manually in Unity/IDE
git add .
git commit -m "fix: resolve merge conflicts"
git push origin main

# Undo last commit (careful!)
git reset --soft HEAD~1

# View history
git log --oneline
```

### 5.3 Blender to Unity Pipeline

#### Optimal FBX Export from Blender

```
EXPORT SETTINGS IN BLENDER:

1. Select object(s)
2. File → Export → FBX (.fbx)
3. Configure:

[X] Selected Objects Only (if only exporting selected)
[X] Apply Modifiers

Transform:
   Scale: 1.00 (Unity uses same scale)
   Forward: -Z Forward
   Up: Y Up
   [X] Apply Unit
   [X] Apply Transform

Geometry:
   [X] Apply Modifiers
   [ ] Tangent Space (Unity calculates it)
   
Armature:
   [ ] Add Leaf Bones (causes problems in Unity)
   [X] Only Deform Bones

Animation:
   [X] Bake Animation (if has animations)
   [ ] NLA Strips
   [ ] All Actions (only if you want to export all)
```

#### Naming Conventions

```
OBJECTS:
- PlayerCharacter_LP (LP = Low Poly)
- Enemy_Goblin_LP
- Prop_Tree_01
- Weapon_Sword

MATERIALS:
- MAT_Player_Skin
- MAT_Ground_Grass
- MAT_Metal_Rusty

TEXTURES:
- TEX_Player_Diffuse.png
- TEX_Player_Normal.png
- TEX_Ground_Albedo.png
```

#### Common Troubleshooting

```
PROBLEM: Model appears gigantic in Unity
SOLUTION: In Blender, Scale = 1 before exporting
          In Unity Inspector, Scale = 1

PROBLEM: Normals are inverted (black)
SOLUTION: Blender: Select All → Shift+N (Recalculate Normals)

PROBLEM: Rig doesn't work in Unity
SOLUTION: Verify rig is "Humanoid" type in Unity
          FBX Export: "Only Deform Bones" checked

PROBLEM: Textures don't import
SOLUTION: Textures must be in same folder as FBX
          Or embed them: FBX Export → Path Mode: "Copy"
```

### 5.4 Recommended External Resources

#### Free Assets

**3D Models:**
- [Kenney.nl](https://kenney.nl/) - Free low-poly models
- [Poly Haven](https://polyhaven.com/) - Models, textures, HDRIs
- [Quaternius](https://quaternius.com/) - Low-poly assets
- [Mixamo](https://www.mixamo.com/) - Characters and animations

**Textures:**
- [Poly Haven](https://polyhaven.com/textures)
- [CC0 Textures](https://cc0textures.com/)
- [TextureCan](https://www.texturecan.com/)

**Audio (SFX):**
- [Freesound.org](https://freesound.org/)
- [Kenney.nl Audio](https://kenney.nl/assets?q=audio)
- [Mixkit](https://mixkit.co/free-sound-effects/)
- [ZapSplat](https://www.zapsplat.com/)

**Music:**
- [Incompetech](https://incompetech.com/music/)
- [Purple Planet](https://www.purple-planet.com/)
- [OpenGameArt Music](https://opengameart.org/art-search-advanced?keys=&field_art_type_tid%5B%5D=12)

**UI:**
- [Kenney UI Pack](https://kenney.nl/assets/ui-pack)
- [Game-icons.net](https://game-icons.net/)

#### Essential Unity Packages

```
FREE:
- TextMesh Pro (Improved UI Text)
- ProBuilder (Level design in Unity)
- Cinemachine (Cinematic cameras)
- Post Processing Stack (Visual effects)
- Input System (New input system)

PAID (OPTIONAL):
- DOTween Pro ($15 - Tweening animations)
- Odin Inspector ($55 - Better inspector)
```

#### Recommended Tutorials

**Unity Basics:**
- [Brackeys Channel](https://www.youtube.com/c/Brackeys) (YouTube)
- [Unity Learn](https://learn.unity.com/)
- [Catlike Coding](https://catlikecoding.com/unity/tutorials/)

**Blender:**
- [Blender Guru - Donut Tutorial](https://www.youtube.com/watch?v=nIoXOplUvAw)
- [Grant Abbitt Low Poly](https://www.youtube.com/c/GrantAbbitt)

**Game Design:**
- [Game Maker's Toolkit](https://www.youtube.com/c/MarkBrownGMT)
- [Extra Credits](https://www.youtube.com/extracredits)

### 5.5 Notion Templates

#### Template: Task Card (Copy to Notion)

```markdown
# [TASK-XXX] Task Title

**👤 Assignee:** [Name]
**🎭 Role:** [Programmer/Modeler/Animator/Designer]
**⏰ Estimate:** X hours
**🎯 Priority:** P0/P1/P2
**📅 Sprint:** Day X
**🔗 GitHub:** #XXX

## 📝 Description
[Detailed description of what needs to be done]

## ✅ Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## 🔗 Dependencies
- Depends on: [TASK-XXX]
- Blocks: [TASK-XXX]

## 📦 Assets/Resources Needed
- Asset 1
- Resource 2

## 📸 References
[Links to images, tutorials, etc.]

## 🪲 Known Issues
- Issue 1 (if applicable)

## 📝 Notes
Additional developer notes
```

#### Template: Daily Standup (Copy to Notion)

```markdown
# Daily Standup - [Date]

## ⏰ Time: [Time]

### 👨‍💻 Programmer
**Yesterday:**
- [Completed X]
- [Worked on Y]

**Today:**
- [Going to work on Z]
- [Going to implement W]

**Blockers:**
- [Blocked by A] / [No blockers]

---

### 🎨 Modeler
**Yesterday:**
- [Completed X]

**Today:**
- [Going to create Y]

**Blockers:**
- [Waiting for Z feedback] / [No blockers]

---

### 🎬 Animator
**Yesterday:**
- [Rigged character X]

**Today:**
- [Going to animate Y]

**Blockers:**
- [No blockers]

---

### 🎮 Game Designer
**Yesterday:**
- [Designed level X]

**Today:**
- [Going to test Y]

**Blockers:**
- [No blockers]

---

## 🎯 Team Goals for Today
- Goal 1
- Goal 2

## 🚨 Critical Issues
- Issue 1 (if any)
```

---

## 📌 Quick Reference Card (Print This!)

```
╔══════════════════════════════════════════════════════════╗
║        GAME JAM SURVIVAL QUICK REFERENCE                 ║
╚══════════════════════════════════════════════════════════╝

🎯 GOLDEN RULE: Done > Perfect

📅 MILESTONES:
Day 1: First Playable (movement + enemy + level)
Day 2: Feature Complete
Day 2 (Last 6h): Polish Only
3h Before Deadline: CODE FREEZE

🚨 WHEN TO CUT SCOPE:
-6h behind → Cut level 2
-12h behind → Cut secondary mechanics  
-18h behind → EMERGENCY: P0 features only

💬 COMMUNICATION:
- Daily standup: 10-15 min
- Discord/Slack always open
- If problem >30 min → Ask for help
- If problem >2h → Change approach

📁 WORKFLOW:
1. Pull before working
2. Commit frequently with clear messages
3. Push at end of day
4. Notion = Design
5. GitHub = Code

⚠️ EMERGENCIES:
- Critical bug → GitHub Issue P0
- Scope creep → Team meeting
- Member absent → Redistribute tasks
- Tech blocker → Placeholder + continue

🔑 BACKUP ASSETS:
- Models: Kenney.nl, Quaternius
- Animations: Mixamo
- SFX: Freesound.org
- Music: Incompetech

📞 EMERGENCY CONTACTS:
Mentor/Advisor: [Contact]
Discord Server: [Link]
GitHub Repo: [Link]
Notion: [Link]

🎉 REMEMBER:
- Sleep is productive
- Eating well keeps brain active
- Having fun is part of the process
- Game doesn't have to be perfect
- Learning is the real prize

╔══════════════════════════════════════════════════════════╗
║ "The only way to fail a game jam is to not finish"      ║
╚══════════════════════════════════════════════════════════╝
```

---

**END OF DOCUMENT**

---

## 📖 How to Use This Document

### For the Complete Team
1. **Before Jam:** Read entire document at least once
2. **During Jam:** Consult specific sections as needed
3. **In meetings:** Use as reference for decision-making

### For Each Role

**Game Designer:**
- Focus on Sections 1, 3, 4
- Responsible for keeping GDD updated
- Use Notion templates

**Programmer:**
- Focus on Sections 1, 2, 4, 5 (snippets)
- Responsible for GitHub Issues
- Consult technical troubleshooting

**Modeler:**
- Focus on Sections 1, 4, 5 (Blender pipeline)
- Consult naming conventions
- Verify technical specs

**Animator:**
- Focus on Sections 1, 4, 5 (Blender pipeline)
- Coordinate with programmer for animation events
- Use animation checklist

---

**Version:** 1.0  
**Created:** [Date]  
**For:** [Team Name]  
**Game Jam:** [Jam Name]

GOOD LUCK! 🎮🚀
