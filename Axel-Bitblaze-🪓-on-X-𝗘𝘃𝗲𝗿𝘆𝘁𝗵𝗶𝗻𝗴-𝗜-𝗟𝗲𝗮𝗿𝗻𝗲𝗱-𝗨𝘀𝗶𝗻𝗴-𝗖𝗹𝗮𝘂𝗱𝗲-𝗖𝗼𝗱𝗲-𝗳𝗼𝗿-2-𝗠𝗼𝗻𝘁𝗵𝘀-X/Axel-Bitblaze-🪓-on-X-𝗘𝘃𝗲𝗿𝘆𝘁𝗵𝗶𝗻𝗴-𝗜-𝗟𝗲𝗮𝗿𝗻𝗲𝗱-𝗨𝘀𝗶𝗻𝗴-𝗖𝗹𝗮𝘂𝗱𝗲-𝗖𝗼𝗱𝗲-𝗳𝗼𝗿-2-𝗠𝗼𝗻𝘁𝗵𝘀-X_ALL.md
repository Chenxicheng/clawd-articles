---
title: "𝗘𝘃𝗲𝗿𝘆𝘁𝗵𝗶𝗻𝗴 𝗜 𝗟𝗲𝗮𝗿𝗻𝗲𝗱 𝗨𝘀𝗶𝗻𝗴 𝗖𝗹𝗮𝘂𝗱𝗲 𝗖𝗼𝗱𝗲 𝗳𝗼𝗿 𝟮 𝗠𝗼𝗻𝘁𝗵𝘀 / 我使用 Claude Code 两个月学到的所有东西"
---

# 𝗘𝘃𝗲𝗿𝘆𝘁𝗵𝗶𝗻𝗴 𝗜 𝗟𝗲𝗮𝗿𝗻𝗲𝗱 𝗨𝘀𝗶𝗻𝗴 𝗖𝗹𝗮𝘂𝗱𝗲 𝗖𝗼𝗱𝗲 𝗳𝗼𝗿 𝟮 𝗠𝗼𝗻𝘁𝗵𝘀 / 我使用 Claude Code 两个月学到的所有东西

It's March 2026 and if you're still copy pasting code into chatgpt then we need to talk.

i've been deep in claude code for the last 2 months. not casually. daily. in the trenches. i did the courses, got certified, built projects with it, broke things, fixed them, and built more things. i've spent more time in my terminal talking to claude than talking to actual humans.

this isn't a "top 10 AI tools" fluff piece. this is everything i've learned the features nobody talks about, the workflows that actually work, the mistakes that cost me hours, and the tricks that saved me days.

bookmark this. you're going to need it more than once.

W𝗵𝗮𝘁 𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝗱𝗲 𝗮𝗰𝘁𝘂𝗮𝗹𝗹𝘆 𝗶𝘀

let me kill the biggest misconception first. claude code is not copilot. it's not a chatbot you paste code into. it's not autocomplete on steroids.

it's an 𝗮𝗴𝗲𝗻𝘁. an actual autonomous agent that:

*   reads your entire codebase

*   plans an approach

*   edits files across your whole project

*   runs your tests

*   sees failures and fixes them

*   iterates until the job is done

the key word is 𝗮𝗴𝗲𝗻𝘁𝗶𝗰. it operates in a loop gather context, take action, verify results, repeat. you tell it what you want, it figures out how to get there. you're not writing code together. you're delegating to something that actually understands what it's reading.

it lives in your terminal. that's not a limitation that's the point. your terminal is the most powerful interface on your machine. claude code meets you there.

[![Image 1: Image](./img_2b73c5a5.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037954736113250304)

W𝗵𝗲𝗿𝗲 𝗶𝘁 𝗿𝘂𝗻𝘀:

Claude code isn't just a CLI tool anymore. it's everywhere:

*   𝘁𝗲𝗿𝗺𝗶𝗻𝗮𝗹: the OG. full power. fastest. this is where the magic happens.

*   𝗩𝗦 𝗖𝗼𝗱𝗲 𝗲𝘅𝘁𝗲𝗻𝘀𝗶𝗼𝗻: inline diffs, @-mentions, sidebar conversations. for people who live in their editor.

*   𝗝𝗲𝘁𝗕𝗿𝗮𝗶𝗻𝘀 𝗽𝗹𝘂𝗴𝗶𝗻: same deal, for the IntelliJ crew.

*   𝗱𝗲𝘀𝗸𝘁𝗼𝗽 𝗮𝗽𝗽 (𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝘄𝗼𝗿𝗸): visual diff review, multiple sessions, scheduled tasks. no terminal needed. the "i don't do command lines" option.

*   𝘄𝗲𝗯 𝗮𝗽𝗽 (𝗰𝗹𝗮𝘂𝗱𝗲.𝗮𝗶/𝗰𝗼𝗱𝗲): no local setup needed. run long tasks from anywhere. open a browser and go.

*   𝗺𝗼𝗯𝗶𝗹𝗲 𝘃𝗶𝗮 𝗿𝗲𝗺𝗼𝘁𝗲 𝗰𝗼𝗻𝘁𝗿𝗼𝗹: start a session on your laptop, control it from your phone.

*   𝘀𝗹𝗮𝗰𝗸: mention

in your workspace, turn issues into PRs from chat. 
*   𝗴𝗶𝘁𝗵𝘂𝗯 𝗮𝗰𝘁𝗶𝗼𝗻𝘀:

in a PR comment and it responds with actual code changes. 
*   G𝗶𝘁𝗹𝗮𝗯 𝗖𝗜/𝗖𝗗: same concept for gitlab teams.

the remote control feature is underrated and nobody talks about it. you're at lunch, get a slack message about a bug, pull out your phone, tell claude to fix it. it runs on your machine at home. you review the diff on your phone. approve. done. the future is now lads.

![Image 2](./img_0b28829f.jpg)

现在是 2026 年 3 月，如果你还在把代码复制粘贴到 ChatGPT 里，那我们需要谈谈了。

过去两个月我一直在深度使用 Claude Code。不是随便玩玩——每天都在用，真刀真枪地干。我学了课程、拿了认证、用它做了项目、踩了坑、填了坑、又做了更多东西。我花在跟 Claude 聊天的时间比跟真人聊天的时间还多。

这不是一篇"十大 AI 工具"的水文。这是我学到的一切——没人谈过的功能、真正有效的workflow、浪费我好几个小时的错误、以及帮我省了好几天的技巧。

收藏这篇文章。你会不止一次需要它。

It's March 2026 and if you're still copy pasting code into chatgpt then we need to talk.

i've been deep in claude code for the last 2 months. not casually. daily. in the trenches. i did the courses, got certified, built projects with it, broke things, fixed them, and built more things. i've spent more time in my terminal talking to claude than talking to actual humans.

this isn't a "top 10 AI tools" fluff piece. this is everything i've learned the features nobody talks about, the workflows that actually work, the mistakes that cost me hours, and the tricks that saved me days.

bookmark this. you're going to need it more than once.

W𝗵𝗮𝘁 𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝗱𝗲 𝗮𝗰𝘁𝘂𝗮𝗹𝗹𝘆 𝗶𝘀

let me kill the biggest misconception first. claude code is not copilot. it's not a chatbot you paste code into. it's not autocomplete on steroids.

it's an 𝗮𝗴𝗲𝗻𝘁. an actual autonomous agent that:

*   reads your entire codebase

*   plans an approach

*   edits files across your whole project

*   runs your tests

*   sees failures and fixes them

*   iterates until the job is done

the key word is 𝗮𝗴𝗲𝗻𝘁𝗶𝗰. it operates in a loop gather context, take action, verify results, repeat. you tell it what you want, it figures out how to get there. you're not writing code together. you're delegating to something that actually understands what it's reading.

it lives in your terminal. that's not a limitation that's the point. your terminal is the most powerful interface on your machine. claude code meets you there.

[![Image 1: Image](./img_2b73c5a5.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037954736113250304)

W𝗵𝗲𝗿𝗲 𝗶𝘁 𝗿𝘂𝗻𝘀:

Claude code isn't just a CLI tool anymore. it's everywhere:

*   𝘁𝗲𝗿𝗺𝗶𝗻𝗮𝗹: the OG. full power. fastest. this is where the magic happens.

*   𝗩𝗦 𝗖𝗼𝗱𝗲 𝗲𝘅𝘁𝗲𝗻𝘀𝗶𝗼𝗻: inline diffs, @-mentions, sidebar conversations. for people who live in their editor.

*   𝗝𝗲𝘁𝗕𝗿𝗮𝗶𝗻𝘀 𝗽𝗹𝘂𝗴𝗶𝗻: same deal, for the IntelliJ crew.

*   𝗱𝗲𝘀𝗸𝘁𝗼𝗽 𝗮𝗽𝗽 (𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝘄𝗼𝗿𝗸): visual diff review, multiple sessions, scheduled tasks. no terminal needed. the "i don't do command lines" option.

*   𝘄𝗲𝗯 𝗮𝗽𝗽 (𝗰𝗹𝗮𝘂𝗱𝗲.𝗮𝗶/𝗰𝗼𝗱𝗲): no local setup needed. run long tasks from anywhere. open a browser and go.

*   𝗺𝗼𝗯𝗶𝗹𝗲 𝘃𝗶𝗮 𝗿𝗲𝗺𝗼𝘁𝗲 𝗰𝗼𝗻𝘁𝗿𝗼𝗹: start a session on your laptop, control it from your phone.

*   𝘀𝗹𝗮𝗰𝗸: mention

in your workspace, turn issues into PRs from chat. 
*   𝗴𝗶𝘁𝗵𝘂𝗯 𝗮𝗰𝘁𝗶𝗼𝗻𝘀:

in a PR comment and it responds with actual code changes. 
*   G𝗶𝘁𝗹𝗮𝗯 𝗖𝗜/𝗖𝗗: same concept for gitlab teams.

the remote control feature is underrated and nobody talks about it. you're at lunch, get a slack message about a bug, pull out your phone, tell claude to fix it. it runs on your machine at home. you review the diff on your phone. approve. done. the future is now lads.

![Image 2](./img_0b28829f.jpg)

**𝗖𝗹𝗮𝘂𝗱𝗲 𝗖𝗼𝗱𝗲 到底是啥**

先让我纠正最大的误解。Claude Code 不是 Copilot。它不是你粘贴代码进去的聊天机器人。也不是加强版自动补全。

它是一个**智能体**。一个真正自主的智能体，能：

*   阅读你的整个代码库
*   制定方案
*   编辑整个项目中的文件
*   运行测试
*   发现失败并修复
*   迭代直到任务完成

关键词是**自主性**。它以循环方式运作——收集上下文、执行操作、验证结果、重复。你告诉它你想要什么，它来想办法实现。不是你在跟它一起写代码，而是你把事情委托给一个真正理解自己在读什么的东西。

它运行在你的终端里。这不是限制——这才是重点。你的终端是你机器上最强大的界面。Claude Code 在那里跟你会合。

[![Image 1: Image](./img_2b73c5a5.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037954736113250304)

𝗶𝗻𝘀𝘁𝗮𝗹𝗹:

```
macOS/Linux: curl -fsSL https://claude.ai/install.sh | bash`
Windows: irm https://claude.ai/install.ps1 | iex`
Homebrew: brew install --cask claude-code`
```

**𝗖𝗹𝗮𝘂𝗱𝗲 𝗖𝗼𝗱𝗲 的运行场所：**

Claude Code 不再只是 CLI 工具了。它无处不在：

*   **终端**：原汁原味。全力输出。最快。这是魔法发生的地方。
*   **VS Code 扩展**：内联 diff、@提及、侧边栏对话。给那些住在编辑器里的人准备的。
*   **JetBrains 插件**：同样的东西，给 IntelliJ 用户。
*   **桌面应用（Claude Cowork）**：可视化 diff 审查、多会话、定时任务。不需要终端。"我不用命令行"选项。
*   **网页应用（claude.ai/code）**：无需本地配置。随时随地运行长任务。打开浏览器就能用。
*   **通过远程控制实现手机操作**：在笔记本上开始会话，从手机控制。
*   **Slack**：在你的 workspace 里提及，将 issue 转成 PR。
*   **GitHub Actions**：在 PR 评论里触发，它会回复实际的代码变更。
*   **GitLab CI/CD**：对 GitLab 团队同样的概念。

远程控制功能被严重低估了，没人谈它。你在吃午饭，收到 Slack 上关于 bug 的消息，掏出手机，让 Claude 去修。代码运行在家里的机器上。你在手机上审查 diff。批准。搞定。未来已经来了，兄弟们。

![Image 2](./img_0b28829f.jpg)

𝘁𝗵𝗲𝗻:

```
cd your-project
claude
log in with your anthropic account
start talking to it
```

that's it. no config files. no setup wizard. no 47 extensions to install. no yaml hell. just cd into your project and type claude.

**𝗖𝗹𝗮𝘂𝗱𝗲 𝗖𝗼𝗱𝗲 入门**

**安装：**

```
macOS/Linux: curl -fsSL https://claude.ai/install.sh | bash`
Windows: irm https://claude.ai/install.ps1 | iex`
Homebrew: brew install --cask claude-code`
```

𝗳𝗶𝗿𝘀𝘁 𝘁𝗵𝗶𝗻𝗴 𝘆𝗼𝘂 𝘀𝗵𝗼𝘂𝗹𝗱 𝗱𝗼:

`claude "what does this project do?"`

watch it explore your codebase, read your files, understand your architecture, and give you a summary. that moment when it correctly summarizes a 20,000+ line repo for the first time that's when it clicks. that's the moment you realize this isn't autocomplete.

T𝗵𝗲 𝗺𝗼𝗱𝗲𝗹𝘀

claude code runs on anthropic's claude model family. knowing which to use and when is half the game:

*   𝗰𝗹𝗮𝘂𝗱𝗲 𝗼𝗽𝘂𝘀 𝟰.𝟲: the big brain. best reasoning. use for complex architecture decisions, tricky debugging, large refactors that touch 10+ files. when you need it to actually think.

*   𝗰𝗹𝗮𝘂𝗱𝗲 𝘀𝗼𝗻𝗻𝗲𝘁 𝟰.𝟲: the workhorse. default model. best balance of speed, cost, and quality for everyday coding. this is your daily driver.

*   𝗰𝗹𝗮𝘂𝗱𝗲 𝗵𝗮𝗶𝗸𝘂: the speedster. cheap and fast. great for simple tasks and subagents. don't sleep on this for quick questions.

**然后：**

```
cd your-project
claude
log in with your anthropic account
start talking to it
```

就这样。没有配置文件。没有安装向导。没有 47 个扩展要装。没有 YAML 地狱。只需要 cd 到你的项目然后输入 claude。

𝘀𝘄𝗶𝘁𝗰𝗵 𝗺𝗼𝗱𝗲𝗹𝘀 𝗮𝗻𝘆𝘁𝗶𝗺𝗲:

```
`/model opus` — mid-session switch when you hit a hard problem
`claude --model opus` — start the whole session with opus
```

here's what i learned the hard way: 𝗺𝗮𝘁𝗰𝗵 𝗲𝗳𝗳𝗼𝗿𝘁 𝘁𝗼 𝘁𝗵𝗲 𝗽𝗿𝗼𝗯𝗹𝗲𝗺. don't burn opus tokens on renaming a variable. don't use haiku for redesigning your auth system. i wasted probably $200 in my first week using opus for everything because it "felt smarter." sonnet handles 90% of tasks identically.

**你首先应该做的事：**

`claude "what does this project do?"`

看它探索你的代码库、阅读文件、理解架构，然后给你一个总结。第一次它正确总结了一个 20000+ 行仓库的那一刻——就是这种感觉。就是这一刻你意识到这不是自动补全。

𝘆𝗼𝘂 𝗰𝗮𝗻 𝗮𝗹𝘀𝗼 𝗰𝗼𝗻𝘁𝗿𝗼𝗹 𝘁𝗵𝗶𝗻𝗸𝗶𝗻𝗴 𝗱𝗲𝗽𝘁𝗵 𝗶𝗻𝗱𝗲𝗽𝗲𝗻𝗱𝗲𝗻𝘁𝗹𝘆 𝗼𝗳 𝘁𝗵𝗲 𝗺𝗼𝗱𝗲𝗹:

```
`/effort low` — quick answers, minimal reasoning. great for "what's the syntax for X?"
`/effort high` — deep analysis, extended thinking. use for debugging.
`/effort max` — full power. burns more tokens but catches edge cases humans miss. use this for anything that'll go to production.
```

**𝗧𝗵𝗲 𝗺𝗼𝗱𝗲𝗹𝘀（模型）**

Claude Code 运行在 Anthropic 的 Claude 模型系列上。知道用哪个、什么时候用，这门功课已经学会了一半：

*   **Claude Opus 4.6**：大脑最发达的。推理最强。用于复杂的架构决策、棘手的调试、涉及 10+ 文件的大型重构。当你需要它真正思考的时候用它。
*   **Claude Sonnet 4.6**：主力模型。默认之选。日常编码中速度、成本和质量最佳平衡。这是你的日常座驾。
*   **Claude Haiku**：速度之星。便宜又快。适合简单任务和子智能体。别小看它用于快速提问。

𝗽𝗿𝗶𝗰𝗶𝗻𝗴 (𝘁𝗵𝗲 𝗿𝗲𝗮𝗹 𝘁𝗮𝗹𝗸)

**随时切换模型：**

```
`/model opus` — 遇到难题时在会话中途切换到 opus
`claude --model opus` — 用 opus 开始整个会话
```

我学到这个教训付出了血的代价：让任务难度匹配模型。不要用 opus 重命名一个变量。不要用 haiku 重新设计你的认证系统。第一周我把所有东西都用 opus 因为它"感觉更聪明"，大概浪费了 200 美元。Sonnet 能以同样的质量处理 90% 的任务。

𝗹𝗲𝘁'𝘀 𝗯𝗲 𝗵𝗼𝗻𝗲𝘀𝘁 𝗮𝗯𝗼𝘂𝘁 𝗺𝗼𝗻𝗲𝘆 𝗯𝗲𝗰𝗮𝘂𝘀𝗲 𝗻𝗼𝗯𝗼𝗱𝘆 𝗲𝗹𝘀𝗲 𝗶𝘀:

```
| plan | cost | what you get |
|------|------|-------------|
| 𝗽𝗿𝗼 | $20/mo | claude code access, sonnet + opus, good for getting started |
| 𝗺𝗮𝘅 𝟱𝘅 | $100/mo | 5x usage limits, 1M context window, priority access |
| 𝗺𝗮𝘅 𝟮𝟬𝘅 | $200/mo | 20x limits, rate limits basically gone for full-day dev |
| 𝘁𝗲𝗮𝗺 | $100/seat/mo (premium) | centralized billing, shared settings, analytics |
| 𝗔𝗣𝗜 | pay per token | sonnet: $3/$15 per MTok in/out. opus: $15/$75 |
```

Real world numbers from anthropic themselves: average developer spends about $𝟲/𝗱𝗮𝘆. 90% of users are under $12/day.

here's the wild stat that sold me: one developer tracked 10 billion tokens over 8 months. on API pricing that would've been ~$15,000. on the max plan? $800. if you're using it daily (and you should be), max pays for itself by week 2.

when you hit your limits on max, you can enable "extra usage" billed at API rates. no hard cutoff. no "sorry, come back tomorrow."

**你还可以独立控制思考深度：**

```
`/effort low` — 快速回答，最少推理。适合"X 的语法是什么？"
`/effort high` — 深度分析，扩展思考。用于调试。
`/effort max` — 全力输出。消耗更多 token，但能捕捉人类漏掉的边缘情况。用于任何要上生产环境的东西。
```

𝗰𝗼𝘀𝘁 𝗺𝗮𝗻𝗮𝗴𝗲𝗺𝗲𝗻𝘁 𝘁𝗶𝗽𝘀 𝗶 𝘄𝗶𝘀𝗵 𝗶 𝗸𝗻𝗲𝘄 𝗱𝗮𝘆 𝟭:

```
use sonnet for 90% of tasks, opus for the hard stuff
use subagents to isolate expensive operations (more on this later)
`/compact` to summarize and save context tokens when conversations get long
`/clear` between unrelated tasks — don't carry CSS bug context into an API redesign
keep your CLAUDE.md lean — bloated instructions waste tokens on every single message
```

**𝗣𝗿𝗶𝗰𝗶𝗻𝗴（定价，真话）**

**关于钱的问题咱们坦诚相待，因为没人会跟你说这些：**

```
| plan | cost | what you get |
|------|------|-------------|
| 𝗽𝗿𝗼 | $20/mo | claude code access, sonnet + opus, 适合入门 |
| 𝗺𝗮𝘅 𝟱𝘅 | $100/mo | 5x 使用限额，1M 上下文窗口，优先访问 |
| 𝗺𝗮𝘅 𝟮𝟬𝘅 | $200/mo | 20x 限额，速率限制对全天候开发基本消失 |
| 𝘁𝗲𝗮𝗺 | $100/seat/mo (高级) | 集中账单、共享设置、分析 |
| 𝗔𝗣𝗜 | 按 token 付费 | sonnet: $3/$15 per MTok in/out. opus: $15/$75 |
```

Anthropic 自己的真实数据：普通开发者每天大约花 **$6**。90% 的用户每天低于 $12。

这个数据让我下定决心：一位开发者追踪了 8 个月共 100 亿 token。按 API 定价大约是 15000 美元。按 Max 计划？只要 800 美元。如果你每天都在用（你应该每天用），Max 计划到第二周就回本了。

当你在 Max 计划下达到限额时，可以开启"额外用量"按 API 费率计费。没有硬性上限。没有"抱歉，明天再来吧"。

𝘁𝗵𝗲 .𝗰𝗹𝗮𝘂𝗱𝗲 𝗳𝗼𝗹𝗱𝗲𝗿 𝘆𝗼𝘂𝗿 𝗽𝗿𝗼𝗷𝗲𝗰𝘁'𝘀 𝗰𝗼𝗻𝘁𝗿𝗼𝗹 𝗰𝗲𝗻𝘁𝗲𝗿

this is where most people leave 80% of the value on the table. the .claude folder is not a black box. it's the control center for how claude behaves in your project.

and here's what most people don't realize: 𝘁𝗵𝗲𝗿𝗲 𝗮𝗿𝗲 𝘁𝘄𝗼 .𝗰𝗹𝗮𝘂𝗱𝗲 𝗱𝗶𝗿𝗲𝗰𝘁𝗼𝗿𝗶𝗲𝘀, 𝗻𝗼𝘁 𝗼𝗻𝗲.

the first lives inside your project (committed to git, shared with your team). the second lives at ~/.claude/ (personal preferences, machine-local state, session history).

[![Image 3: Image](./img_081bc96d.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037959141877334017)

**我希望在第一天就知道的费用管理技巧：**

```
用 sonnet 处理 90% 的任务，opus 只用于难题
用子智能体隔离昂贵操作（后面详述）
`/compact` 当对话变长时手动总结节省上下文 token
`/clear` 在不相关的任务之间清理——不要把 CSS bug 的上下文带到 API 重设计上
保持 CLAUDE.md 精简——臃肿的指令每条消息都会浪费 token
```

𝗖𝗟𝗔𝗨𝗗𝗘.𝗺𝗱: 𝘁𝗵𝗲 𝘀𝗶𝗻𝗴𝗹𝗲 𝗺𝗼𝘀𝘁 𝗶𝗺𝗽𝗼𝗿𝘁𝗮𝗻𝘁 𝗳𝗶𝗹𝗲

when you start a claude code session, the first thing it reads is CLAUDE.md. it loads it straight into the system prompt. everything in there, claude follows. every session. consistently.

if you tell claude to always write tests before implementation, it will. if you say "never use console.log, use the custom logger," it will respect that every time.

**𝗧𝗵𝗲 .𝗰𝗹𝗮𝘂𝗱𝗲 𝗳𝗼𝗹𝗱𝗲𝗿——你的项目控制中心**

这是大多数人对 Claude Code 的使用还停留在 80% 价值以下的原因。.claude 文件夹不是黑箱。它是控制 Claude 在你的项目中行为方式的控制中心。

而且大多数人没意识到的是：**有两个 .claude 目录，不是一个。**

第一个在你的项目内部（提交到 git，与团队共享）。第二个在 ~/.claude/（个人偏好、机器本地状态、会话历史）。

[![Image 3: Image](./img_081bc96d.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037959141877334017)

𝘄𝗵𝗮𝘁 𝘁𝗼 𝘄𝗿𝗶𝘁𝗲:

*   build, test, and lint commands (npm run test, make build)

*   key architectural decisions ("we use a monorepo with turborepo")

*   non-obvious gotchas ("typescript strict mode is on, unused variables are errors")

*   import conventions, naming patterns, error handling styles

*   file and folder structure for the main modules

**𝗖𝗟𝗔𝗨𝗗𝗘.𝗺𝗱：最重要的文件**

当你启动 Claude Code 会话时，它第一个读取的就是 CLAUDE.md。它直接加载到系统提示里。这里面的每一条指令，Claude 都会遵守。每一次会话。始终如一。

如果你告诉 Claude 始终在实现之前写测试，它就会这样做。如果你说"不要用 console.log，用自定义 logger"，它每次都会遵守。

𝘄𝗵𝗮𝘁 𝗡𝗢𝗧 𝘁𝗼 𝘄𝗿𝗶𝘁𝗲:

*   anything that belongs in a linter or formatter config (prettier handles that, not CLAUDE.md)

*   full documentation you can already link to

*   long paragraphs explaining theory

**该怎么写：**

*   构建、测试和 lint 命令（npm run test, make build）
*   关键架构决策（"我们用 turborepo 做 monorepo"）
*   不明显的坑（"TypeScript strict 模式已开启，未使用变量是错误"）
*   import 规范、命名模式、错误处理风格
*   主要模块的文件和文件夹结构

𝗸𝗲𝗲𝗽 𝗶𝘁 𝘂𝗻𝗱𝗲𝗿 𝟮𝟬𝟬 𝗹𝗶𝗻𝗲𝘀. files longer than that start eating too much context, and claude's instruction adherence actually drops. i learned this the hard way when my 400-line CLAUDE.md was getting half-ignored. cut it to 150 lines, everything got better.

**不要写什么：**

*   属于 linter 或格式化器配置的东西（Prettier 干这个的，不是 CLAUDE.md）
*   你可以链接到的完整文档
*   解释理论的长段落

𝗵𝗲𝗿𝗲'𝘀 𝘄𝗵𝗮𝘁 𝗮 𝘀𝗼𝗹𝗶𝗱 𝗖𝗟𝗔𝗨𝗗𝗘.𝗺𝗱 𝗹𝗼𝗼𝗸𝘀 𝗹𝗶𝗸𝗲:

```
Project: Acme API

Commands
npm run dev          # Start dev server
npm run test         # Run tests (Jest)
npm run lint         # ESLint + Prettier check
npm run build        # Production build

Architecture
- Express REST API, Node 20
- PostgreSQL via Prisma ORM
- All handlers live in src/handlers/
- Shared types in src/types/

Conventions
- Use zod for request body validation
- Return shape is always { data, error }
- Never expose stack traces to the client
- Use the logger module, not console.log

Watch out for
- Tests use a real local DB, not mocks. Run `npm run db:test:reset` first
- Strict TypeScript: no unused imports, ever
```

that's 20 lines. it gives claude everything it needs to work productively in this codebase without constant clarification.

**保持在 200 行以内。** 超过这个长度的文件开始占用太多上下文，而且 Claude 的指令遵循度实际上会下降。我吃这个亏是因为我 400 行的 CLAUDE.md 被忽略了一半。精简到 150 行，一切变好了。

𝗖𝗟𝗔𝗨𝗗𝗘.𝗹𝗼𝗰𝗮𝗹.𝗺𝗱: 𝘆𝗼𝘂𝗿 𝗽𝗲𝗿𝘀𝗼𝗻𝗮𝗹 𝗼𝘃𝗲𝗿𝗿𝗶𝗱𝗲𝘀

sometimes you have preferences that are just yours, not the team's. maybe you prefer a different test runner. maybe you want claude to always open files in a specific pattern.

create CLAUDE.local.md in your project root. claude reads it alongside the main CLAUDE.md, and it's automatically gitignored so your personal tweaks never land in the repo.

**一个扎实的 CLAUDE.md 长这样：**

```
Project: Acme API

Commands
npm run dev          # Start dev server
npm run test         # Run tests (Jest)
npm run lint         # ESLint + Prettier check
npm run build        # Production build

Architecture
- Express REST API, Node 20
- PostgreSQL via Prisma ORM
- All handlers live in src/handlers/
- Shared types in src/types/

Conventions
- Use zod for request body validation
- Return shape is always { data, error }
- Never expose stack traces to the client
- Use the logger module, not console.log

Watch out for
- Tests use a real local DB, not mocks. Run `npm run db:test:reset` first
- Strict TypeScript: no unused imports, ever
```

这才 20 行。它给了 Claude 在这个代码库中高效工作所需的一切，不需要反复确认。

𝘁𝗵𝗲 𝗿𝘂𝗹𝗲𝘀/ 𝗳𝗼𝗹𝗱𝗲𝗿 𝗺𝗼𝗱𝘂𝗹𝗮𝗿 𝗶𝗻𝘀𝘁𝗿𝘂𝗰𝘁𝗶𝗼𝗻𝘀 𝘁𝗵𝗮𝘁 𝘀𝗰𝗮𝗹𝗲

CLAUDE.md works great for a single project. but once your team grows, you end up with a 300-line CLAUDE.md that nobody maintains and everyone ignores.

the rules/ folder solves that.

every markdown file inside .claude/rules/ gets loaded alongside your CLAUDE.md automatically:

```
.claude/rules/
├── code-style.md
├── testing.md
├── api-conventions.md
└── security.md
```

each file stays focused. the person who owns API conventions edits api-conventions.md. the person who owns testing standards edits testing.md. nobody stomps on each other.

the real power comes from 𝗽𝗮𝘁𝗵-𝘀𝗰𝗼𝗽𝗲𝗱 𝗿𝘂𝗹𝗲𝘀. add YAML frontmatter and the rule only activates when claude is working with matching files:

```
---
paths:
  - "src/api/**/*.ts"
  - "src/handlers/**/*.ts"
---
```

**𝗖𝗟𝗔𝗨𝗗𝗘.𝗹𝗼𝗰𝗮𝗹.𝗺𝗱：你的个人覆盖设置**

有时候你有自己的偏好，不是团队的。也许你更喜欢另一个测试运行器。也许你希望 Claude 始终以特定模式打开文件。

在项目根目录创建 CLAUDE.local.md。Claude 会和主 CLAUDE.md 一起读取它，而且它自动被 gitignore，所以你个人的小调整永远不会进入仓库。

𝗔𝗣𝗜 𝗗𝗲𝘀𝗶𝗴𝗻 𝗥𝘂𝗹𝗲𝘀

*   All handlers return { data, error } shape

*   Use zod for request body validation

*   Never expose internal error details to clients

claude won't even load this when it's editing a React component. it only kicks in when working inside src/api/ or src/handlers/. clean, focused, efficient.

[![Image 4: Image](./img_1b7bd789.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037959703632986112)

**𝗥𝘂𝗹𝗲𝘀/ 文件夹——可扩展的模块化指令**

CLAUDE.md 对单个项目很有效。但一旦团队壮大，你就会得到一个 300 行的 CLAUDE.md，没人维护，每个人都无视它。

rules/ 文件夹解决了这个问题。

.claude/rules/ 里的每个 markdown 文件都会自动和你的 CLAUDE.md 一起加载：

```
.claude/rules/
├── code-style.md
├── testing.md
├── api-conventions.md
└── security.md
```

每个文件保持专注。负责 API 规范的人编辑 api-conventions.md。负责测试标准的人编辑 testing.md。谁也不会踩到谁。

真正的力量来自**路径范围的规则**。添加 YAML frontmatter，规则只会在 Claude 处理匹配文件时激活：

```
---
paths:
  - "src/api/**/*.ts"
  - "src/handlers/**/*.ts"
---
```

𝗔𝗣𝗜 𝗗𝗲𝘀𝗶𝗴𝗻 𝗥𝘂𝗹𝗲𝘀

*   All handlers return { data, error } shape

*   Use zod for request body validation

*   Never expose internal error details to clients

Claude 在编辑 React 组件时根本不会加载这个。只有在 src/api/ 或 src/handlers/ 下工作时才会触发。干净、专注、高效。

[![Image 4: Image](./img_1b7bd789.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037959703632986112)

𝘁𝗵𝗲 𝗳𝗲𝗮𝘁𝘂𝗿𝗲𝘀 𝘁𝗵𝗮𝘁 𝗰𝗵𝗮𝗻𝗴𝗲𝗱 𝗵𝗼𝘄 𝗶 𝘄𝗼𝗿𝗸

**𝗧𝗵𝗲 𝗳𝗲𝗮𝘁𝘂𝗿𝗲𝘀 𝘁𝗵𝗮𝘁 𝗰𝗵𝗮𝗻𝗴𝗲𝗱 𝗵𝗼𝘄 𝗜 𝘄𝗼𝗿𝗸（改变我工作方式的功能）**

**多文件编辑**

这就是 Claude Code 把其他所有工具远远甩在身后的地方。这是让我停止用其他工具做正经工作的功能。

`claude "refactor the authentication system to use JWT tokens instead of sessions"`

它会：

*   找到所有涉及 auth 的文件
*   更新中间件
*   修改路由
*   改动测试
*   更新配置
*   修复 import

一次会话跨 15+ 个文件。应用之前向你展示 diff 供审查。你批准、拒绝或对每个文件提出修改意见。

我曾经在一个会话里把整个 Express 应用从回调重构为 async/await。23 个文件。每一个都正确。用 tab 补全做做看？

𝗺𝘂𝗹𝘁𝗶-𝗳𝗶𝗹𝗲 𝗲𝗱𝗶𝘁𝗶𝗻𝗴

this is where claude code leaves everything else in the dust. this is the feature that made me stop using anything else for serious work.

`claude "refactor the authentication system to use JWT tokens instead of sessions"`

it will:

*   find every file touching auth

*   update the middleware

*   modify the routes

*   change the tests

*   update the config

*   fix the imports

across 15+ files in one session. shows you diffs for review before applying. you approve, reject, or ask for changes on each file.

i refactored an entire express app from callbacks to async/await in one session. 23 files. every one correct. try doing that with tab completion.

**𝗚𝗶𝘁 集成**

Claude Code 原生支持 git，而且它的 commit 信息写得比我共事过的大多数人都好：

```
claude "commit my changes with a descriptive message"
claude "create a PR for this feature"
claude "help me resolve these merge conflicts"
claude "show me what changed in the last 5 commits and explain the impact"
```

它写的是proper commit 信息——不是"fixed stuff"，而是关于什么变了、为什么变的真实描述。它创建带摘要和测试计划的 PR。它通过真正理解两边代码来处理合并冲突，而不是选一边然后碰运气。

𝗴𝗶𝘁 𝗶𝗻𝘁𝗲𝗴𝗿𝗮𝘁𝗶𝗼𝗻

claude code speaks git natively and it's better at commit messages than most humans i've worked with:

```
claude "commit my changes with a descriptive message"
claude "create a PR for this feature"
claude "help me resolve these merge conflicts"
claude "show me what changed in the last 5 commits and explain the impact"
```

it writes proper commit messages not "fixed stuff" but actual descriptions of what changed and why. it creates PRs with summaries and test plans. it handles merge conflicts by actually understanding the code on both sides, not just picking a side and hoping.

**𝗧𝗵𝗲 𝗮𝗴𝗲𝗻𝘁𝗶𝗰 𝗹𝗼𝗼𝗽（自主循环）：写→测→修→重复**

Claude 不只是写代码——它运行代码：

`写一个函数 → 运行测试 → 发现失败 → 读取错误 → 修复 bug → 再次运行测试 → 全部绿灯`

这个循环才是关键。它不是"给你一些代码，祝你好运"。而是"我写了，测了，修了你想不到的边缘情况，然后通过了。"我曾经看着它在自己写的代码里捉到 bug，那个 bug 我自己要好几个小时才能发现。

𝘁𝗵𝗲 𝗮𝗴𝗲𝗻𝘁𝗶𝗰 𝗹𝗼𝗼𝗽 𝘄𝗿𝗶𝘁𝗲, 𝘁𝗲𝘀𝘁, 𝗳𝗶𝘅, 𝗿𝗲𝗽𝗲𝗮𝘁

claude doesn't just write code it runs it:

`writes a function → runs the tests → sees a failure → reads the error → fixes the bug → runs tests again → all green`

this loop is the whole point. it's not "here's some code, good luck." it's "i wrote it, tested it, fixed the edge case you didn't think of, and it passes." i've watched it catch bugs in its own code that i wouldn't have spotted for hours.

**𝗦𝘂𝗯𝗮𝗴𝗲𝗻𝘁𝘀——没人谈的游戏规则改变者**

这个功能我花了 3 周才开始正确使用，我后悔每一天没有早点用。

Claude 可以生成专门的子智能体来处理特定任务，与主会话隔离：

*   **𝗲𝘅𝗽𝗹𝗼𝗿𝗲 𝗮𝗴𝗲𝗻𝘁**：只读研究，快速，用 haiku。完美适合"去理解这个模块是怎么工作的"。
*   **𝗽𝗹𝗮𝗻 𝗮𝗴𝗲𝗻𝘁**：实现之前分析。"动手之前先思考"的强制执行者。
*   **𝗴𝗲𝗻𝗲𝗿𝗮𝗹 𝗮𝗴𝗲𝗻𝘁**：复杂多步任务，干净上下文。

为什么这很重要：当你让 Claude 运行完整测试套件时，输出数百行的是/否结果……会淹没你的上下文窗口。你的主对话被噪音污染了。子智能体在隔离环境中处理。它做那些脏活，压缩发现结果，然后返回干净的摘要。

[![Image 5: Image](./img_1ab05499.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037960517990637568)

你也可以为你的特定工作流创建自定义智能体：

```
.claude/agents/security-reviewer.md
---
name: security-reviewer
description: Expert code reviewer for security vulnerabilities. Use PROACTIVELY when reviewing PRs or before deployments.
model: sonnet
tools: Read, Grep, Glob
---

You are a senior security engineer. When reviewing code:
- Flag bugs, not just style issues
- Check for SQL injection and XSS risks
- Look for exposed credentials or secrets
- Check authentication and authorization gaps
- Note performance concerns only when they matter at scale
```

现在 Claude 会在相关时自动将安全审查委托给你的自定义智能体。或者你可以显式调用：输入 /security-reviewer 它就会启动。

tools 字段是有意的——安全审计者只需要 Read、Grep 和 Glob。它没有任何理由写文件。model 字段让你用 haiku 处理廉价的只读任务，把 opus 省给真正需要深度推理的场景。

个人智能体放在 ~/.claude/agents/，可以在所有项目中用。

![Image 6](./img_1c55a550.jpg)

𝘀𝘂𝗯𝗮𝗴𝗲𝗻𝘁𝘀 𝘁𝗵𝗲 𝗴𝗮𝗺𝗲 𝗰𝗵𝗮𝗻𝗴𝗲𝗿 𝗻𝗼𝗯𝗼𝗱𝘆 𝘁𝗮𝗹𝗸𝘀 𝗮𝗯𝗼𝘂𝘁

this one took me 3 weeks to start using properly and i regret every day i wasted not using them.

claude can spawn specialized sub-agents to handle specific tasks in isolation:

*   𝗲𝘅𝗽𝗹𝗼𝗿𝗲 𝗮𝗴𝗲𝗻𝘁 read-only research, fast, uses haiku. perfect for "go understand how this module works."

*   𝗽𝗹𝗮𝗻 𝗮𝗴𝗲𝗻𝘁 analyzes before implementing. the "think before you code" enforcer.

*   𝗴𝗲𝗻𝗲𝗿𝗮𝗹 𝗮𝗴𝗲𝗻𝘁 complex multi-step tasks in a clean context.

why this matters: when you ask claude to run your full test suite, that output hundreds of lines of pass/fail.. floods your context window. your main conversation gets polluted with noise. subagents handle it in isolation. they do the messy work, compress the findings, and send back a clean summary.

[![Image 5: Image](./img_1ab05499.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037960517990637568)

you can also create custom agents for your specific workflows:

```
.claude/agents/security-reviewer.md
---
name: security-reviewer
description: Expert code reviewer for security vulnerabilities. Use PROACTIVELY when reviewing PRs or before deployments.
model: sonnet
tools: Read, Grep, Glob
---

You are a senior security engineer. When reviewing code:
- Flag bugs, not just style issues
- Check for SQL injection and XSS risks
- Look for exposed credentials or secrets
- Check authentication and authorization gaps
- Note performance concerns only when they matter at scale
```

now claude automatically delegates security reviews to your custom agent when relevant. or you can call it explicitly: type /security-reviewer and it spins up.

the tools field is intentional.. a security auditor only needs Read, Grep, and Glob. it has no business writing files. the model field lets you use haiku for cheap read-only tasks and save opus for the ones that actually need deep reasoning.

personal agents go in ~/.claude/agents/ and are available across all your projects.

![Image 6](./img_1c55a550.jpg)

**𝗠𝗖𝗣（𝗠𝗼𝗱𝗲𝗹 𝗖𝗼𝗻𝘁𝗲𝘅𝘁 𝗣𝗿𝗼𝘁𝗼𝗰𝗼𝗹）——秘密武器**

这就是 Claude Code 从"不错的编码助手"升级为"我整个工作流的编排层"的地方。

𝗠𝗖𝗣 让𝗖𝗹𝗮𝘂𝗱𝗲 能连接外部工具和服务：

*   **𝗚𝗶𝘁𝗛𝘂𝗯**：搜索仓库、阅读 issue、管理 PR、审查代码
*   **𝗦𝗹𝗮𝗰𝗸**：读取频道、发布消息、回复线程
*   **𝗣𝗼𝘀𝘁𝗴𝗿𝗲𝘀/𝗠𝘆𝗦𝗤𝗟**：直接查询数据库
*   **𝗝𝗶𝗿𝗮**：更新工单、修改状态
*   **𝗙𝗶𝗴𝗺𝗮**：读取设计稿（真的，没开玩笑）
*   **𝗣𝘂𝗽𝗽𝗲𝘁𝗲𝗲𝗿/𝗣𝗹𝗮𝘆𝘄𝗿𝗶𝗴𝗵𝘁**：浏览器自动化
*   **𝗦𝗲𝗻𝘁𝗿𝘆**：错误监控
*   **𝗡𝗼𝘁𝗶𝗼𝗻**：读写文档

在项目根目录的 .mcp.json 里配置：

```
{
  "mcpServers": {
    "github": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your_token"
      }
    }
  }
}
```

𝗠𝗖𝗣 𝗺𝗼𝗱𝗲𝗹 𝗰𝗼𝗻𝘁𝗲𝘅𝘁 𝗽𝗿𝗼𝘁𝗼𝗰𝗼𝗹 (𝘁𝗵𝗲 𝘀𝗲𝗰𝗿𝗲𝘁 𝘄𝗲𝗮𝗽𝗼𝗻)

this is where claude code goes from "good coding assistant" to "orchestration layer for my entire workflow."

**𝗡𝗼𝘄 𝘆𝗼𝘂 𝗰𝗮𝗻 𝗱𝗼 𝘁𝗵𝗶𝗻𝗴𝘀 𝗹𝗶𝗸𝗲（现在你可以做这样的事情）：**

```
claude "find all open bugs in our github repo tagged 'critical' and summarize them"
claude "query the database for users who signed up this week and post the count to #metrics on slack"
claude "check sentry for the top 5 errors this week and create github issues for each one"
```

一个工具，连接到一切。我让 Claude 在一次对话里拉 GitHub issue、读取我的数据库、发摘要到 Slack。不切换标签页。不切换上下文。不在工具之间复制粘贴。

[![Image 7: Image](./img_2d504f97.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037960839433748480)

𝗠𝗖𝗣 𝗹𝗲𝘁𝘀 𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝗻𝗻𝗲𝗰𝘁 𝘁𝗼 𝗲𝘅𝘁𝗲𝗿𝗻𝗮𝗹 𝘁𝗼𝗼𝗹𝘀 𝗮𝗻𝗱 𝘀𝗲𝗿𝘃𝗶𝗰𝗲𝘀:

*   𝗴𝗶𝘁𝗵𝘂𝗯: search repos, read issues, manage PRs, review code

*   𝘀𝗹𝗮𝗰𝗸: read channels, post messages, respond to threads

*   𝗽𝗼𝘀𝘁𝗴𝗿𝗲𝘀/𝗺𝘆𝘀𝗾𝗹: query your database directly

*   𝗷𝗶𝗿𝗮: update tickets, change statuses

*   𝗳𝗶𝗴𝗺𝗮: read designs (yes, really)

*   𝗽𝘂𝗽𝗽𝗲𝘁𝗲𝗲𝗿/𝗽𝗹𝗮𝘆𝘄𝗿𝗶𝗴𝗵𝘁: browser automation

*   𝘀𝗲𝗻𝘁𝗿𝘆: error monitoring

*   𝗻𝗼𝘁𝗶𝗼𝗻: read and write docs

**𝗛𝗼𝗼𝗸𝘀——确定性自动化**

关于 CLAUDE.md 指令的事情是——它们只是建议。Claude 大多数时候遵循，但不是所有时候。你不能依赖一个语言模型总是运行你的 linter。总是格式化你的代码。总是检查危险命令。

hooks 让这些行为**确定性**的。它们是在 Claude 工作流的特定时刻自动触发的事件处理器。你的 shell 脚本每次都会运行，没有例外。

𝗰𝗼𝗻𝗳𝗶𝗴𝘂𝗿𝗲 𝗶𝘁 𝗶𝗻 .𝗺𝗰𝗽.𝗷𝘀𝗼𝗻 𝗮𝘁 𝘆𝗼𝘂𝗿 𝗽𝗿𝗼𝗷𝗲𝗰𝘁 𝗿𝗼𝗼𝘁:

```
{
  "mcpServers": {
    "github": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "your_token"
      }
    }
  }
}
```

**你最会用的事件：**

*   **𝗣𝗿𝗲𝗧𝗼𝗼𝗹𝗨𝘀𝗲**：在任何工具运行之前触发。你的安全门。在这儿拦截危险命令。
*   **𝗣𝗼𝘀𝘁𝗧𝗼𝗼𝗹𝗨𝘀𝗲**：工具成功之后触发。自动格式化、自动 lint、自动验证。
*   **𝗦𝘁𝗼𝗽**：Claude 完成一项任务时触发。质量门。"测试必须通过才算完成"。
*   **𝗨𝘀𝗲𝗿𝗣𝗿𝗼𝗺𝗽𝘁𝗦𝘂𝗯𝗺𝗶𝘁**：你按回车时触发。提示验证。
*   **𝗡𝗼𝘁𝗶𝗳𝗶𝗰𝗮𝘁𝗶𝗼𝗻**：Claude 需要你注意时的桌面通知。

这是一个真实的 hooks 配置，auto-format Claude 处理的每个文件并拦截危险的 bash 命令：

```
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit|MultiEdit",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '.tool_input.file_path' | xargs npx prettier --write 2>/dev/null"
          }
        ]
      }
    ],
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "$CLAUDE_PROJECT_DIR/.claude/hooks/bash-firewall.sh"
          }
        ]
      }
    ]
  }
}
```

bash 防火墙脚本从 stdin 读取命令，检查危险模式（rm -rf, git push --force, DROP TABLE），然后以退出码 2 阻止。退出码 0 = 放行。退出码 1 = 警告但继续。退出码 2 = 完全阻止。

一个 Stop hook 运行 npm test 并在失败时以退出码 2 退出，会阻止 Claude 在套件不绿的情况下宣布"完成了"。不再有"我好了！"但 3 个测试还在失败的情况。

hooks 不会在会话中热重载，改了要重启。而且它们以你的完整用户权限运行，所以要引用你的 shell 变量并验证 JSON 输入。

[![Image 8: Image](./img_0956f87e.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037973574066282496)

𝗻𝗼𝘄 𝘆𝗼𝘂 𝗰𝗮𝗻 𝗱𝗼 𝘁𝗵𝗶𝗻𝗴𝘀 𝗹𝗶𝗸𝗲:

```
claude "find all open bugs in our github repo tagged 'critical' and summarize them"
claude "query the database for users who signed up this week and post the count to #metrics on slack"
claude "check sentry for the top 5 errors this week and create github issues for each one"
```

one tool, connected to everything. i have claude pulling github issues, reading my database, and posting summaries to slack in one conversation. no switching tabs. no context switching. no copy-pasting between tools.

[![Image 7: Image](./img_2d504f97.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037960839433748480)

**𝗦𝗸𝗶𝗹𝗹𝘀——按需调用的可复用工作流**

skills 是让我意识到这个兔子洞有多深的功能。

skill 是一个工作流，Claude 可以根据上下文自主调用，或者你可以用斜杠命令触发。skills 监控对话并在恰当的时刻行动。

𝗵𝗼𝗼𝗸𝘀: 𝗱𝗲𝘁𝗲𝗿𝗺𝗶𝗻𝗶𝘀𝘁𝗶𝗰 𝗮𝘂𝘁𝗼𝗺𝗮𝘁𝗶𝗼𝗻

here's the thing about CLAUDE.md instructions, they're suggestions. claude follows them most of the time, not all of the time. you can't rely on a language model to always run your linter. always format your code. always check for dangerous commands.

hooks make these behaviors 𝗱𝗲𝘁𝗲𝗿𝗺𝗶𝗻𝗶𝘀𝘁𝗶𝗰. they're event handlers that fire automatically at specific points in claude's workflow. your shell script runs every time, no exceptions.

**𝗘𝗮𝗰𝗵 𝘀𝗸𝗶𝗹𝗹 𝗹𝗶𝘃𝗲𝘀 𝗶𝗻 𝗶𝘁𝘀 𝗼𝘄𝗻 𝘀𝘂𝗯𝗱𝗶𝗿𝗲𝗰𝘁𝗼𝗿𝘆 𝘄𝗶𝘁𝗵 𝗮 𝗦𝗞𝗜𝗟𝗟.𝗺𝗱 𝗳𝗶𝗹𝗲：**

```
.claude/skills/
├── security-review/
│   ├── SKILL.md
│   └── DETAILED_GUIDE.md
└── deploy/
    ├── SKILL.md
    └── templates/
        └── release-notes.md
```

𝘁𝗵𝗲 𝗲𝘃𝗲𝗻𝘁𝘀 𝘆𝗼𝘂'𝗹𝗹 𝘂𝘀𝗲 𝗺𝗼𝘀𝘁:

*   𝗣𝗿𝗲𝗧𝗼𝗼𝗹𝗨𝘀𝗲: fires before any tool runs. your security gate. block dangerous commands here.

*   𝗣𝗼𝘀𝘁𝗧𝗼𝗼𝗹𝗨𝘀𝗲: fires after a tool succeeds. auto-format, auto-lint, auto-validate.

*   𝗦𝘁𝗼𝗽: fires when claude finishes a task. quality gate. "tests must pass before you're done."

*   𝗨𝘀𝗲𝗿𝗣𝗿𝗼𝗺𝗽𝘁𝗦𝘂𝗯𝗺𝗶𝘁: fires when you press enter. prompt validation.

*   𝗡𝗼𝘁𝗶𝗳𝗶𝗰𝗮𝘁𝗶𝗼𝗻: desktop alerts when claude needs your attention.

here's a real hooks config that auto-formats every file claude touches and blocks dangerous bash commands:

```
{
  "hooks": {
    "PostToolUse": [
      {
        "matcher": "Write|Edit|MultiEdit",
        "hooks": [
          {
            "type": "command",
            "command": "jq -r '.tool_input.file_path' | xargs npx prettier --write 2>/dev/null"
          }
        ]
      }
    ],
    "PreToolUse": [
      {
        "matcher": "Bash",
        "hooks": [
          {
            "type": "command",
            "command": "$CLAUDE_PROJECT_DIR/.claude/hooks/bash-firewall.sh"
          }
        ]
      }
    ]
  }
}
```

the bash firewall script reads the command from stdin, checks it against dangerous patterns (rm -rf, git push --force, DROP TABLE), and exits with code 2 to block it. exit 0 = let it through. exit 1 = warn but continue. exit 2 = block completely.

a Stop hook that runs npm test and exits with code 2 on failure will prevent claude from declaring "done" until the suite is green. no more "i'm done!" when 3 tests are failing.

hooks don't hot-reload mid-session, restart if you change them. and they run with your full user permissions, so quote your shell variables and validate your JSON input.

[![Image 8: Image](./img_0956f87e.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037973574066282496)

**𝗧𝗵𝗲 𝗦𝗞𝗜𝗟𝗟.𝗺𝗱 𝘂𝘀𝗲𝘀 𝗬𝗔𝗠𝗟 𝗳𝗿𝗼𝗻𝘁𝗺𝗮𝘁𝘁𝗲𝗿 𝘁𝗼 𝗱𝗲𝘀𝗰𝗿𝗶𝗯𝗲 𝘄𝗵𝗲𝗻 𝘁𝗼 𝗮𝗰𝘁𝗶𝘃𝗮𝘁𝗲：**

Analyze the codebase for security vulnerabilities:

1.   SQL injection and XSS risks

2.   Exposed credentials or secrets

3.   Insecure configurations

4.   Authentication and authorization gaps

Report findings with severity ratings and specific remediation steps. Reference security-standards.md for our security standards.

当你 说"审查这个 PR 的安全问题"时，Claude 读取描述，识别到匹配，然后自动调用 skill。或者你直接调用：/security-review。

skill 和命令的关键区别：**skills 可以 bundl e 辅助文件。**reference security-standards.md 会拉取一个 DETAILED_GUIDE.md，那是和 SKILL.md 在同一目录的详细文档。命令是单文件。skills 是包。

那个在 X 上走红的 /last30days skill 就是一个完美例子——有人构建了一个 skill，扫描过去 30 天任何主题的 Reddit 和 X，综合社区已经摸索出来的东西，然后给你写好可用的提示。输入 /last30days prompting techniques for legal questions，它返回真正的律师和高级用户实际在用的框架。这就是你用 skills 可以构建的东西。

个人 skills 放在 ~/.claude/skills/，可在所有项目中使用。

𝘀𝗸𝗶𝗹𝗹𝘀: 𝗿𝗲𝘂𝘀𝗮𝗯𝗹𝗲 𝘄𝗼𝗿𝗸𝗳𝗹𝗼𝘄𝘀 𝗼𝗻 𝗱𝗲𝗺𝗮𝗻𝗱

skills are the feature that made me realize how deep this rabbit hole goes.

a skill is a workflow that claude can invoke on its own based on context, or that you can trigger with a slash command. skills watch the conversation and act when the moment is right.

**𝗣𝗹𝗮𝗻 𝗺𝗼𝗱𝗲——建造之前先思考**

这个功能把我从自己的冲动中拯救了无数次，多到数不清。

𝗲𝗮𝗰𝗵 𝘀𝗸𝗶𝗹𝗹 𝗹𝗶𝘃𝗲𝘀 𝗶𝗻 𝗶𝘁𝘀 𝗼𝘄𝗻 𝘀𝘂𝗯𝗱𝗶𝗿𝗲𝗰𝘁𝗼𝗿𝘆 𝘄𝗶𝘁𝗵 𝗮 𝗦𝗞𝗜𝗟𝗟.𝗺𝗱 𝗳𝗶𝗹𝗲:

```
.claude/skills/
├── security-review/
│   ├── SKILL.md
│   └── DETAILED_GUIDE.md
└── deploy/
    ├── SKILL.md
    └── templates/
        └── release-notes.md
```

**𝗕𝗲𝗳𝗼𝗿𝗲 𝘆𝗼𝘂 𝗹𝗲𝘁 𝗖𝗹𝗮𝘂𝗱𝗲 𝗹𝗼𝗼𝘀𝗲 𝗼𝗻 𝗮 𝗯𝗶𝗴 𝗿𝗲𝗳𝗮𝗰𝘁𝗼𝗿（在你让 Claude 放开手脚做大重构之前）：**

```
按两次 `Shift+Tab` 进入 plan 模式
claude "analyze the database layer and propose a migration to TypeORM"
```

Claude 探索你的代码库，读取相关文件，分析架构，然后给出计划。不做任何修改。不改动任何东西。只有分析和提议方案。

你审查它。调整它。提问。找漏洞。然后当你有信心了，批准，让它实施。

这防止了"Claude 重写了我整个项目，但我没要求它这么做"的时刻。相信我，那个时刻一点都不好玩。先计划，再建造。永远如此。

𝘁𝗵𝗲 𝗦𝗞𝗜𝗟𝗟.𝗺𝗱 𝘂𝘀𝗲𝘀 𝗬𝗔𝗠𝗟 𝗳𝗿𝗼𝗻𝘁𝗺𝗮𝘁𝘁𝗲𝗿 𝘁𝗼 𝗱𝗲𝘀𝗰𝗿𝗶𝗯𝗲 𝘄𝗵𝗲𝗻 𝘁𝗼 𝗮𝗰𝘁𝗶𝘃𝗮𝘁𝗲:

Analyze the codebase for security vulnerabilities:

1.   SQL injection and XSS risks

2.   Exposed credentials or secrets

3.   Insecure configurations

4.   Authentication and authorization gaps

Report findings with severity ratings and specific remediation steps. Reference

.md for our security standards.

when you say "review this PR for security issues," claude reads the description, recognizes it matches, and invokes the skill automatically. or you call it directly: /security-review.

the key difference from commands: 𝘀𝗸𝗶𝗹𝗹𝘀 𝗰𝗮𝗻 𝗯𝘂𝗻𝗱𝗹𝗲 𝘀𝘂𝗽𝗽𝗼𝗿𝘁𝗶𝗻𝗴 𝗳𝗶𝗹𝗲𝘀 𝗮𝗹𝗼𝗻𝗴𝘀𝗶𝗱𝗲 𝘁𝗵𝗲𝗺. the

.md reference pulls in a detailed document that lives right next to SKILL.md. commands are single files. skills are packages.

the /last30days skill that went viral on X is a perfect example, someone built a skill that scans Reddit and X from the last 30 days on any topic, synthesizes what the community has figured out, and writes you ready-to-use prompts. type /last30days prompting techniques for legal questions and it returns frameworks real lawyers and power users are actually using. that's the kind of thing you can build with skills.

personal skills go in ~/.claude/skills/ and are available across all your projects.

**𝗠𝗲𝗺𝗼𝗿𝘆 𝘀𝘆𝘀𝘁𝗲𝗺——你用得越多，它就越聪明**

Claude 会跨会话记住事情。自动地。

纠正它一次——"这个项目不要用 class components，我们用 hooks"——它就会保存那个偏好。下次会话，它已经知道了。你不用重复自己。

用 /memory 管理。存储在 ~/.claude/projects/<project>/memory/。

CLAUDE.md（团队知识）+ 自动记忆（个人学习）的组合意味着 **Claude 会复利增长**。你用得越多，它就越好用。同一项目第一周的 Claude 和第八周的 Claude 是完全不同的两种动物。

𝗽𝗹𝗮𝗻 𝗺𝗼𝗱𝗲: 𝘁𝗵𝗶𝗻𝗸 𝗯𝗲𝗳𝗼𝗿𝗲 𝘆𝗼𝘂 𝗯𝘂𝗶𝗹𝗱

this one saved me from myself more times than i can count.

**𝗖𝗼𝗺𝗽𝘂𝘁𝗲𝗿 𝘂𝘀𝗲**

这个功能在 2026 年 3 月刚推出，它很野。

Claude 现在可以直接控制你的电脑了：

*   打开应用程序
*   操控浏览器
*   填写电子表格
*   与任何 GUI 交互
*   截图并对看到的内容做出反应

无需设置。通过远程控制从手机也能用。

我还没深入研究这个——还在实验。但它蕴含的可能性是疯狂的。想象一下告诉 Claude "打开 Figma，截屏最新设计，然后用 React 实现出来"。我们正在接近那一天。

𝗯𝗲𝗳𝗼𝗿𝗲 𝘆𝗼𝘂 𝗹𝗲𝘁 𝗰𝗹𝗮𝘂𝗱𝗲 𝗹𝗼𝗼𝘀𝗲 𝗼𝗻 𝗮 𝗯𝗶𝗴 𝗿𝗲𝗳𝗮𝗰𝘁𝗼𝗿:

```
hit `Shift+Tab` twice to enter plan mode
claude "analyze the database layer and propose a migration to TypeORM"
```

claude explores your codebase, reads the relevant files, analyzes the architecture then presents a plan. no changes made. nothing modified. just analysis and a proposed approach.

you review it. adjust it. ask questions. poke holes. then when you're confident, approve and let it implement.

this prevents the "claude rewrote my entire project and i didn't ask for that" moment. trust me, that moment is not fun. plan first, build second. always.

**𝗣𝗼𝘄𝗲𝗿 𝘂𝘀𝗲𝗿 𝘄𝗼𝗿𝗸𝗳𝗹𝗼𝘄𝘀（高级用户工作流）**

这些模式让我从"使用 Claude Code"进化到"用 Claude Code 搞事情"。这些都不是文档里写的。

𝗺𝗲𝗺𝗼𝗿𝘆 𝘀𝘆𝘀𝘁𝗲𝗺: 𝗶𝘁 𝗴𝗲𝘁𝘀 𝘀𝗺𝗮𝗿𝘁𝗲𝗿 𝘁𝗵𝗲 𝗺𝗼𝗿𝗲 𝘆𝗼𝘂 𝘂𝘀𝗲 𝗶𝘁

claude remembers things across sessions. automatically.

correct it once "don't use class components in this project, we use hooks" and it saves that preference. next session, it already knows. you don't repeat yourself.

manage it with /memory. stored at ~/.claude/projects/<project>/memory/.

the combination of CLAUDE.md (team knowledge) + auto memory (personal learning) means 𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝗺𝗽𝗼𝘂𝗻𝗱𝘀. it gets better the more you use it. week 1 claude and week 8 claude on the same project are different animals.

**𝗧𝗵𝗲 "𝗶𝗻𝘁𝗲𝗿𝘃𝗶𝗲𝘄 𝗺𝗲" 𝘁𝗲𝗰𝗵𝗻𝗶𝗾𝘂𝗲（"采访我"技巧）**

要启动一个复杂项目？别写一个巨大的 prompt。别试图一开始就想到所有事情。就说：

`claude "interview me in detail about what i want to build"`

让 Claude 向你提问。它会问技术栈、需求、边缘情况、现有代码、部署目标、用户类型——那些你会在 prompt 里忘记提到的东西。10 分钟的来回给 Claude 的上下文比 500 字的 prompt 好得多。

我现在每个新功能都用这个。每一个。

𝗰𝗼𝗺𝗽𝘂𝘁𝗲𝗿 𝘂𝘀𝗲

this one dropped in march 2026 and it's wild.

claude can now control your computer directly:

*   open applications

*   navigate browsers

*   fill out spreadsheets

*   interact with any GUI

*   take screenshots and react to what it sees

no setup required. works from your phone via remote control.

i haven't gone deep on this one yet still experimenting. but the implications are insane. imagine telling claude to "open figma, screenshot the latest design, then implement it in react." we're getting there.

**𝗧𝗵𝗲 𝗿𝗲𝘀𝗲𝗮𝗿𝗰𝗵 → 𝗶𝗺𝗽𝗹𝗲𝗺𝗲𝗻𝘁 𝘀𝗽𝗹𝗶𝘁（研究→实现拆分）**

永远不要让 Claude 实现它还不理解的东西。

```
阶段 1: 按两次 `Shift+Tab` → plan 模式 → `"explore the codebase and understand how payments work"`
审查分析。确保它真的理解了。
阶段 2: `"implement subscription billing based on your analysis"`
```

"直接开干"和"先理解，再开干"的质量差异天差地别。在遗留代码库里尤其如此，因为没有任何东西在你期望的位置。

𝗽𝗼𝘄𝗲𝗿 𝘂𝘀𝗲𝗿 𝘄𝗼𝗿𝗸𝗳𝗹𝗼𝘄𝘀

these are the patterns that took me from "using claude code" to "being dangerous with claude code." none of this is in the docs.

**𝗣𝗮𝗿𝗮𝗹𝗹𝗲𝗹 𝘄𝗼𝗿𝗸 𝘄𝗶𝘁𝗵 𝘄𝗼𝗿𝗸𝘁𝗿𝗲𝗲𝘀（用 worktree 并行工作）**

```
终端 1: `claude --worktree auth-feature`
终端 2: `claude --worktree billing-feature`
```

每个获得一个隔离的 git 分支。两个独立 Claude 会话同时开发两个功能。准备好了再合并。

我有时候跑 3 个 worktree。终端 1 跑 auth feature，终端 2 跑 API endpoint，终端 3 跑测试套件。全并行。全隔离。生产力是真的离谱。

𝘁𝗵𝗲 "𝗶𝗻𝘁𝗲𝗿𝘃𝗶𝗲𝘄 𝗺𝗲" 𝘁𝗲𝗰𝗵𝗻𝗶𝗾𝘂𝗲

starting a complex project? don't write a massive prompt. don't try to think of everything upfront. just say:

`claude "interview me in detail about what i want to build"`

let claude ask YOU the questions. it'll ask about tech stack, requirements, edge cases, existing code, deployment targets, user types things you'd forget to mention in a prompt. 10 minutes of back-and-forth gives claude better context than a 500-word prompt ever could.

i use this for every new feature now. every single one.

**𝗧𝗵𝗲 𝗰𝗼𝗻𝘁𝗲𝘅𝘁 𝗺𝗮𝗻𝗮𝗴𝗲𝗺𝗲𝗻𝘁 𝗴𝗮𝗺𝗲（上下文管理策略）**

**这是 #1 技能，把普通 Claude Code 用户和高级用户区分开来。**

上下文窗口大约 200K token。听起来很多。当你深入一个会话时就不是了。随着它被填满：

*   旧的工具输出先被清除
*   对话被自动总结
*   早期的指令可能会丢失

𝘁𝗵𝗲 𝗿𝗲𝘀𝗲𝗮𝗿𝗰𝗵 → 𝗶𝗺𝗽𝗹𝗲𝗺𝗲𝗻𝘁 𝘀𝗽𝗹𝗶𝘁

never let claude implement something it doesn't understand first.

```
phase 1: `Shift+Tab` twice → plan mode → `"explore the codebase and understand how payments work"`
review the analysis. make sure it actually gets it.
phase 2: `"implement subscription billing based on your analysis"`
```

the quality difference between "just build it" and "understand it first, then build it" is night and day. especially on legacy codebases where nothing is where you'd expect it.

**𝗔𝗰𝘁𝗶𝘃𝗲𝗹𝘆 𝗺𝗮𝗻𝗮𝗴𝗲 𝗶𝘁（主动管理它）：**

```
`/compact` — 手动总结对话以节省空间
`/clear` — 在不相关任务之间全新开始
`/cost` — 看看什么在消耗你的 token 以及消耗在哪里
用子智能体处理冗长操作（测试输出、日志分析、大文件读取）
把重复性指令放在 CLAUDE.md 里，不要放在对话里
```

𝗽𝗮𝗿𝗮𝗹𝗹𝗲𝗹 𝘄𝗼𝗿𝗸 𝘄𝗶𝘁𝗵 𝘄𝗼𝗿𝗸𝘁𝗿𝗲𝗲𝘀

```
terminal 1: `claude --worktree auth-feature`
terminal 2: `claude --worktree billing-feature`
```

each gets an isolated git branch. two features developed simultaneously by two separate claude sessions. merge when ready.

i run 3 worktrees sometimes. auth feature in terminal 1, API endpoint in terminal 2, test suite in terminal 3. all running in parallel. all isolated. it's obscene productivity.

**黄金法则：尝试两次都失败了，就停下来。别继续。** /clear 然后从头写一个更好的初始 prompt。带着清晰 prompt 的全新上下文几乎总是比被失败方法污染的上下文效果好得多。我为此浪费了大约 6 小时才学会这个教训。

𝘁𝗵𝗲 𝗰𝗼𝗻𝘁𝗲𝘅𝘁 𝗺𝗮𝗻𝗮𝗴𝗲𝗺𝗲𝗻𝘁 𝗴𝗮𝗺𝗲

**𝗧𝗵𝗲 ! 𝗽𝗿𝗲𝗳𝗶𝘅 𝘁𝗿𝗶𝗰𝗸（! 前缀技巧）**

**在任何命令前加 ! 就能直接在 shell 里运行，不需要 Claude：**

```
!git status
!npm test
!cat src/config.ts
```

输出自动添加到 Claude 的上下文里。非常适合快速向 Claude 展示正在发生什么，而不用让它运行命令然后等待权限提示。

𝘁𝗵𝗶𝘀 𝗶𝘀 𝘁𝗵𝗲 #𝟭 𝘀𝗸𝗶𝗹𝗹 𝘁𝗵𝗮𝘁 𝘀𝗲𝗽𝗮𝗿𝗮𝘁𝗲𝘀 𝗴𝗼𝗼𝗱 𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝗱𝗲 𝘂𝘀𝗲𝗿𝘀 𝗳𝗿𝗼𝗺 𝗴𝗿𝗲𝗮𝘁 𝗼𝗻𝗲𝘀.

the context window is ~200K tokens. sounds like a lot. it's not when you're deep in a session. as it fills up:

*   older tool outputs get cleared first

*   conversation gets auto-summarized

*   early instructions may be lost

**𝗘𝘅𝘁𝗲𝗿𝗻𝗮𝗹 𝗲𝗱𝗶𝘁𝗼𝗿 𝗳𝗼𝗿 𝗹𝗼𝗻𝗴 𝗽𝗿𝗼𝗺𝗽𝘁𝘀（长 prompt 用外部编辑器）**

Ctrl+G 打开你的系统编辑器（vim、VS Code，随你怎么配置的）。用语法高亮写复杂的多行 prompt。保存关闭——发送给 Claude。

比在单行终端输入里打一大段字好多了。我现在每个超过 2 句的 prompt 都用这个。

𝗺𝗮𝗻𝗮𝗴𝗲 𝗶𝘁 𝗮𝗰𝘁𝗶𝘃𝗲𝗹𝘆:

```
`/compact` — manually summarize the conversation to save space
`/clear` — fresh start between unrelated tasks
`/cost` — see what's eating your tokens and where
use subagents for verbose operations (test output, log analysis, large file reads)
put recurring instructions in CLAUDE.md, not in conversation
```

**𝗧𝗵𝗲 𝗱𝗼𝘂𝗯𝗹𝗲-𝗲𝘀𝗰𝗮𝗽𝗲 𝗿𝗲𝘄𝗶𝗻𝗱（双击 Escape 回退）**

这个很关键，没人提过。

Claude 走错方向了？双击 Escape，会出现回退菜单。你可以撤销上一个操作、往回更多步、或者"Summarize from here"——压缩失败的尝试同时保留有用的上下文。比 /clear 好多了，因为不会失去一切，只失去错误的部分。

[![Image 9: Image](./img_14bbc638.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037947336899665920)

把这张表打印出来。贴到显示器上。说真的。

𝘁𝗵𝗲 𝗴𝗼𝗹𝗱𝗲𝗻 𝗿𝘂𝗹𝗲: after two failed attempts at something, stop. don't keep going. /clear and write a better initial prompt from scratch. a fresh context with a clear prompt almost always works better than a polluted context full of failed approaches. i learned this at the cost of about 6 hours of wasted time.

**𝗣𝗲𝗿𝗺𝗶𝘀𝘀𝗶𝗼𝗻 𝗺𝗼𝗱𝗲𝘀（权限模式）**

Claude Code 有不同的自主级别。知道什么时候用哪一种很重要：

[![Image 10: Image](./img_046a769d.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037947627908833280)

从 default 开始。一旦信任它了（我大约花了一周），移到 acceptedEdits。做大型重构之前用 plan 做探索。

𝘁𝗵𝗲 ! 𝗽𝗿𝗲𝗳𝗶𝘅 𝘁𝗿𝗶𝗰𝗸

**𝗬𝗼𝘂 𝗰𝗮𝗻 𝗮𝗹𝘀𝗼 𝘄𝗵𝗶𝘁𝗲𝗹𝗶𝘀𝘁 𝗮𝗻𝗱 𝗯𝗹𝗮𝗰𝗸𝗹𝗶𝘀𝘁 𝘀𝗽𝗲𝗰𝗶𝗳𝗶𝗰 𝗰𝗼𝗺𝗺𝗮𝗻𝗱𝘀 𝗶𝗻 .𝗰𝗹𝗮𝘂𝗱𝗲/𝘀𝗲𝘁𝘁𝗶𝗻𝗴𝘀.𝗷𝘀𝗼𝗻：**

```
{
  "permissions": {
    "allow": [
      "Bash(npm run *)",
      "Bash(git status)",
      "Bash(git diff *)",
      "Read",
      "Write",
      "Edit"
    ],
    "deny": [
      "Bash(rm -rf *)",
      "Bash(curl *)",
      "Read(./.env)",
      "Read(./.env.*)"
    ]
  }
}
```

allow 列表不用问直接跑。deny 列表完全阻止。两者都没列的，Claude 先问。这块中间地带是刻意设计的。安全网但不管得太细。

𝘁𝘆𝗽𝗲 ! 𝗯𝗲𝗳𝗼𝗿𝗲 𝗮𝗻𝘆 𝗰𝗼𝗺𝗺𝗮𝗻𝗱 𝘁𝗼 𝗿𝘂𝗻 𝗶𝘁 𝗱𝗶𝗿𝗲𝗰𝘁𝗹𝘆 𝗶𝗻 𝘆𝗼𝘂𝗿 𝘀𝗵𝗲𝗹𝗹 𝘄𝗶𝘁𝗵𝗼𝘂𝘁 𝗰𝗹𝗮𝘂𝗱𝗲:

```
!git status
!npm test
!cat src/config.ts
```

the output gets added to claude's context automatically. great for quickly showing claude what's happening without asking it to run the command and waiting for permission prompts.

**𝗖𝗹𝗮𝘂𝗱𝗲 𝗖𝗼𝗱𝗲 𝘃𝘀 𝗖𝘂𝗿𝘀𝗼𝗿 𝘃𝘀 𝗖𝗼𝗽𝗶𝗹𝗼𝘁**

**最诚实的对比。没有 fanboy 能量。只是我的真实体验：**

𝗲𝘅𝘁𝗲𝗿𝗻𝗮𝗹 𝗲𝗱𝗶𝘁𝗼𝗿 𝗳𝗼𝗿 𝗹𝗼𝗻𝗴 𝗽𝗿𝗼𝗺𝗽𝘁𝘀

Ctrl+G opens your system editor (vim, VS Code, whatever you have set). write complex multi-line prompts with syntax highlighting. save and close it sends to claude.

way better than typing a paragraph into a single-line terminal input. i use this for every prompt longer than 2 sentences now.

**𝗖𝗹𝗮𝘂𝗱𝗲 𝗖𝗼𝗱𝗲**：终端原生，真正自主。读取你整个代码库。自主多文件修改。最佳使用场景：复杂重构、架构决策、全代码库变更、调试棘手问题、涉及 3+ 个文件的一切。感觉像一个冷静的资深工程师，从不疲倦，从不评判你的代码。

𝘁𝗵𝗲 𝗱𝗼𝘂𝗯𝗹𝗲-𝗲𝘀𝗰𝗮𝗽𝗲 𝗿𝗲𝘄𝗶𝗻𝗱

this one's clutch and nobody mentions it.

claude went the wrong direction? double-tap Escape, and you get a rewind menu. you can undo the last action, go back further, or "summarize from here" which compresses the failed attempt while keeping the useful context. way better than /clear because you don't lose everything, just the mistake.

[![Image 9: Image](./img_14bbc638.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037947336899665920)

print this table. tape it to your monitor. seriously.

**𝗖𝘂𝗿𝘀𝗼𝗿**：IDE 原生（VS Code 分支）。日常驾驶舱最佳选择，tab 补全和内联建议。在编辑器里反馈循环更紧。自主性较低但小改动更快。最佳使用场景：快速编辑、内联补全、写代码时保持心流。

𝗽𝗲𝗿𝗺𝗶𝘀𝘀𝗶𝗼𝗻 𝗺𝗼𝗱𝗲𝘀

claude code has different levels of autonomy. knowing when to use each is important:

[![Image 10: Image](./img_046a769d.jpg)](https://x.com/Axel_bitblaze69/article/2037978621684621428/media/2037947627908833280)

start with default. move to acceptEdits once you trust it (took me about a week). use plan for exploration before big refactors.

**𝗚𝗶𝘁𝗛𝘂𝗯 𝗖𝗼𝗽𝗶𝗹𝗼𝘁**：插件方式。免费额度最好（$10/mo）。企业选择最安全。自主能力在提升但仍落后于 Claude Code 和 Cursor。

这里大多数人都没意识到的事情是：**你不必选一个。**

组合策略是真实存在的，而且大多数高级用户实际上就是这么做的。Cursor 做日常 tab 补全和内联编辑。Claude Code 做重活——重构、新功能、调试、架构决策。

数据也支持这个结论：经验丰富的开发者平均使用 **2.3 个 AI 编码工具**。不是用一个替代另一个，而是用对的工具做对的事。

Claude Code 在不到一年的时间里从零成为 **#1 最受欢迎的 AI 编码工具**。2026 年初的调查中，46% 的开发者给它评最喜欢。95% 的开发者现在每周使用 AI 工具。75% 的人用 AI 做超过一半的编码工作。

游戏已经变了。永久地。问题不再是"要不要用 AI 编码工具"，而是"你能多快掌握它们"。

𝗖𝗹𝗮𝘂𝗱𝗲 𝗖𝗼𝗱𝗲 生态系统

社区在 Claude Code 之上已经构建了大量的工具。以下是值得知道的：

𝘆𝗼𝘂 𝗰𝗮𝗻 𝗮𝗹𝘀𝗼 𝘄𝗵𝗶𝘁𝗲𝗹𝗶𝘀𝘁 𝗮𝗻𝗱 𝗯𝗹𝗮𝗰𝗸𝗹𝗶𝘀𝘁 𝘀𝗽𝗲𝗰𝗶𝗳𝗶𝗰 𝗰𝗼𝗺𝗺𝗮𝗻𝗱𝘀 𝗶𝗻 .𝗰𝗹𝗮𝘂𝗱𝗲/𝘀𝗲𝘁𝘁𝗶𝗻𝗴𝘀.𝗷𝘀𝗼𝗻:

```
{
  "permissions": {
    "allow": [
      "Bash(npm run *)",
      "Bash(git status)",
      "Bash(git diff *)",
      "Read",
      "Write",
      "Edit"
    ],
    "deny": [
      "Bash(rm -rf *)",
      "Bash(curl *)",
      "Read(./.env)",
      "Read(./.env.*)"
    ]
  }
}
```

the allow list runs without asking. the deny list is blocked entirely. anything not in either list claude asks first. that middle ground is intentional. safety net without micromanaging every command.

**𝗦𝘂𝗽𝗲𝗿𝗽𝗼𝘄𝗲𝗿𝘀（obra/superpowers）**：一套面向 AI 编码智能体的完整开发方法论。GitHub 上 117K+ star。它改变了你的智能体写代码的方式——强制它先头脑风暴、创建详细实施计划、启动子智能体驱动开发、做两阶段代码审查后才宣布完成。如果你觉得 Claude Code 有时候产出的是"意大利面条代码"，这就是解药。

𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝗱𝗲 𝘃𝘀 𝗰𝘂𝗿𝘀𝗼𝗿 𝘃𝘀 𝗰𝗼𝗽𝗶𝗹𝗼𝘁

**𝗚𝗦𝗗——𝗚𝗲𝘁 𝗦𝗵𝗶𝘁 𝗗𝗼𝗻𝗲（gsd-build/get-shit-done）**：面向 Claude Code 的元提示和上下文管理系统。轻量但强大。解决了上下文退化问题。

𝘁𝗵𝗲 𝗵𝗼𝗻𝗲𝘀𝘁 𝗰𝗼𝗺𝗽𝗮𝗿𝗶𝘀𝗼𝗻. 𝗻𝗼 𝗳𝗮𝗻𝗯𝗼𝘆 𝗲𝗻𝗲𝗿𝗴𝘆. 𝗷𝘂𝘀𝘁 𝘄𝗵𝗮𝘁 𝗶'𝘃𝗲 𝗲𝘅𝗽𝗲𝗿𝗶𝗲𝗻𝗰𝗲𝗱:

**𝗮𝘄𝗲𝘀𝗼𝗺𝗲-𝗰𝗹𝗮𝘂𝗱𝗲-𝗰𝗼𝗱𝗲**：社区策划的 Claude Code 最优质资源集合——skills、智能体、MCP 服务器等。你探索外面有什么的起点。

𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝗱𝗲: terminal-native, truly agentic. reads your entire codebase. autonomous multi-file changes. best for: complex refactors, architecture decisions, codebase-wide changes, debugging gnarly issues, anything touching more than 3 files. feels like a calm senior engineer who never gets tired and never judges your code.

**/𝗹𝗮𝘀𝘁𝟯𝟬𝗱𝗮𝘆𝘀 𝘀𝗸𝗶𝗹𝗹**：那个在 X 上走红的 skill。扫描过去 30 天任何主题的 Reddit、X、YouTube、Hacker News 和整个网络。综合社区知识为可直接使用的提示。输入 /last30days cold email frameworks，它给你找到 3Ps framework、ADA、intention-based triggers——这些东西你自己永远找不到。然后基于真正有效的东西给你写好可用的提示。开源，MIT 许可证。

𝗰𝘂𝗿𝘀𝗼𝗿 IDE-native (VS Code fork). best daily driver for tab completions and inline suggestions. tighter feedback loop in the editor. less autonomous but faster for small changes. best for: quick edits, inline completions, staying in flow while writing code.

**𝗖𝗹𝗮𝘂𝗱𝗲 𝗵𝗼𝘄-𝘁𝗼**：视觉化、示例驱动的 Claude Code 精通指南。视觉型学习者想要结构化教程的最佳资源。

𝗴𝗶𝘁𝗵𝘂𝗯 𝗰𝗼𝗽𝗶𝗹𝗼𝘁: plugin approach. best free tier ($10/mo). safest corporate choice. agentic capabilities are improving but still lag behind both claude code and cursor.

here's what most people don't realize: 𝘆𝗼𝘂 𝗱𝗼𝗻'𝘁 𝗵𝗮𝘃𝗲 𝘁𝗼 𝗽𝗶𝗰𝗸 𝗼𝗻𝗲.

the combo strategy is real and it's what most power users actually do. cursor for daily tab completions and inline edits. claude code for the heavy lifting refactors, new features, debugging, architecture decisions.

the data backs this up: experienced developers use 𝟮.𝟯 𝗔𝗜 𝗰𝗼𝗱𝗶𝗻𝗴 𝘁𝗼𝗼𝗹𝘀 on average. it's not about replacing one with the other. it's about using the right tool for the right job.

claude code went from zero to the #𝟭 𝗺𝗼𝘀𝘁 𝗹𝗼𝘃𝗲𝗱 𝗔𝗜 𝗰𝗼𝗱𝗶𝗻𝗴 𝘁𝗼𝗼𝗹 in under a year. 46% of developers rated it their favorite in early 2026 surveys. 95% of developers now use AI tools weekly. 75% use AI for more than half their coding.

the game has changed. permanently. the question isn't whether to use AI coding tools. it's how fast you can get good at them.

**𝗖𝗹𝗮𝘂𝗱𝗲 𝗺𝗲𝗺**：持久记忆层。如果内置记忆系统不够你用的话。

𝘁𝗵𝗲 𝗰𝗹𝗮𝘂𝗱𝗲 𝗰𝗼𝗱𝗲 𝗲𝗰𝗼𝘀𝘆𝘀𝘁𝗲𝗺

the community has built an insane amount of tooling on top of claude code. here are the ones worth knowing:

**𝗨𝗜 𝗨𝗫 𝗽𝗿𝗼 𝗺𝗮𝘅**：面向 Claude Code 的设计专注工具。当你想让 Claude 关心东西长什么样，而不只是关心它怎么运作的时候用它。

𝘀𝘂𝗽𝗲𝗿𝗽𝗼𝘄𝗲𝗿𝘀 (obra/superpowers): a full development methodology for AI coding agents. 117K+ stars on github. it changes how your agent writes code forces it to brainstorm first, create detailed implementation plans, launch subagent-driven development, and do two-stage code review before declaring done. if you feel like claude code produces "spaghetti" sometimes, this is the fix.

**𝗻𝟴𝗻-𝗠𝗖𝗣**：把 Claude Code 连接到 n8n 工作流自动化。如果你已经在用 n8n，这是毫无疑问的集成。

生态系统增长很快。每周都有新工具。以上是我实际用过或见过产生真实结果的。不是每个东西的精心挑选列表，只是现在真正重要的那些。

常见错误（我都犯过）

𝗚𝗦𝗗 𝗴𝗲𝘁 𝘀𝗵𝗶𝘁 𝗱𝗼𝗻𝗲 (gsd-build/get-shit-done) a meta-prompting and context management system for claude code. lightweight but powerful. solves the context degradation problem.

**1. 在 CLAUDE.md 里写小说** 保持 200 行以内。具体的。可执行的。如果 Claude 忽视你的指令，你的 CLAUDE.md 可能太长了。我有一个 400 行的 CLAUDE.md 简直是一份宣言。精简到 150 行，一切改善了。

𝗮𝘄𝗲𝘀𝗼𝗺𝗲-𝗰𝗹𝗮𝘂𝗱𝗲-𝗰𝗼𝗱𝗲 community-curated collection of the best resources, skills, agents, and MCP servers. your starting point for discovering what's out there.

/𝗹𝗮𝘀𝘁𝟯𝟬𝗱𝗮𝘆𝘀 𝘀𝗸𝗶𝗹𝗹 the one that went viral. scans Reddit, X, YouTube, Hacker News, and the web from the last 30 days on any topic you give it. synthesizes community knowledge into ready-to-use prompts. type /last30days cold email frameworks and it finds the 3 Ps framework, ADA, intention-based triggers stuff you'd never find on your own. then writes you ready-to-use prompts based on what actually works. open source, MIT license.

**2. 任务之间不用 /𝗰𝗹𝗲𝗮𝗿** 关于修复 CSS bug 的对话对于实现新 API endpoint 没有任何有用的上下文。剩余的上下文实际上会损害性能。清理它。全新开始。每次都这样。

𝗰𝗹𝗮𝘂𝗱𝗲 𝗵𝗼𝘄-𝘁𝗼 visual, example-driven guide to mastering claude code. best resource for visual learners who want structured tutorials.

**3. 与之对抗而不是重启** 尝试两次都失败了，上下文被错误方法污染了。Claude 开始引用它自己的错误。/clear 然后写一个更好的 prompt。带着清晰 prompt 的全新上下文几乎总是效果好得多。我为此浪费了大约 6 小时才学会这个教训。

𝗰𝗹𝗮𝘂𝗱𝗲 𝗺𝗲𝗺 persistent memory layer. if the built-in memory system isn't enough for your workflow.

**4. 不用子智能体** 在你的主对话里运行完整测试套件用数百行的输出淹没上下文。委托给子智能体。保持你的主对话干净，专注在真正的工作上。

𝗨𝗜 𝗨𝗫 𝗽𝗿𝗼 𝗺𝗮𝘅 design-focused tooling for claude code. for when you want claude to care about how things look, not just how they work.

**5. 所有东西都用 opus** Sonnet 能以同样的质量处理 90% 的任务。opus 只用于那真正需要深度推理的 10%——复杂架构、棘手调试、微妙逻辑错误。你的钱包会感谢你。我的就感谢了。

𝗻𝟴𝗻-𝗠𝗖𝗣 connects claude code to n8n workflow automation. if you're already using n8n, this is a no-brainer integration.

the ecosystem is growing fast. new tools every week. these are the ones i've actually used or seen produce real results. not a curated list of everything just the ones that matter right now.

**6. 大改动时忽略 plan 模式** 任何涉及 3+ 个文件的都要先计划。始终如此。你花在审查计划的 5 分钟，会在 Claude 走错方向时为你节省 2 小时的清理工作。

𝗰𝗼𝗺𝗺𝗼𝗻 𝗺𝗶𝘀𝘁𝗮𝗸𝗲𝘀 (𝗶 𝗺𝗮𝗱𝗲 𝗮𝗹𝗹 𝗼𝗳 𝘁𝗵𝗲𝘀𝗲)

𝟭. 𝘄𝗿𝗶𝘁𝗶𝗻𝗴 𝗮 𝗻𝗼𝘃𝗲𝗹 𝗶𝗻 𝗖𝗟𝗔𝗨𝗗𝗘.𝗺𝗱 keep it under 200 lines. specific. actionable. if claude's ignoring your instructions, your CLAUDE.md is probably too long. i had a 400-line one that was basically a manifesto. cut it to 150, everything improved.

𝟮. 𝗻𝗼𝘁 𝘂𝘀𝗶𝗻𝗴 /𝗰𝗹𝗲𝗮𝗿 𝗯𝗲𝘁𝘄𝗲𝗲𝗻 𝘁𝗮𝘀𝗸𝘀 a conversation about fixing a CSS bug has zero useful context for implementing a new API endpoint. the leftover context actively hurts performance. clear it. start fresh. every time.

𝟯. 𝗳𝗶𝗴𝗵𝘁𝗶𝗻𝗴 𝗶𝘁 𝗶𝗻𝘀𝘁𝗲𝗮𝗱 𝗼𝗳 𝗿𝗲𝘀𝘁𝗮𝗿𝘁𝗶𝗻𝗴 after two failed attempts, the context is polluted with wrong approaches. claude starts referencing its own mistakes. /clear and write a better prompt. the fresh context almost always nails it. i wasted 6 hours once before learning this.

𝟰. 𝗻𝗼𝘁 𝘂𝘀𝗶𝗻𝗴 𝘀𝘂𝗯𝗮𝗴𝗲𝗻𝘁𝘀 running a full test suite in your main conversation floods the context with hundreds of lines of output. delegate to a subagent. keep your main conversation clean and focused on the actual work.

𝟱. 𝘂𝘀𝗶𝗻𝗴 𝗼𝗽𝘂𝘀 𝗳𝗼𝗿 𝗲𝘃𝗲𝗿𝘆𝘁𝗵𝗶𝗻𝗴 sonnet handles 90% of tasks perfectly. opus is for the 10% that actually needs deep reasoning complex architecture, tricky debugging, subtle logic errors. your wallet will thank you. mine did.

𝟲. 𝗶𝗴𝗻𝗼𝗿𝗶𝗻𝗴 𝗽𝗹𝗮𝗻 𝗺𝗼𝗱𝗲 𝗳𝗼𝗿 𝗯𝗶𝗴 𝗰𝗵𝗮𝗻𝗴𝗲𝘀 always plan first on anything touching more than 3 files. always. the 5 minutes you spend reviewing a plan saves you 2 hours of cleanup when claude goes in the wrong direction.

𝟳. 𝗻𝗼𝘁 𝗺𝗮𝗻𝗮𝗴𝗶𝗻𝗴 𝗰𝗼𝗻𝘁𝗲𝘅𝘁 𝗮𝗰𝘁𝗶𝘃𝗲𝗹𝘆 the context window is a resource. treat it like one. /compact when it's getting long. subagents for verbose operations. CLAUDE.md for instructions instead of repeating them every session. the people who manage context well get dramatically better results than those who don't.

**7. 不主动管理上下文** 上下文窗口是一种资源。像资源一样对待它。当它变长时用 /compact。冗长操作交给子智能体。用 CLAUDE.md 放指令而不是每个会话都重复。那些管理上下文好的人得到了显著更好的结果，比那些不管理的。

总结

Claude Code 不是一种工具。它是一个队友。

一个读你整个代码库的家伙。遵守你的编码标准。运行你的测试。创建你的 PR。记住你的偏好。连接到你的所有工具。而且你用得越多，它就越好。

我已经这样做了两个月。我学了课程、拿了认证、每天做项目。而且我可以绝对自信地告诉你：那些学会与 Claude Code 一起工作的开发者，而不只往它里面粘贴代码的，正在以前所未有的速度发布。

现在是 2026 年。你有机会使用一个 AI 智能体，它能自主导航一个 50000 行的代码库、进行精准的多文件修改、运行你的测试、修复它自己的 bug，并创建带文档的 pull request。你的祖先会梦想拥有这个。

停止收藏关于 AI 的文章。开始用它来构建。

如果这帮到了你，分享给还在往 ChatGPT 复制粘贴的人。他们比你更需要这个。

找到我

𝘁𝗵𝗲 𝗯𝗼𝘁𝘁𝗼𝗺 𝗹𝗶𝗻𝗲

claude code isn't a tool. it's a teammate.

one that reads your entire codebase, follows your coding standards, runs your tests, creates your PRs, remembers your preferences, connects to all your tools, and gets better the more you use it.

i've been at this for 2 months. i've done the courses, got the certs, built projects daily. and i can tell you with absolute confidence the developers who learn to work WITH claude code, not just paste code at it, are shipping at a pace that would've been unthinkable a year ago.

it's 2026. you have access to an AI agent that can autonomously navigate a 50,000-line codebase, make surgical multi-file changes, run your tests, fix its own bugs, and create pull requests with documentation. your ancestors would have dreamed of this.

stop bookmarking articles about AI. start building with it.

if this helped you, share it with someone who's still copy-pasting into chatgpt. they need this more than you do.

find me →
