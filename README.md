# AI training materials
Repository and collection of materials and stuff I have found and tried, around AI

## Levels of interacting with AI
AI is continously evolving. There are many ways and levels how you can interact with AI. 

This summary is based on this video:
<br>
[![Watch the video](https://img.youtube.com/vi/6W_-YWHKwZ4/hqdefault.jpg)](https://www.youtube.com/embed/6W_-YWHKwZ4)


Stages:

<details><summary>  Stage 1: Chat interface coding </summary>
<br>
What: Having Chat/GPT or Claude open, chatting with the model, having the chat interface open and using it for code. Copying and pasting code

Skills required at this level:
- Good prompting
- Basics of prompt engineering
- What should or should not go into the context window

Time to master this level:
- one week

How you know you have mastered this skill:
- You can write prompts, selectively generate a context and produce output with consistently good results.
</details>

<details><summary>  Stage 2: Mid-loop generation </summary>
<br>

What: Having an AI in your IDE, using auto-complete

Skills:
- Being able to select an adequate code completion
- Troubleshooting with help of the AI
- Use the AI to step by step generate code

Time to master this level:
- Not too long; one or two projects

How you know you have mastered this skill:
- You can work with and grow a code base with the use of a large language model

</details>

<details><summary>  Stage 3: In the loop agentic coding </summary>
<br>

What: Build out the skills to work with an AI, interact, "babysit" the AI

Skills:
- help install guardrails, imporove prompts and skills
- build prompt library
- extract resulable skills, meta prompts, hooks

Time to master this level:
- two or three months

How do you know that you have mastered this level: 
- You see and understand the struggle and problems around the interaction with an AI
- You have a prompt library and meta AI skills and prompts, resuable code and context, hooks

</details>

<details><summary>  Stage 4: On the loop agentic coding </summary>
<br>

What: You spec the work and hand the work over to an AI, then you come back and revisit the work.

Skills:
- You can spec the work correctly
- You can give good prompts that allow the AI to run the work alone
- Multiple Claude sessions in paralell

How you know that you have mastered this skill:
- You can hand off the work to an AI and come back and the outout is correct and of high quaility

</details>

<details><summary>  Stage 5: Multi-agent coding </summary>

Skills:
- Claude code teams

</details>
  

## Claude in yolo mode (in a container)

This repository: https://github.com/con/yolo


## Multi-agentic AI


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

Available shash commands in Claude Code:

- /speckit.constitution - Set project principles/guidelines
- /speckit.specify - Define what you want to build (requirements)
- /speckit.plan - Create technical implementation plan
- /speckit.tasks - Break down into actionable tasks
- /speckit.implement - Execute the implementation
- /speckit.clarify - Clarify underspecified areas
- /speckit.analyze - Cross-check consistency

For example:

- Use /speckit.constitution to establish your scientific computing principles (reproducibility, performance, extensibility)
- Use /speckit.specify to document what velocity centiles should do conceptually (the math, the workflow, expected inputs/outputs)
- Use /speckit.plan to specify your tech stack decisions (pure functions vs classes, xarray structures, config approach)
- Use /speckit.tasks to break down the refactoring into ordered steps
- Use /speckit.implement to execute the transformation

This would give you versioned, documented decision-making for your research code - which is valuable for reproducibility and for onboarding collaborators.

An example project with spec-kit: Building a website on advanced git use.

</details>

<details><summary>  /speckit.constitution </summary>
<br>
Establish principles for an educational Quarto website teaching terminal-based Git 
to rehabilitation science students and researchers. Key principles:

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

</details>

</details>

<details><summary>  /speckit.specify </summary>

Build "Terminal-Based Git for Rehabilitation Research" - a comprehensive Quarto 
website teaching Git exclusively through the command line, starting from terminal 
fundamentals and Git internals.

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

MODULE 2: Basic Git Terminal Workflow
- git init: Starting a repository
- git status: Your constant companion
- git add: Staging changes (what's really happening)
- git commit: Creating snapshots
- git log: Reading history (--oneline, --graph, --all)
- git diff: Comparing states (working vs staged vs committed)
- Writing good commit messages from the terminal
- Hands-on: Version a simple R analysis script
- Terminal output examples with annotations
- Common beginner mistakes and fixes

MODULE 3: Remote Repositories via Terminal
- Cloning: git clone URL
- Understanding remotes: git remote -v
- Pushing: git push origin main
- Pulling: git pull origin main
- Fetch vs pull: git fetch explained
- Authentication: SSH keys vs HTTPS tokens via terminal
- Setting up SSH keys in terminal (ssh-keygen)
- Hands-on: Clone, modify, commit, push a research repository
- Troubleshooting: "rejected" pushes, authentication failures

MODULE 4: Branching in the Terminal
- What branches really are (refs/heads)
- Creating branches: git branch, git checkout -b, git switch -c
- Switching branches: git checkout vs git switch
- Viewing branches: git branch -v, git branch -a
- What happens in .git when you branch
- Branch naming conventions for research
- Hands-on: Create feature branch for new analysis
- Terminal visualization: git log --graph --all --oneline

MODULE 5: Merging and Conflicts via Terminal
- Fast-forward vs three-way merge
- git merge: Combining branches
- What happens during a merge (in .git)
- Understanding merge conflicts
- Conflict markers: <<<<<<<, =======, >>>>>>>
- Resolving conflicts with terminal text editors (nano, vim basics)
- git mergetool for terminal-based resolution
- Continuing merge: git merge --continue
- Aborting merge: git merge --abort
- Hands-on: Create and resolve conflict in analysis script
- Reading git status during conflicts

MODULE 6: Rewriting History with Rebase
- git rebase: Moving branches
- Interactive rebase: git rebase -i
- Squashing commits via terminal
- Reword, edit, drop commits
- When to rebase vs merge
- The golden rule: never rebase published history
- Understanding rebase conflicts
- Hands-on: Clean up messy exploratory analysis commits
- Terminal workflow for interactive rebase

MODULE 7: Advanced Terminal Git Operations
- Viewing commit details: git show
- Searching history: git log -S, git log --grep
- Blame: git blame for line-by-line history
- Stashing: git stash save/pop/list
- Tagging releases: git tag
- Cherry-picking: git cherry-pick
- Viewing file history: git log -- filename
- Hands-on: Use git log to find when bug was introduced

MODULE 8: Data Management via Terminal
- .gitignore: What to exclude and why
- Creating .gitignore from terminal
- Common patterns for research (*.RData, *.pyc, data/)
- git rm --cached: Removing tracked files
- Git LFS commands: git lfs track, git lfs ls-files
- Checking repository size: git count-objects -vH
- Hands-on: Set up .gitignore for R/Python project
- Terminal commands for data hygiene

MODULE 9: Collaborative Workflows in Terminal
- Forking workflow (via GitHub CLI: gh repo fork)
- Feature branch workflow
- Pull requests via terminal: gh pr create, gh pr checkout
- Code review commands: git diff main..feature-branch
- Keeping fork updated: git remote add upstream
- Syncing with upstream: git fetch upstream, git rebase upstream/main
- Hands-on: Simulate multi-person analysis collaboration
- Terminal-based code review workflow

MODULE 10: Troubleshooting via Terminal
- Reading Git error messages
- Undoing changes: git restore, git reset
- Recovering commits: git reflog
- Finding lost work: git fsck --lost-found
- Detached HEAD: understanding and fixing
- Corrupted repository: git fsck
- When to start over: git reset --hard, rm -rf .git
- Hands-on: Deliberate mistakes and terminal-based recovery
- Terminal debugging workflow

MODULE 11: Terminal Integration with Research Tools
- Git in terminal + RStudio workflow
- Git in terminal + Jupyter notebooks
- Viewing diffs for .ipynb files
- Pre-commit hooks via shell scripts
- Git aliases in ~/.gitconfig
- Shell history as documentation (history | grep git)
- Hands-on: Create custom git aliases for common workflows
- Terminal-based research workflow automation

MODULE 12: Professional Research Repositories
- Repository structure via terminal (tree command)
- Writing README.md in terminal editors
- LICENSE files
- Git workflows for reproducible research
- Semantic versioning via git tag
- Archiving for publication: git archive
- Creating releases: gh release create
- Hands-on: Set up complete research repository from terminal
- Terminal checklist for publication-ready repos

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

</details>


<details><summary>  /speckit.plan </summary>

  FRAMEWORK: Quarto
- Version: Latest stable (1.4+)
- Format: Website project
- Theme: Custom based on "darkly" or "cyborg" (terminal aesthetic)
- Code highlighting: Terminal/bash-focused theme

STRUCTURE:
_quarto.yml: 
  - Site navigation with module progression
  - Terminal-friendly theme configuration
  - Search enabled
  - Syntax highlighting for bash, shell, git output

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

</details> 

## Skills.md 

## Claude.md

## Materials:

Yarik's slides: 
https://datasets.datalad.org/centerforopenneuroscience/talks/2026-ca-origami-retreat-aicoding.html#/
