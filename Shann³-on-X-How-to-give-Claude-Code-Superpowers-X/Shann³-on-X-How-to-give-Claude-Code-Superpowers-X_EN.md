---
title: "Shann³ on X: "How to give Claude Code Superpowers" / X"
source: "https://x.com/shannholmberg/status/2038636871270424794?s=52&t=jjVOMAzDZNfuD4kcqctqJw"
saved_at: "2026-03-31"
tags: ["Claude", "X/Twitter"]
---

# Shann³ on X: "How to give Claude Code Superpowers" / X

Title: Shann³ on X: "How to give Claude Code Superpowers" / X

URL Source: https://x.com/shannholmberg/status/2038636871270424794?s=52&t=jjVOMAzDZNfuD4kcqctqJw

Markdown Content:
After a year of claude code. superpowers is the plugin I wish I had from day one.

it increased speed, quality and removed the frustration of going back and forth with claude on a regular basis.

without it, claude just starts building without asking questions &. writing a plan. sometimes it works, but mostly you end up course-correcting for an hour.

superpowers is an open-source workflow framework by jesse vincent (

). 125,000+ github stars, gaining 15-20K per week.

Shann³

![Image 1](./img_1f035ee6.jpg)

@shannholmberg

claude superpowers is the most underrated plugin for marketers right now 83,000 github stars. trending daily. but almost everyone using it is a developer here´s how it works and how to apply it to marketing ![Image 2: 🧵](./img_32b9d684.svg)

[![Image 3: Image](./img_00761fc5.jpg)](https://x.com/shannholmberg/status/2032892199751528486/photo/1)

think about what a good engineer does with a new task. they dont just start coding. they read the codebase, ask questions, weigh trade-offs, write up an approach, then build.

superpowers gives claude that same process. 14+ skills that kick in based on what you're doing: brainstorming, spec-first planning, TDD, subagent execution, systematic debugging.

the skills are mandatory. if one applies, claude must use it. the framework has a list of 12 excuses developers use to skip workflows.

works with cursor, codex, and gemini CLI.

[![Image 4: Image](./img_31e9410e.jpg)](https://x.com/shannholmberg/article/2038636871270424794/media/2038586793717800960)

superpowers breaks every task into 7 phases. you don't always hit all 7, some tasks only need the first two or three. but the structure is there when you need it.

[![Image 5: Image](./img_06c50fc7.jpg)](https://x.com/shannholmberg/article/2038636871270424794/media/2038617706438545408)

phase 1: brainstorming

this is the one I use the most

before any new feature, superpowers forces a brainstorming session. not "ask a few questions and move on." a full 9-step workflow:

> explore your project context (files, docs, recent commits)

> ask clarifying questions one at a time (never batched, so you actually think about each answer)

> propose 2-3 approaches with trade-offs and a recommendation

> present the design in sections, seek your approval after each

> write a design doc to your project

> self-review the spec for gaps, contradictions, ambiguity

> wait for your explicit approval before moving forward

zero implementation until the design is approved. there´s only one exit from brainstorming: moving to the planning phase.

[![Image 6: Image](./img_33c02aa3.jpg)](https://x.com/shannholmberg/article/2038636871270424794/media/2038604705258151937)

phase 2: planning

once brainstorming is approved, superpowers generates a structured plan with dependencies, acceptance criteria, exact file paths, and order of operations.

the iron rule here: no placeholders allowed. any of these will fail the plan:

> "TBD"

> "TODO"

> "implement later"

> "similar to task above"

every single task has to contain complete, copy-pasteable instructions. the assumption is that whoever executes the plan (usually a subagent) has zero familiarity with your codebase.

strict, yes. but it means you see exactly what claude will build before it writes a single line. you read the plan, tweak anything thats off, approve it, and execution follows the spec.

I've started treating these plans like mini PRDs. they're detailed enough that I could hand one to a subagent and they'd know exactly what to build.

[![Image 7: Image](./img_26cafa40.jpg)](https://x.com/shannholmberg/article/2038636871270424794/media/2038604968010432512)

phase 3: subagent-driven development

claude dispatches subagents for independent tasks, all running in parallel. each subagent gets a fresh context window with no drift from other tasks. the main claude session never writes code itself. it just orchestrates:

> dispatch tasks to subagents

> review what comes back

> track progress against the plan

[![Image 8: Image](./img_0fb3e4f4.jpg)](https://x.com/shannholmberg/article/2038636871270424794/media/2038605725455581184)

phase 4: test-driven development

superpowers enforces what it calls the "iron law": no production code without a failing test first. if code gets written before its test, it gets deleted.

write a failing test, write the simplest code that passes it, refactor. classic TDD loop, but the framework enforces it so you can't skip it when you're in a hurry.

I don't use TDD for everything. for quick prototypes and one-off scripts, I skip this phase. but for anything that needs to be maintained, having tests written before the code means I can refactor later without guessing what's going to break.

[![Image 9: Image](./img_33dca35f.jpg)](https://x.com/shannholmberg/article/2038636871270424794/media/2038606033904652288)

phase 5: two-stage code review

two separate reviews per task. first review checks spec compliance: does the code match what was planned? second review checks code quality. both must pass, and they run as separate reviewer agents so the first review doesnt bias the second.

[![Image 10: Image](./img_3291f60f.jpg)](https://x.com/shannholmberg/article/2038636871270424794/media/2038606317686820864)

phase 6: systematic debugging

when something breaks, superpowers follows a strict protocol:

> reproduce the bug

> isolate the cause

> form one hypothesis (not three)

> make the smallest possible change

> verify

theres a 3-strike rule. if 3 attempted fixes fail, the framework stops trying to patch symptoms and forces you to question the architecture. this prevents the death spiral where claude keeps making small tweaks that don't address the root cause.

[![Image 11: Image](./img_0081324e.jpg)](https://x.com/shannholmberg/article/2038636871270424794/media/2038607945785602048)

phase 7: branch completion

once everything passes, it handles the merge, PR, or cleanup.

My latest example is building our new agency landing page from scratch.

I kicked off a brainstorming session and superpowers started by reading my existing project structure, the design system I had in place, and recent commits. about 5 minutes of back and forth:

> asked about framework preferences

> asked about design constraints

> asked whether I had existing brand assets

> proposed a component structure, animation plan, deployment config

approved the pla and it dispatched agents: one for the hero section, another for the feature grid, another for deployment. 30 minutes and 5 iterations later, the coming soon page was live

Shann³

![Image 12](./img_1f035ee6.jpg)

@shannholmberg

building our new agency LP from scratch. 1. huddled with the team on brand direction. mood boards in Google Flow, type pairings, color palettes. goal was a brand that doesnt scream ai generated but lets us create assets with ai 2. researched frameworks, landed on Astro + Radix

![Image 13](./img_24c8473c.jpg)

without those brainstorming and planning steps, that build would have been hours of me course-correcting claudes assumptions mid-build. I know because I've done similar builds without a framework and spent most of the time doing exactly that.

the brainstorming session front-loaded every decision that would have been a mid-build argument. by the time agents started writing code, there was nothing left to argue about.

install it as a claude code plugin and start your next task normally.

the brainstorming kicks in automatically before any code gets written.

1. answer the brainstorming questions honestly. you'll catch assumptions you didn't know you were making.

2. let it generate a plan. read through it carefully. tweak anything thats off and approve.

3. on a multi-file task, let it dispatch subagents and just watch what happens.

Link to git:

the skills consume context window. on large tasks with lots of existing code, the brainstorming and planning prompts can eat into what claude has available for your actual implementation. I've hit this on a few bigger projects.

for quick one-file fixes, the brainstorming gate is overkill. sometimes you just want to change a color or fix a typo.

it shines on multi-file features and full builds. anything where you'd normally go back and forth with claude for an hour trying to get the architecture right.

0 to 125,000 github stars in months. #1 trending on github.

[![Image 14: Image](./img_146b990f.jpg)](https://x.com/shannholmberg/article/2038636871270424794/media/2038620901617410049)

developers are figuring out that raw prompting has a ceiling. you can write better prompts, add more context, be more specific. but at some point you need structure, not just better input.

follow me

for more on building with ai tools, vibe coding, and agent systems.