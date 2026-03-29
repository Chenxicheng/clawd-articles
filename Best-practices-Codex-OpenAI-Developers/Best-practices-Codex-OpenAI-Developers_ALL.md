---
title: ""
source: ""
saved_at: "2026-03-28"
tags: ["AI", "Article"]
---

# 

# Best practices – Codex | OpenAI Developers

If you're new to Codex or coding agents in general, this guide will help you get better results faster. It covers the core habits that make Codex more effective across the CLI, IDE extension, and the Codex app, from prompting and planning to validation, MCP, skills, and automations.

Codex works best when you treat it less like a one-off assistant and more like a teammate you configure and improve over time.

A useful way to think about this: start with the right task context, use AGENTS.md for durable guidance, configure Codex to match your workflow, connect external systems with MCP, turn repeated work into skills, and automate stable workflows.

## Strong first use: Context and prompts

Codex is already strong enough to be useful even when your prompt isn't perfect. You can often hand it a hard problem with minimal setup and still get a strong result. Clear prompting isn't required to get value, but it does make results more reliable, especially in larger codebases or higher-stakes tasks.

If you work in a large or complex repository, the biggest unlock is giving Codex the right task context and a clear structure for what you want done.

A good default is to include four things in your prompt:

- Goal: What are you trying to change or build?
- Context: Which files, folders, docs, examples, or errors matter for this task? You can @ mention certain files as context.
- Constraints: What standards, architecture, safety requirements, or conventions should Codex follow?
- Done when: What should be true before the task is complete, such as tests passing, behavior changing, or a bug no longer reproducing?

This helps Codex stay scoped, make fewer assumptions, and produce work that's easier to review.

Choose a reasoning level based on how hard the task is and test what works best for your workflow. Different users and tasks work best with different settings.

- Low for faster, well-scoped tasks
- Medium or High for more complex changes or debugging
- Extra High for long, agentic, reasoning-heavy tasks

To provide context faster, try using speech dictation inside the Codex app to dictate what you want Codex to do rather than typing it.

If the task is complex, ambiguous, or hard to describe well, ask Codex to plan before it starts coding.

A few approaches work well:

Use Plan mode: For most users, this is the easiest and most effective option. Plan mode lets Codex gather context, ask clarifying questions, and build a stronger plan before implementation. Toggle with /plan or Shift+Tab.

Ask Codex to interview you: If you have a rough idea of what you want but aren't sure how to describe it well, ask Codex to question you first. Tell it to challenge your assumptions and turn the fuzzy idea into something concrete before writing code.

Use a PLANS.md template: For more advanced workflows, you can configure Codex to follow a PLANS.md or execution-plan template for longer-running or multi-step work.

Once a prompting pattern works, the next step is to stop repeating it manually. That's where AGENTS.md comes in.

Think of AGENTS.md as an open-format README for agents. It loads into context automatically and is the best place to encode how you and your team want Codex to work in a repository.

A good AGENTS.md covers:

- repo layout and important directories
- How to run the project
- Build, test, and lint commands
- Engineering conventions and PR expectations
- Constraints and do-not rules
- What done means and how to verify work

The /init slash command in the CLI is the quick-start command to scaffold a starter AGENTS.md in the current directory. It's a great starting point, but you should edit the result to match how your team actually builds, tests, reviews, and ships code.

You can create AGENTS.md files at different levels: a global AGENTS.md for personal defaults that sits in ~/.codex, a repo-level file for shared standards, and more specific files in subdirectories for local rules. If there's a more specific file closer to your current directory, that guidance wins.

Keep it practical. A short, accurate AGENTS.md is more useful than a long file full of vague rules. Start with the basics, then add new rules only after you notice repeated mistakes.

If AGENTS.md starts getting too large, keep the main file concise and reference task-specific markdown files for things like planning, code review, or architecture.

When Codex makes the same mistake twice, ask it for a retrospective and update AGENTS.md. Guidance stays practical and based on real friction.

## Configuration

Configuration is one of the main ways to make Codex behave more consistently across sessions and surfaces. For example, you can set defaults for model choice, reasoning effort, sandbox mode, approval policy, profiles, and MCP setup.

A good starting pattern is:

- Keep personal defaults in ~/.codex/config.toml
- Keep repo-specific behavior in .codex/config.toml
- Use command-line overrides only for one-off situations

config.toml is where you define durable preferences such as MCP servers, profiles, multi-agent setup, and feature flags. You can edit it directly or ask Codex to update it for you.

Codex ships with operating level sandboxing and has two key knobs that you can control. Approval mode determines when Codex asks for your permission to run a command and sandbox mode determines if Codex can read or write in the directory and what files the agent can access.

If you're new to coding agents, start with the default permissions. Keep approval and sandboxing tight by default, then loosen permissions only for trusted repos or specific workflows once the need is clear.

## Validate your work

Configure Codex for your real environment early. Many quality issues are really setup issues, like the wrong working directory, missing write access, wrong model defaults, or missing tools and connectors.

Don't stop at asking Codex to make a change. Ask it to create tests when needed, run the relevant checks, confirm the result, and review the work before you accept it.

Codex can do this loop for you, but only if it knows what "good" looks like. That guidance can come from either the prompt or AGENTS.md.

That can include:

- Writing or updating tests for the change
- Running the right test suites
- Checking lint, formatting, or type checks
- Confirming the final behavior matches the request
- Reviewing the diff for bugs, regressions, or risky patterns

A useful option here is the slash command /review, which gives you a few ways to review code:

- Review against a base branch for PR-style review
- Review uncommitted changes
- Review a commit
- Use custom review instructions

## Use MCPs for external context

Use MCPs when the context Codex needs lives outside the repo. It lets Codex connect to the tools and systems you already use, so you don't have to keep copying and pasting live information into prompts.

Model Context Protocol (MCP) is an open standard for connecting Codex to external tools and systems.

Use MCP when:

- The needed context lives outside the repo
- The data changes frequently
- You want Codex to use a tool rather than rely on pasted instructions
- You need a repeatable integration across users or projects

Add tools only when they unlock a real workflow. Do not start by wiring in every tool you use. Start with one or two tools that clearly remove a manual loop you already do often, then expand from there.

## Skills

Once a workflow becomes repeatable, stop relying on long prompts or repeated back-and-forth. Use a Skill to package the instructions in a SKILL.md file, context, and supporting logic Codex should apply consistently. Skills work across the CLI, IDE extension, and Codex app.

Keep each skill scoped to one job. Start with 2 to 3 concrete use cases, define clear inputs and outputs, and write the description so it says what the skill does and when to use it.

Don't try to cover every edge case up front. Start with one representative task, get it working well, then turn that workflow into a skill and improve from there.

Skills are especially useful for recurring jobs like:

- Log triage
- Release note drafting
- PR review against a checklist
- Migration planning
- Telemetry or incident summaries
- Standard debugging flows

Personal skills are stored in $HOME/.agents/skills, and shared team skills can be checked into .agents/skills inside a repository.

## Automations

Once a workflow is stable, you can schedule Codex to run it in the background for you. In the Codex app, automations let you choose the project, prompt, cadence, and execution environment for a recurring task.

Good candidates include:

- Summarizing recent commits
- Scanning for likely bugs
- Drafting release notes
- Checking CI failures
- Producing standup summaries
- Running repeatable analysis workflows on a schedule

A useful rule is that skills define the method, automations define the schedule. If a workflow still needs a lot of steering, turn it into a skill first. Once it's predictable, automation becomes a force multiplier.

Use automations for reflection and maintenance, not just execution. Review recent sessions, summarize repeated friction, and improve prompts, instructions, or workflow setup over time.

## Session management

Codex sessions aren't just chat history. They're working threads that accumulate context, decisions, and actions over time, so managing them well has a big impact on quality.

Keep one thread per coherent unit of work. If the work is still part of the same problem, staying in the same thread is often better because it preserves the reasoning trail. Fork only when the work truly branches.

Use Codex's subagent workflows to offload bounded work from the main thread. Keep the main agent focused on the core problem, and use subagents for tasks like exploration, tests, or triage.

## Common mistakes to avoid

A few common mistakes to avoid when first using Codex:

- Overloading the prompt with durable rules instead of moving them into AGENTS.md or a skill
- Not letting the agent see its work by not giving details on how to best run build and test commands
- Skipping planning on multi-step and complex tasks
- Giving Codex full permission to your computer before you understand the workflow
- Running live threads on the same files without using git worktrees
- Turning a recurring task into an automation before it's reliable manually
- Treating Codex like something you have to watch step by step instead of using it in parallel with your own work
- Using one thread per project instead of one thread per task. This leads to bloated context and worse results over time

---

## 中文

---
title: ""
source: ""
saved_at: "2026-03-28"
tags: ["AI", "Article"]
---

# 

# 最佳实践 – Codex | OpenAI 开发者

如果你刚接触 Codex 或编码 Agent，本指南将帮助你更快获得更好的结果。它涵盖了使 Codex 在 CLI、IDE 扩展和 Codex 应用中更有效的核心习惯，从提示工程、规划到验证、MCP、Skills 和自动化。

Codex 最好的使用方式是将它视为一个你可以长期配置和改进的团队成员，而不是一次性助手。

一个有用的思路是：从正确的任务上下文开始，使用 AGENTS.md 进行持久化指导，配置 Codex 以匹配你的工作流程，通过 MCP 连接外部系统，将重复性工作转化为 Skills，并自动化稳定的工作流程。

## 强大的首次使用：上下文和提示

Codex 已经足够强大，即使提示不完美也能提供帮助。你可以经常给它一个很难的问题，最小化设置，依然获得强劲的结果。清晰的提示不是获得价值的必要条件，但在更大的代码库或更高风险的任务中，它确实能让结果更可靠。

如果你工作在大型或复杂的代码库中，最大的突破是给 Codex 正确的任务上下文和清晰的结构。

一个好的默认做法是在提示中包含四件事：

- 目标：你想要改变或构建什么？
- 上下文：哪些文件、文件夹、文档、示例或错误对这个任务重要？
- 约束条件：Codex 应该遵循哪些标准、架构、安全要求或约定？
- 完成条件：任务完成前应该是什么样子？

这有助于 Codex 保持范围，减少假设，并产生更容易审查的工作。

根据任务的难度选择推理级别，并测试什么最适合你的工作流程。

- Low：更快、范围更小的任务
- Medium 或 High：更复杂的更改或调试
- Extra High：漫长的、Agent 性的、推理密集型的任务

如果任务复杂、模糊或难以描述，请在 Codex 开始编码之前要求它制定计划。

## AGENTS.md

AGENTS.md 是 Agents 的开放式格式 README。它自动加载到上下文中，是编码你和你的团队希望 Codex 在仓库中如何工作的最佳位置。

一个好的 AGENTS.md 涵盖：

- 仓库布局和重要目录
- 如何运行项目
- 构建、测试和 lint 命令
- 工程约定和 PR 期望
- 约束和禁止规则
- 完成的定义以及如何验证

/init slash 命令是 CLI 中的快速启动命令，可在当前目录中搭建起始 AGENTS.md。这是一个很好的起点，但你应该编辑结果以匹配你的团队实际构建、测试、审查和发布代码的方式。

保持实用。简短准确的 AGENTS.md 比冗长的模糊规则文件更有用。从基础知识开始，然后在注意到重复错误后才添加新规则。

## 配置

配置是使 Codex 在不同会话和表面上更一致地行为的主要方式之一。例如，你可以设置模型选择、推理努力、沙盒模式、审批策略、配置文件和 MCP 设置的默认值。

一个好的起点模式是：

- 将个人默认值保存在 ~/.codex/config.toml 中
- 将仓库特定行为保存在 .codex/config.toml 中
- 仅在一次性的情况下使用命令行覆盖

config.toml 是定义持久偏好设置的地方，如 MCP 服务器、配置文件、多代理设置和功能开关。

Codex 附带操作系统级别的沙盒，有两个你可以控制的关键旋钮。审批模式决定 Codex 何时请求你运行命令的权限，沙盒模式决定 Codex 是否可以读取或写入目录以及代理可以访问哪些文件。

如果你刚接触编码 Agent，请从默认权限开始。默认保持审批和沙盒严格，然后在需要时仅对可信仓库或特定工作流程放宽权限。

## 验证你的工作

尽早为你的真实环境配置 Codex。许多质量问题实际上是设置问题，比如错误的工作目录、缺少写入权限、错误的模型默认值或缺少工具和连接器。

不要仅仅要求 Codex 做出更改就停止。要求它在需要时创建测试，运行相关检查，确认结果，并在接受工作之前审查它。

## 使用 MCP 获取外部上下文

当 Codex 需要的上下文存在于仓库外部时，使用 MCP。它让你将 Codex 连接到你已经使用的工具和系统，这样你就不必不断地将实时信息粘贴到提示中。

模型上下文协议 (MCP) 是一个开放标准，用于将 Codex 连接到外部工具和系统。

仅在真正开启真实工作流程时添加工具。不要一开始就将你使用的每个工具连接起来。从一两个能明显消除你经常手动循环的工具开始，然后再扩展。

## Skills

一旦工作流程可重复，就停止依赖冗长的提示或反复来回。将工作流程包装在 SKILL.md 文件、上下文和支持逻辑中，使 Codex 能够一致地应用。Skills 在 CLI、IDE 扩展和 Codex 应用中都能工作。

每个 Skill 保持范围单一。从 2 到 3 个具体的用例开始，定义清晰的输入和输出，并写好描述，说明 Skill 做什么以及何时使用。

不要试图在一开始就覆盖每个边缘情况。从一个代表性的任务开始，使其良好运行，然后将那个工作流程转化为 Skill 并从中改进。

一个好的经验法则是：如果你不断重用相同的提示或纠正相同的工作流程，它可能应该成为一个 Skill。

## 自动化

一旦工作流程稳定，你可以安排 Codex 在后台为你运行它。在 Codex 应用中，自动化让你为重复任务选择项目、提示、节奏和执行环境。

好的候选包括：

- 总结最近的提交
- 扫描可能的 bug
- 起草发布说明
- 检查 CI 失败
- 生成站会摘要
- 按计划运行重复性分析工作流程

一个有用的规则是：Skills 定义方法，自动化定义时间表。如果工作流程仍然需要很多引导，先把它变成一个 Skill。一旦可预测，自动化就成为力量倍增器。

## 会话管理

Codex 会话不仅仅是聊天历史。它们是积累上下文、决策和行动的工乍线程，因此管理好它们对质量有很大影响。

每个连贯的工作单元保持一个线程。如果工作仍然是同一问题的一部分，保持在同一个线程中通常更好，因为它保留了推理路径。仅在工作真正分支时才 fork。

使用 Codex 的子代理工作流程将有限的工作从主线程卸载。让主代理专注于核心问题，并将子代理用于探索、测试或分类等任务。

## 要避免的常见错误

初次使用 Codex 时要避免的一些常见错误：

- 用持久的规则压垮提示，而不是将它们移到 AGENTS.md 或 Skill 中
- 不让代理看到它的工作（即不提供如何最好地运行构建和测试命令的细节）
- 在多步骤和复杂任务上跳过规划
- 在了解工作流程之前授予 Codex 对电脑的完全权限
- 在不使用 git worktrees 的情况下在相同文件上运行实时线程
- 在工作流程手动不可靠之前将其变为自动化
- 将 Codex 视为必须逐步查看的东西，而不是将其用于你自己的并行工作
- 每个项目使用一个线程而不是每个任务一个线程。这会导致上下文臃肿，随着时间的推移结果变差
