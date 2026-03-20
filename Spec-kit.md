## Spec-kit

Spec-Kit is GitHub's toolkit for "Spec-Driven Development",  a methodology where you write detailed specifications first, then use AI agents to implement them. It's designed to work with various AI coding assistants including Claude Code.

How to use Spec-Kit with Claude:

Install the Spec-Kit CLI:

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

Initialize a project with Claude support:

```bash
specify init my-models --ai claude
```

<img width="578" height="420" alt="image" src="https://github.com/user-attachments/assets/ab544e4c-9bd8-4ae1-b487-4b7f0cdfba90" />

Now you are redy to set the parameters for your project:

<img width="654" height="538" alt="image" src="https://github.com/user-attachments/assets/7ac0e0be-4ab0-4e22-9e48-642d7783468a" />

Move into your folder. Launch Claude terminal:

```bash
claude
```

<img width="742" height="538" alt="image" src="https://github.com/user-attachments/assets/2dec2232-bb30-4076-b4c9-4316ed246373" />


# Spec-Kit Command Reference

## Overview

Spec-Kit provides seven slash commands for structured, reproducible software development. These commands are used **inside Claude Code** (not your regular terminal) and create a documented workflow from requirements to implementation.

## The Complete Workflow

```
/speckit.constitution  →  /speckit.specify  →  /speckit.clarify  →  /speckit.plan  →  /speckit.tasks  →  /speckit.analyze  →  /speckit.implement
      ↓                        ↓                      ↓                    ↓                  ↓                    ↓                      ↓
  Project              Feature            Fill gaps          Technical        Task           Quality          Build actual
  principles         requirements        before plan        decisions      breakdown         gate            project files
```

---

## Command Details

### `/speckit.constitution` - Establish Project Principles

**What it does:** Creates the foundational principles and guidelines that govern all development decisions in your project.

**When to use:** First step, before any feature work begins.

**What it creates:**
- `.specify/memory/constitution.md` - Your project's governing document

**Purpose:** 
Establishes consistent decision-making criteria across all features. Like a research protocol that guides methodology choices, the constitution ensures technical decisions align with project values.

**What to include:**
- Pedagogical approach (for educational projects)
- Technical quality standards
- Accessibility requirements
- Research best practices
- Development philosophy
- Quality gates

**Example prompt:**
```
/speckit.constitution Establish principles for an educational Quarto website 
teaching terminal-based Git to rehabilitation science students and researchers. 
Key principles:

PEDAGOGICAL APPROACH:
- Terminal-first: All Git operations taught via command line (no GUI tools)
- Foundations-first: Start with terminal basics and Git mental models before commands
- Progressive complexity: Terminal basics → Git concepts → Basic Git → Advanced Git
- Learn-by-doing: every concept includes hands-on terminal exercises
- Conceptual understanding: Explain the .git directory and Git's internal model
- Error-friendly: teach recovery strategies and how to read error messages
- Context-aware: examples use rehabilitation research workflows

TERMINAL PHILOSOPHY:
- Demystify the command line for researchers from non-CS backgrounds
- Build confidence through small wins
- Teach transferable terminal skills (navigation, file operations)
- Explain why terminal > GUI for reproducibility and documentation

ACCESSIBILITY:
- Assume no prior terminal experience
- Define all jargon and command syntax
- Visual aids showing terminal output with annotations
- Cross-platform guidance (macOS, Linux, Windows/WSL)
- Multiple learning modalities (text, diagrams, terminal screenshots)

TECHNICAL QUALITY:
- All commands tested on macOS, Linux, and Windows (Git Bash/WSL)
- Exact terminal output examples
- Common error messages with explanations
- Copy-pasteable commands with explanations
- Version-controlled with contribution guidelines

RESEARCH BEST PRACTICES:
- Emphasize reproducibility through command-line documentation
- Teach what NOT to version (large data, PHI, credentials)
- Command-line integration with R, Python workflows
- Documentation through commit messages and repository structure
```

**Why it matters:**
- Ensures consistency across all development phases
- Provides rationale for technical decisions
- Documents project values for collaborators
- Acts as a decision-making framework
- Creates reproducible development methodology

---

### `/speckit.specify` - Define What to Build

**What it does:** Creates a detailed specification of **what** you want to build, without specifying **how** to build it.

**When to use:** After constitution is established, as the first step for each new feature.

**What it creates:**
- `specs/001-feature-name/` - New feature directory (numbered sequentially)
- `specs/001-feature-name/spec.md` - Feature specification document
- Git branch: `001-feature-name` (often created automatically)

**Purpose:**
Separates requirements (the "what") from implementation (the "how"). Like a research hypothesis that defines outcomes without prescribing methods, the spec focuses on user needs and desired functionality.

**What to include:**
- Target audience and prerequisites
- Learning objectives or user stories
- Content structure or feature breakdown
- Success criteria
- Design requirements (functional, not technical)
- Examples of desired behavior

**Example prompt:**
```
/speckit.specify Build "Terminal-Based Git for Rehabilitation Research" - 
a comprehensive Quarto website teaching Git exclusively through the command line, 
starting from terminal fundamentals and Git internals.

TARGET AUDIENCE:
- Rehabilitation science grad students, postdocs, researchers
- Little to no terminal/command-line experience
- May have used Git via GUI tools but want deeper understanding
- Need reproducible, documentable workflows for research code

PREREQUISITE KNOWLEDGE:
- Basic computer literacy (file systems, folders)
- No terminal experience required
- No prior Git knowledge required

LEARNING OBJECTIVES:
After completing this tutorial, learners will be able to:
1. Navigate file systems and execute commands in the terminal
2. Understand Git's internal structure (the .git repository)
3. Explain Git's conceptual model (snapshots, commits, branches, HEAD)
4. Perform all basic Git operations via command line
5. Create and manage feature branches from the terminal
6. Resolve merge conflicts using terminal-based tools
7. Use interactive rebase to clean commit history
8. Implement collaborative workflows entirely via command line
9. Handle sensitive research data appropriately
10. Troubleshoot Git issues by understanding internals
11. Document research workflows through Git history

CONTENT STRUCTURE:
MODULE 0: Terminal Fundamentals
- What is the terminal and why researchers should use it
- Opening terminal on macOS, Linux, Windows (Git Bash, WSL)
- Terminal anatomy: prompt, cursor, commands
- Basic navigation: pwd, ls, cd
- File operations: mkdir, touch, cat, rm, mv, cp
- Paths: absolute vs relative
- Command structure: command -flags arguments
- Reading help: --help, man pages
- Common error messages and what they mean
- Hands-on: Navigate your file system, create research project folder
- Why terminal for research: reproducibility, documentation, automation

MODULE 1: Git Conceptual Foundation
- What is version control and why it matters for research
- Git's mental model: snapshots not diffs
- The three states: working directory, staging area, repository
- What's in the .git directory (exploring with terminal)
  - objects/: Git's database (blobs, trees, commits)
  - refs/: Branches and tags
  - HEAD: Your current position
  - config: Repository configuration
  - index: The staging area
- Commits as snapshots with metadata
- The commit graph and history as a DAG
- Branches as movable pointers
- Understanding HEAD and detached HEAD
- Hands-on: Initialize repository, explore .git with ls, cat
- Visual diagrams: Git's internal object model

[Continue with remaining modules...]

WEBSITE FEATURES:
- Terminal command reference sidebar (always visible)
- Syntax highlighting for bash/shell commands
- Annotated terminal output screenshots
- Searchable command index
- Common error messages glossary
- Quick reference: Git commands cheat sheet (downloadable)
- Terminal emulator examples with copy buttons
- Progress tracking per module
- Cross-platform notes (macOS/Linux/Windows differences)

DESIGN REQUIREMENTS:
- Monospace font for all terminal commands
- Color-coded terminal output (matching actual terminal colors)
- Clear visual distinction: commands vs output vs explanations
- Mobile-responsive but optimized for desktop (terminal work)
- Dark mode option (common for terminal users)
- Copy-to-clipboard buttons for all commands
```

**Files in feature directory after `/speckit.specify`:**
```
specs/001-terminal-git-tutorial/
└── spec.md
```

---

### `/speckit.clarify` - Structured Clarification Workflow

**What it does:** Runs a systematic Q&A session to identify and fill gaps in your specification **before** planning begins.

**When to use:** After `/speckit.specify`, before `/speckit.plan` (recommended but optional).

**What it modifies:**
- Updates `spec.md` with a new **"Clarifications"** section

**How it works:**
1. Claude Code analyzes your specification
2. Identifies underspecified, ambiguous, or missing areas
3. Asks targeted questions sequentially
4. Records your answers directly in the spec
5. Continues until all major gaps are addressed

**Example interaction:**
```
> /speckit.clarify

Claude: "I notice Module 5 mentions 'data management' but doesn't specify 
what file sizes should trigger Git LFS vs .gitignore. What threshold 
should we use?"

You: "Files over 50MB should use Git LFS, files over 500MB shouldn't 
be in Git at all."

Claude: "For the terminal screenshots, what annotation style do you prefer? 
Arrows, highlights, numbered steps?"

You: "Use arrows for important commands, highlight output in yellow."

Claude: "Should exercises be scaffolded (step-by-step) or open-ended 
for exploration?"

You: "Start with scaffolded in early modules, transition to open-ended 
by Module 6."

[Claude updates spec.md with a Clarifications section]
```

**What gets added to `spec.md`:**
```markdown
## Clarifications

### Data File Size Thresholds
- Files < 50MB: Track in Git normally
- Files 50MB - 500MB: Use Git LFS
- Files > 500MB: Exclude from Git, document location in README

### Screenshot Annotation Style
- Red arrows for important commands users should notice
- Yellow highlights for output that will be referenced
- Numbered steps for multi-command sequences
- Consistent terminal color scheme across all screenshots

### Exercise Scaffolding Progression
- Modules 0-5: Fully scaffolded step-by-step exercises
- Module 6-8: Partially scaffolded with some open exploration
- Modules 9-12: Open-ended challenges with minimal guidance
```

**Why it's valuable:**
- Catches ambiguities **before** technical planning starts
- Reduces rework during implementation
- Documents decision rationale
- Creates more complete specifications
- Prevents assumptions from becoming bugs

**Best practices:**
- Answer honestly; say "I don't know" if uncertain
- Ask counter-questions if needed
- Request clarification on Claude's questions
- Can run multiple times as spec evolves

---

### `/speckit.plan` - Create Technical Implementation Plan

**What it does:** Defines **how** you'll build what's specified, including technology choices, architecture, and development approach.

**When to use:** After specification is complete and clarified.

**What it creates:**
```
specs/001-terminal-git-tutorial/
├── spec.md                  (already exists)
├── plan.md                  ← Technical implementation plan
├── research.md              ← Background research and rationale
├── quickstart.md            ← Quick start guide for developers
├── data-model.md            ← Content/data structure
├── contracts/               ← Interface specifications (if needed)
└── checklists/              ← Quality assurance checklists
```

**Purpose:**
Translates requirements into concrete technical decisions. Like a research methods section, the plan documents **how** you'll achieve the objectives defined in the spec.

**What `plan.md` includes:**
- Technology stack choices (frameworks, libraries, tools)
- Architecture decisions
- File structure and organization
- Development workflow
- Testing strategy
- Deployment approach
- Feature implementation details

**What `research.md` includes:**
- Technology investigation results
- Comparison of alternatives
- Best practices discovered
- Version compatibility notes
- Links to documentation
- Rationale for choices made

**What `quickstart.md` includes:**
- Development environment setup
- Prerequisites and dependencies
- Quick commands to preview/build
- Common troubleshooting
- How to contribute

**What `data-model.md` includes:**
- Content hierarchy and structure
- Navigation organization
- Metadata schema
- Relationships between components

**Example prompt:**
```
/speckit.plan Use Quarto for the website framework with a clean, 
academic theme optimized for terminal aesthetics. Structure as a 
multi-page site with navigation, search functionality, and code highlighting.

FRAMEWORK: Quarto
- Version: Latest stable (1.4+)
- Format: Website project
- Theme: Custom based on "darkly" or "cyborg" (terminal aesthetic)
- Code highlighting: Terminal/bash-focused theme

STRUCTURE:
_quarto.yml: Site configuration
- Module-based navigation
- Terminal-friendly theme
- Search enabled
- Bash syntax highlighting

index.qmd: Landing page
- Course overview
- Prerequisites (none!)
- Learning path visualization
- Why terminal > GUI for research

modules/:
- 00-terminal-fundamentals.qmd
- 01-git-concepts.qmd
- 02-basic-workflow.qmd
- 03-remotes.qmd
- 04-branching.qmd
- 05-merging.qmd
- 06-rebase.qmd
- 07-advanced-operations.qmd
- 08-data-management.qmd
- 09-collaboration.qmd
- 10-troubleshooting.qmd
- 11-tool-integration.qmd
- 12-professional-repos.qmd

exercises/: Hands-on terminal exercises per module

reference/:
- command-index.qmd (searchable command reference)
- error-messages.qmd (common errors and solutions)
- cheat-sheet.qmd (downloadable PDF)
- glossary.qmd

resources/:
- setup-guides/ (platform-specific setup)
- further-reading.qmd
- git-internals-deep-dive.qmd

SPECIAL FEATURES:
- Terminal code blocks with bash syntax highlighting
- Collapsible "Expected Output" sections
- Platform-specific callouts (macOS/Linux/Windows)
- Mermaid diagrams for .git directory structure
- Annotated terminal screenshots (with arrows, highlights)
- Copy button for all commands
- "Try it yourself" interactive sections

DEPLOYMENT:
- GitHub Pages via GitHub Actions
- Custom domain (optional)
- Automated accessibility checks (terminal contrast)

DEVELOPMENT:
- Local preview: quarto preview
- Validate all commands on multiple platforms
- Screenshot terminal output with consistent styling
- Test copy buttons
```

**Why it's valuable:**
- Explicit technology decisions (reviewable, changeable)
- Documents rationale (prevents "why did we choose X?" later)
- Enables collaboration (others understand architecture)
- Research reproducibility (methods section equivalent)
- Separates "what" from "how"

---

### `/speckit.tasks` - Generate Task Breakdown

**What it does:** Breaks down the implementation plan into ordered, executable tasks with dependencies.

**When to use:** After plan is complete and validated.

**What it creates:**
- `specs/001-terminal-git-tutorial/tasks.md` - Detailed task list

**Purpose:**
Creates a systematic execution roadmap. Like a data collection protocol with step-by-step procedures, the task list ensures nothing is forgotten and work proceeds in the correct order.

**What `tasks.md` includes:**
- Sequential task numbering
- Clear task descriptions
- File paths for each task
- Dependencies between tasks
- Parallel execution markers `[P]`
- Checkpoints for validation
- Organized by user story or module

**Example structure:**
```markdown
# Implementation Tasks

## Phase 1: Project Setup (Tasks 1-5)

### Task 1: Initialize Quarto project structure
- Create base Quarto website project
- Configure _quarto.yml with site metadata
- Dependencies: None
- Files: _quarto.yml

### Task 2: Set up custom theme
- Create styles.css with terminal aesthetic
- Configure dark mode support
- Dependencies: Task 1
- Files: styles.css, _quarto.yml

### Task 3: Configure navigation structure [P]
- Define module hierarchy in _quarto.yml
- Set up sidebar navigation
- Dependencies: Task 1
- Files: _quarto.yml

## Phase 2: Module 0 - Terminal Fundamentals (Tasks 6-10)

### Task 6: Write Module 0 content
- Create modules/00-terminal-fundamentals.qmd
- Include all terminal basics topics from spec
- Add code examples and terminal output
- Dependencies: Task 2, Task 3
- Files: modules/00-terminal-fundamentals.qmd

### Task 7: Create Module 0 exercises [P]
- Create exercises/module-00-exercises.md
- Include hands-on terminal navigation tasks
- Dependencies: Task 6
- Files: exercises/module-00-exercises.md

### Task 8: Add Module 0 screenshots [P]
- Capture annotated terminal screenshots
- Add to modules/00-terminal-fundamentals.qmd
- Dependencies: Task 6
- Files: images/module-00/*.png

[Continue for all 13 modules...]

## Phase N: Testing & Deployment (Tasks 60-65)

### Task 62: Validate all commands cross-platform
- Test commands on macOS, Linux, Windows
- Update platform-specific notes
- Dependencies: All module tasks complete
- Files: All module .qmd files

### Task 63: Set up GitHub Actions deployment
- Create .github/workflows/deploy.yml
- Configure GitHub Pages
- Dependencies: Task 62
- Files: .github/workflows/deploy.yml
```

**Key features:**
- **Dependencies**: Ensures tasks execute in correct order
- **Parallel markers `[P]`**: Identifies tasks that can run simultaneously
- **File paths**: Exact locations for implementation
- **Checkpoints**: Validation steps between phases
- **Phase organization**: Groups related tasks logically

**Why it's valuable:**
- Clear execution roadmap
- Prevents dependency issues
- Enables progress tracking
- Supports iterative development
- Documents implementation sequence

---

### `/speckit.analyze` - Cross-Artifact Consistency Check

**What it does:** Validates consistency and coverage across your spec, plan, and tasks documents.

**When to use:** After `/speckit.tasks`, before `/speckit.implement` (optional quality gate).

**What it creates:**
- `specs/001-terminal-git-tutorial/analysis.md` - Analysis report

**Purpose:**
Quality assurance before implementation begins. Like peer review before data collection, analysis catches gaps, conflicts, and missing pieces that would cause problems during implementation.

**What it checks:**

**Coverage Analysis:**
- ✅ Does every requirement in spec appear in the plan?
- ✅ Does every plan component have corresponding tasks?
- ✅ Are all modules from spec included in tasks?
- ❌ Missing: Requirements without implementation tasks

**Consistency Analysis:**
- ✅ Are technology choices consistent across documents?
- ❌ Conflicts: Spec says X but plan implements Y
- ❌ Contradictions: Different assumptions in different docs

**Completeness Analysis:**
- ✅ All learning objectives covered?
- ❌ Missing: Topics mentioned but not planned
- ❌ Gaps: Implementation details undefined

**Example `analysis.md` output:**
```markdown
# Specification Analysis Report
Generated: 2026-03-20

## Executive Summary
- Total requirements in spec: 156
- Coverage in plan: 148 (94.9%)
- Coverage in tasks: 142 (91.0%)
- Conflicts detected: 3
- Recommendations: 8

## Coverage Matrix

### Spec Requirements → Plan Coverage
✅ Terminal fundamentals module → Covered in plan.md section 2.1
✅ Git concepts module → Covered in plan.md section 2.2
✅ 12 content modules → All covered in plan
❌ Interactive exercises → Mentioned in spec, NO IMPLEMENTATION in plan
✅ GitHub Pages deployment → Covered in plan.md section 4.3
✅ Accessibility (WCAG AA) → Mentioned in plan section 5.2

### Plan Components → Task Coverage
✅ Quarto project setup → Tasks 1-3
✅ Module 0 content → Tasks 6-10
✅ Module 1 content → Tasks 11-15
❌ Custom CSS styling → Referenced in plan, NO TASKS DEFINED
✅ GitHub Actions workflow → Task 63
✅ Cross-platform testing → Task 62

## Conflicts Detected

### CONFLICT 1: Module Count Mismatch
- **Spec**: Lists 13 modules (0-12)
- **Plan**: References only 12 modules in navigation config
- **Impact**: Module 12 might not appear in navigation
- **Recommendation**: Verify module numbering in _quarto.yml configuration

### CONFLICT 2: Accessibility Requirements
- **Spec**: Requires WCAG AA compliance throughout
- **Plan**: Mentions accessibility but deployment section only mentions "contrast checks"
- **Tasks**: No dedicated accessibility validation tasks found
- **Impact**: May not meet stated accessibility requirements
- **Recommendation**: Add accessibility testing tasks (pa11y, axe-core, or manual WCAG checklist)

### CONFLICT 3: Exercise Format
- **Spec**: "Hands-on terminal exercises" (format unspecified)
- **Plan**: Mentions exercises as separate .md files in exercises/ directory
- **Tasks**: Some tasks create exercises, others don't
- **Impact**: Inconsistent exercise availability across modules
- **Recommendation**: Ensure every module has corresponding exercise file

## Missing Components

### From Spec, Not in Plan:
1. ❌ Interactive code execution (mentioned in spec, not addressed in plan)
2. ❌ Progress tracking mechanism (spec mentions checkboxes, no implementation)
3. ❌ Downloadable cheat sheet PDF (spec requirement, not in plan)

### From Plan, Not in Tasks:
1. ❌ Custom CSS for terminal aesthetic (plan section 3.2, no tasks)
2. ❌ Mermaid diagram setup (mentioned in plan, no implementation tasks)
3. ❌ Copy-to-clipboard buttons (plan feature, no tasks)

## Recommendations

### High Priority
1. **Add accessibility validation tasks** - Required by spec, missing from tasks
2. **Define CSS implementation tasks** - Plan references custom styling, needs tasks
3. **Clarify module numbering** - Resolve 12 vs 13 module conflict

### Medium Priority
4. **Add exercise creation for all modules** - Ensure consistency
5. **Define interactive exercise implementation** - If scope includes this
6. **Create downloadable cheat sheet task** - Spec requirement

### Low Priority
7. **Add Mermaid setup task** - If using diagrams as planned
8. **Implement progress tracking** - Nice-to-have from spec

## Readiness Assessment

| Criterion | Status | Notes |
|-----------|--------|-------|
| Spec completeness | ✅ PASS | All major requirements documented |
| Plan coverage | ⚠️ PARTIAL | 94.9% coverage, some gaps |
| Task breakdown | ⚠️ PARTIAL | 91% coverage, missing some plan components |
| Consistency | ❌ FAIL | 3 conflicts need resolution |
| Implementation ready | ⚠️ NOT RECOMMENDED | Address conflicts and gaps first |

## Next Steps

**Before running `/speckit.implement`:**
1. Resolve module numbering conflict
2. Add accessibility testing tasks
3. Add CSS implementation tasks
4. Decide on interactive exercises scope
5. Re-run `/speckit.analyze` to verify fixes
```

**Why it's valuable:**
- Catches problems before implementation
- Prevents wasted development effort
- Ensures nothing from spec gets forgotten
- Validates assumptions across documents
- Quality gate before expensive implementation phase

**Best practice:**
If analysis shows major conflicts or <90% coverage, fix issues and regenerate tasks before implementing.

---

### `/speckit.implement` - Execute Implementation

**What it does:** Reads `tasks.md` and systematically executes every task to build your actual project files.

**When to use:** Final step, after all planning, validation, and analysis complete.

**What it creates:**
**ALL YOUR ACTUAL PROJECT FILES** - the working website, application, or codebase described in your spec.

**For your Git tutorial, creates:**
```
Advanced_Git/
├── .specify/                          (already exists - spec documentation)
│   ├── memory/constitution.md
│   └── specs/001-terminal-git-tutorial/
│       ├── spec.md
│       ├── plan.md
│       ├── tasks.md
│       └── analysis.md
│
├── _quarto.yml                        ← NEW: Site configuration
├── index.qmd                          ← NEW: Landing page
├── styles.css                         ← NEW: Custom terminal theme
│
├── modules/                           ← NEW: All tutorial content
│   ├── 00-terminal-fundamentals.qmd
│   ├── 01-git-concepts.qmd
│   ├── 02-basic-workflow.qmd
│   ├── 03-remotes.qmd
│   ├── 04-branching.qmd
│   ├── 05-merging.qmd
│   ├── 06-rebase.qmd
│   ├── 07-advanced-operations.qmd
│   ├── 08-data-management.qmd
│   ├── 09-collaboration.qmd
│   ├── 10-troubleshooting.qmd
│   ├── 11-tool-integration.qmd
│   └── 12-professional-repos.qmd
│
├── exercises/                         ← NEW: Hands-on exercises
│   ├── module-00-exercises.md
│   ├── module-01-exercises.md
│   └── ... (one per module)
│
├── reference/                         ← NEW: Reference materials
│   ├── command-index.qmd
│   ├── error-messages.qmd
│   ├── cheat-sheet.qmd
│   └── glossary.qmd
│
├── resources/                         ← NEW: Additional resources
│   ├── setup-guides/
│   │   ├── macos.md
│   │   ├── linux.md
│   │   └── windows.md
│   ├── further-reading.qmd
│   └── git-internals-deep-dive.qmd
│
├── images/                            ← NEW: Screenshots and diagrams
│   ├── module-00/
│   ├── module-01/
│   └── ...
│
├── .github/workflows/                 ← NEW: CI/CD
│   └── deploy.yml
│
└── _site/                             ← Generated after quarto render
```

**How it works:**

1. **Parses `tasks.md`**: Reads task structure, dependencies, parallel markers
2. **Executes sequentially**: Follows dependency order, respects `[P]` markers
3. **Creates files**: Writes all content according to specifications
4. **Runs commands**: Executes build/test commands (e.g., `quarto preview`)
5. **Reports progress**: Shows task-by-task completion status
6. **Handles errors**: Stops on failures, allows debugging and continuation

**What you'll see during execution:**

```
> /speckit.implement

Reading implementation plan from tasks.md...
Found 65 tasks across 14 phases.
Analyzing dependencies...
Execution order validated.

Starting implementation...

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Phase 1: Project Setup
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[1/65] Initialize Quarto project structure
  Creating _quarto.yml...
  ✓ File created: _quarto.yml (234 bytes)
  ✓ Project structure initialized

[2/65] Set up custom theme
  Creating styles.css...
  ✓ File created: styles.css (1,847 bytes)
  ✓ Terminal aesthetic theme configured

[3/65] Configure navigation structure [PARALLEL]
  Updating _quarto.yml...
  ✓ Navigation hierarchy configured
  ✓ 13 modules added to sidebar

Phase 1 complete ✓ (3/3 tasks)

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Phase 2: Module 0 - Terminal Fundamentals
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[6/65] Write Module 0 content
  Creating modules/00-terminal-fundamentals.qmd...
  Writing introduction section...
  Writing navigation commands section...
  Writing file operations section...
  Adding code examples and terminal output...
  ✓ File created: modules/00-terminal-fundamentals.qmd (4,293 words)

[7/65] Create Module 0 exercises [PARALLEL]
  Creating exercises/module-00-exercises.md...
  ✓ File created: exercises/module-00-exercises.md (892 words)

[8/65] Add Module 0 screenshots [PARALLEL]
  Creating images/module-00/ directory...
  Note: Screenshot placeholders added. Actual screenshots should be captured manually.
  ✓ Directory created: images/module-00/

Phase 2 complete ✓ (3/3 tasks)

[Progress continues through all 65 tasks...]

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Phase 14: Testing & Deployment
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

[62/65] Validate all commands cross-platform
  Checking command syntax for macOS...
  Checking command syntax for Linux...
  Checking command syntax for Windows/Git Bash...
  ✓ All commands validated

[63/65] Set up GitHub Actions deployment
  Creating .github/workflows/deploy.yml...
  ✓ File created: .github/workflows/deploy.yml
  ✓ GitHub Pages deployment configured

[64/65] Build site locally
  Running: quarto render
  ✓ Site built successfully in _site/

[65/65] Create README with getting started guide
  Creating README.md...
  ✓ File created: README.md

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
Implementation Complete!
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

Summary:
  ✓ 65/65 tasks completed
  ✓ 0 errors
  ✓ 48 files created
  ✓ 32,847 total lines written

Next steps:
  1. Preview your site: quarto preview
  2. Review generated content
  3. Add actual screenshots to images/ directories
  4. Test on multiple platforms
  5. Deploy: git push (GitHub Actions will build automatically)
```

**If errors occur:**

```
[25/65] Write Module 5: Merging and Conflicts
  Creating modules/05-merging.qmd...
  ✗ ERROR: Dependency not satisfied - modules/04-branching.qmd not found

Implementation paused.

Options:
1. Fix the error and continue from this task
2. Skip this task and continue
3. Abort implementation

What would you like to do?
```

You can:
- Investigate and fix the issue
- Ask Claude Code to retry
- Skip problematic tasks
- Abort and fix specifications

**What Claude Code executes:**

From your tasks, it might run:
```bash
# Project setup
quarto create-project . --type website

# Testing
quarto preview  # Local preview server
quarto render   # Build static site

# Git operations
git add .
git commit -m "Add Module 3: Remote Repositories"

# Validation
# (commands to check links, test code examples, etc.)
```

**Progress tracking:**
- Real-time task completion
- File creation notifications
- Error reporting with context
- Ability to pause/resume
- All changes committed to Git incrementally

**Why it's valuable:**
- Systematic execution prevents missed steps
- Progress visibility
- Reproducible build process
- Error handling and recovery
- Documented in Git history
- Can pause and resume
- Validates as it builds

**Time estimate:**
For a project like your Git tutorial (65 tasks, 13 modules, ~50 files):
- **Small projects**: 10-30 minutes
- **Medium projects**: 30-90 minutes
- **Large projects**: 2-4 hours

**Best practice:**
Monitor the implementation, test incrementally, and commit working checkpoints to Git. Don't leave Claude Code unattended for very long implementations.

---

## Files Created Throughout Workflow

### After `/speckit.constitution`:
```
.specify/
└── memory/
    └── constitution.md
```

### After `/speckit.specify`:
```
.specify/
├── memory/constitution.md
└── specs/
    └── 001-terminal-git-tutorial/
        └── spec.md
```

### After `/speckit.clarify`:
```
.specify/
├── memory/constitution.md
└── specs/
    └── 001-terminal-git-tutorial/
        └── spec.md  (updated with Clarifications section)
```

### After `/speckit.plan`:
```
.specify/
├── memory/constitution.md
└── specs/
    └── 001-terminal-git-tutorial/
        ├── spec.md
        ├── plan.md
        ├── research.md
        ├── quickstart.md
        ├── data-model.md
        ├── contracts/
        └── checklists/
```

### After `/speckit.tasks`:
```
.specify/
├── memory/constitution.md
└── specs/
    └── 001-terminal-git-tutorial/
        ├── spec.md
        ├── plan.md
        ├── research.md
        ├── quickstart.md
        ├── data-model.md
        ├── tasks.md  ← New
        ├── contracts/
        └── checklists/
```

### After `/speckit.analyze`:
```
.specify/
├── memory/constitution.md
└── specs/
    └── 001-terminal-git-tutorial/
        ├── spec.md
        ├── plan.md
        ├── research.md
        ├── quickstart.md
        ├── data-model.md
        ├── tasks.md
        ├── analysis.md  ← New
        ├── contracts/
        └── checklists/
```

### After `/speckit.implement`:
```
project_root/
├── .specify/  (documentation, unchanged)
├── _quarto.yml  ← All your actual
├── index.qmd    ← project files
├── modules/     ← created here!
├── exercises/
├── reference/
├── resources/
├── images/
└── .github/
```

---

## Quick Reference Table

| Command | Creates/Modifies | Purpose | Required? |
|---------|------------------|---------|-----------|
| `/speckit.constitution` | `constitution.md` | Project principles | Yes (first) |
| `/speckit.specify` | `spec.md` | Requirements | Yes |
| `/speckit.clarify` | Updates `spec.md` | Fill gaps | Recommended |
| `/speckit.plan` | `plan.md`, `research.md`, etc. | Technical decisions | Yes |
| `/speckit.tasks` | `tasks.md` | Task breakdown | Yes |
| `/speckit.analyze` | `analysis.md` | Quality check | Optional |
| `/speckit.implement` | **All project files** | Build it | Yes (final) |

---

## Example: Research Data Analysis Pipeline

Here's how you might use Spec-Kit for a different type of project:

```
/speckit.constitution
Establish principles for a reproducible data analysis pipeline for 
clinical trial data. Emphasize: data validation, audit trails, 
statistical reproducibility, PHI protection, and clear documentation.

/speckit.specify
Build a Python pipeline for analyzing multi-site rehabilitation 
outcomes data. Must handle: data ingestion from multiple formats, 
validation, normalization, statistical analysis, visualization, 
and automated reporting with full provenance tracking.

/speckit.clarify
[Claude asks about validation rules, statistical methods, etc.]

/speckit.plan
Use Python 3.11+ with pandas, scipy, matplotlib. Implement as 
modular pipeline with DVC for data versioning. Configuration via 
YAML. Testing with pytest. Documentation with Sphinx.

/speckit.tasks
[Generates: setup tasks, module creation tasks, testing tasks, 
documentation tasks, CI/CD tasks]

/speckit.analyze
[Validates all data validation requirements have tests, 
all analysis steps are documented, etc.]

/speckit.implement
[Creates: Python modules, tests, documentation, config files, 
DVC setup, CI/CD workflows]
```

---

## Tips for Effective Spec-Kit Usage

### 1. **Constitution is your north star**
Reference it when making decisions. "Does this align with our principles?"

### 2. **Spec before plan, always**
Resist the urge to specify technologies in `/speckit.specify`. Keep it focused on **what**, not **how**.

### 3. **Use `/speckit.clarify` liberally**
Better to over-clarify than discover ambiguities during implementation.

### 4. **Review generated files**
After each step, read what was created:
```bash
cat specs/001-*/spec.md
cat specs/001-*/plan.md
cat specs/001-*/tasks.md
```

### 5. **Run `/speckit.analyze` for complex projects**
The bigger the project, the more valuable the analysis step becomes.

### 6. **Commit frequently during implementation**
Don't wait until the end. Commit after each phase or module.

### 7. **Iterate when needed**
You can re-run commands to regenerate files as your understanding evolves.

### 8. **Use Git branches**
Spec-Kit creates feature branches automatically. Use them!

---

## Common Questions

**Q: Can I edit the generated files manually?**

A: Yes! All files are yours to edit. Spec-Kit generates starting points, not final artifacts.

**Q: What if I want to change something after `/speckit.implement`?**

A: You can:
1. Edit files directly (small changes)
2. Update spec/plan and re-run `/speckit.tasks` + `/speckit.implement` (major changes)
3. Create a new feature (002-) for significant additions

**Q: Do I need to use all seven commands?**

A: Required: constitution, specify, plan, tasks, implement
Optional: clarify (recommended), analyze (recommended for complex projects)

**Q: Can I use Spec-Kit for non-code projects?**

A: Yes! Documentation sites, research protocols, data pipelines, educational materials—anything with structured requirements benefits from Spec-Kit.

**Q: How is this different from just prompting Claude?**

A: Spec-Kit enforces separation of concerns (what vs how), creates documentation artifacts, ensures systematic implementation, and maintains version-controlled decision rationale. It's structured methodology vs ad-hoc generation.

---

## Materials & Resources

- **Yarik's slides**: https://datasets.datalad.org/centerforopenneuroscience/talks/2026-ca-origami-retreat-aicoding.html
- **Spec-Kit GitHub**: https://github.com/github/spec-kit
- **Spec-Kit Documentation**: https://github.github.io/spec-kit/
