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

Available slash commands in Claude Code:

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


## Skills.md 

## Claude.md
