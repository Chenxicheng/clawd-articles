---
title: "Best practices – Codex | OpenAI Developers"
source: "https://developers.openai.com/codex/learn/best-practices"
saved_at: "2026-03-28"
tags: [Codex, OpenAI, Best Practices, AI Coding Agent]
---

# Best practices – Codex | OpenAI Developers / 最佳实践 – Codex | OpenAI 开发者

---

If you're new to Codex or coding agents in general, this guide will help you get better results faster. It covers the core habits that make Codex more effective across the CLI, IDE extension, and the Codex app, from prompting and planning to validation, MCP, skills, and automations.

如果你刚接触 Codex 或编码 Agent，本指南将帮助你更快获得更好的结果。它涵盖了使 Codex 在 CLI、IDE 扩展和 Codex 应用中更有效的核心习惯，从提示工程、规划到验证、MCP、Skills 和自动化。

---

Codex works best when you treat it less like a one-off assistant and more like a teammate you configure and improve over time.

Codex 最好的使用方式是将它视为一个你可以长期配置和改进的团队成员，而不是一次性助手。

---

A useful way to think about this: start with the right task context, use AGENTS.md for durable guidance, configure Codex to match your workflow, connect external systems with MCP, turn repeated work into skills, and automate stable workflows.

一个有用的思路是：从正确的任务上下文开始，使用 AGENTS.md 进行持久化指导，配置 Codex 以匹配你的工作流程，通过 MCP 连接外部系统，将重复性工作转化为 Skills，并自动化稳定的工作流程。

---

## Strong first use: Context and prompts / 强大的首次使用：上下文和提示

Codex is already strong enough to be useful even when your prompt isn't perfect. You can often hand it a hard problem with minimal setup and still get a strong result.

Codex 已经足够强大，即使提示不完美也能提供帮助。你可以经常给它一个很难的问题，最小化设置，依然获得强劲的结果。

---

If you work in a large or complex repository, the biggest unlock is giving Codex the right task context and a clear structure for what you want done.

如果你工作在大型或复杂的代码库中，最大的突破是给 Codex 正确的任务上下文和清晰的结构。

---

A good default is to include four things in your prompt:

一个好的默认做法是在提示中包含四件事：

- **Goal**: What are you trying to change or build? / 目标：你想要改变或构建什么？
- **Context**: Which files, folders, docs, examples, or errors matter for this task? / 上下文：哪些文件、文件夹、文档、示例或错误对这个任务重要？
- **Constraints**: What standards, architecture, safety requirements, or conventions should Codex follow? / 约束条件：Codex 应该遵循哪些标准、架构、安全要求或约定？
- **Done when**: What should be true before the task is complete? / 完成条件：任务完成前应该是什么样子？

---

Choose a reasoning level based on how hard the task is:

根据任务的难度选择推理级别：

- **Low** for faster, well-scoped tasks / Low：更快、范围更小的任务
- **Medium or High** for more complex changes or debugging / Medium 或 High：更复杂的更改或调试
- **Extra High** for long, agentic, reasoning-heavy tasks / Extra High：漫长的、Agent 性的、推理密集型的任务

---

## AGENTS.md

Think of AGENTS.md as an open-format README for agents. It loads into context automatically and is the best place to encode how you and your team want Codex to work in a repository.

AGENTS.md 是 Agents 的开放式格式 README。它自动加载到上下文中，是编码你和你的团队希望 Codex 在仓库中如何工作的最佳位置。

---

A good AGENTS.md covers:

一个好的 AGENTS.md 涵盖：

- repo layout and important directories / 仓库布局和重要目录
- How to run the project / 如何运行项目
- Build, test, and lint commands / 构建、测试和 lint 命令
- Engineering conventions and PR expectations / 工程约定和 PR 期望
- Constraints and do-not rules / 约束和禁止规则
- What done means and how to verify work / 完成的定义以及如何验证

---

Keep it practical. A short, accurate AGENTS.md is more useful than a long file full of vague rules. Start with the basics, then add new rules only after you notice repeated mistakes.

保持实用。简短准确的 AGENTS.md 比冗长的模糊规则文件更有用。从基础知识开始，然后在注意到重复错误后才添加新规则。

---

## Configuration / 配置

Configuration is one of the main ways to make Codex behave more consistently across sessions and surfaces.

配置是使 Codex 在不同会话和表面上更一致地行为的主要方式之一。

---

Codex ships with operating level sandboxing and has two key knobs: Approval mode and Sandbox mode.

Codex 附带操作系统级别的沙盒，有两个关键旋钮：审批模式和沙盒模式。

---

If you're new to coding agents, start with the default permissions. Keep approval and sandboxing tight by default, then loosen permissions only for trusted repos or specific workflows.

如果你刚接触编码 Agent，请从默认权限开始。默认保持审批和沙盒严格，然后在需要时仅对可信仓库或特定工作流程放宽权限。

---

## Validate your work / 验证你的工作

Don't stop at asking Codex to make a change. Ask it to create tests when needed, run the relevant checks, confirm the result, and review the work before you accept it.

不要仅仅要求 Codex 做出更改就停止。要求它在需要时创建测试，运行相关检查，确认结果，并在接受工作之前审查它。

---

## Use MCPs for external context / 使用 MCP 获取外部上下文

Use MCPs when the context Codex needs lives outside the repo. It lets Codex connect to the tools and systems you already use.

当 Codex 需要的上下文存在于仓库外部时，使用 MCP。它让你将 Codex 连接到你已经使用的工具和系统。

---

Add tools only when they unlock a real workflow. Do not start by wiring in every tool you use.

仅在真正开启真实工作流程时添加工具。不要一开始就将你使用的每个工具连接起来。

---

## Skills

Once a workflow becomes repeatable, stop relying on long prompts or repeated back-and-forth. Use a Skill to package the instructions in a SKILL.md file.

一旦工作流程可重复，就停止依赖冗长的提示或反复来回。将工作流程包装在 SKILL.md 文件中。

---

Keep each skill scoped to one job. Start with 2 to 3 concrete use cases, define clear inputs and outputs.

每个 Skill 保持范围单一。从 2 到 3 个具体的用例开始，定义清晰的输入和输出。

---

## Automations / 自动化

Once a workflow is stable, you can schedule Codex to run it in the background for you. Automations let you choose the project, prompt, cadence, and execution environment.

一旦工作流程稳定，你可以安排 Codex 在后台为你运行它。自动化让你为重复任务选择项目、提示、节奏和执行环境。

---

A useful rule: skills define the method, automations define the schedule.

一个有用的规则是：Skills 定义方法，自动化定义时间表。

---

## Session management / 会话管理

Codex sessions aren't just chat history. They're working threads that accumulate context, decisions, and actions over time.

Codex 会话不仅仅是聊天历史。它们是积累上下文、决策和行动的工乍线程。

---

Keep one thread per coherent unit of work. Fork only when the work truly branches.

每个连贯的工作单元保持一个线程。仅在工作真正分支时才 fork。

---

## Common mistakes to avoid / 要避免的常见错误

- Overloading the prompt with durable rules instead of moving them into AGENTS.md or a skill / 用持久的规则压垮提示，而不是将它们移到 AGENTS.md 或 Skill 中
- Not letting the agent see its work / 不让代理看到它的工作
- Skipping planning on multi-step and complex tasks / 在多步骤和复杂任务上跳过规划
- Giving Codex full permission before understanding the workflow / 在了解工作流程之前授予 Codex 完全权限
- Using one thread per project instead of per task / 每个项目使用一个线程而不是每个任务一个
