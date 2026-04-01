---
title: "Troy Hua on X: "How Anthropic Built 7 Layers of Memory and a Dreaming System for Claude Code  (video" / "Troy Hua on X: Anthropic如何为Claude Code构建7层记忆系统和梦境系统（视频）"
source: "https://x.com/troyhua/status/2039052328070734102"
saved_at: "2026-04-01"
tags: ["Claude", "Anthropic", "Memory", "X/Twitter"]
---

# Troy Hua on X: "How Anthropic Built 7 Layers of Memory and a Dreaming System for Claude Code  (video" / "Troy Hua on X: Anthropic如何为Claude Code构建7层记忆系统和梦境系统（视频）

> A comprehensive reverse-engineering of every memory and context management system inside Claude Code's leaked harness — from lightweight token pruning to a "dreaming" system that consolidates memories while you sleep.

> 一份对Claude Code泄露harness中所有记忆和上下文管理系统的全面逆向工程——从亚毫秒级的token裁剪到"梦境"系统，该系统在用户睡眠时整合记忆。

0:19

0:19

LLMs have a fundamental constraint: a fixed context window. Claude Code typically operates with a 200K token window (expandable to 1M with the [1m] suffix). A single coding session can easily blow past this — a few file reads, some grep results, a handful of edit cycles, and you're at the limit.

LLM有一个根本性约束：固定的上下文窗口。Claude Code通常以200K token窗口运行（可通过[1m]后缀扩展至1M）。单个编码会话很容易超出这个限制——几次文件读取、一些grep结果、几次编辑循环，你就会达到上限。

Claude Code solves this with a 7-layer memory architecture that spans from sub-millisecond token pruning to multi-hour background "dreaming" consolidation. Each layer is progressively more expensive but more powerful, and the system is designed so cheaper layers prevent the need for more expensive ones.

Claude Code通过一个7层记忆架构来解决这个问题，该架构涵盖从亚毫秒级token裁剪到多小时后台"梦境"整合。每层都越来越昂贵但也越来越强大，系统设计使得较便宜的层级能够在大多数情况下阻止更昂贵层级的触发。

Everything starts with knowing how many tokens you've used. The canonical function is tokenCountWithEstimation() in src/utils/tokens.ts:

一切从知道你使用了多少token开始。标准函数是src/utils/tokens.ts中的tokenCountWithEstimation()：

> Canonical token count = last API response's usage.input_tokens + rough estimates for messages added since

> 标准token计数 = 上一次API响应的usage.input_tokens + 之后添加消息的粗略估算

The rough estimation uses a simple heuristic: 4 bytes per token for most text, 2 bytes per token for JSON (which tokenizes more densely). Images and documents get a flat 2,000 token estimate regardless of size.

粗略估算使用简单启发式方法：大多数文本每token 4字节，JSON每token 2字节（因为JSON的token密度更高）。图片和文档无论大小都获得固定的2000 token估算。

The system resolves the available context window through a priority chain:

系统通过优先级链来解析可用上下文窗口：

> [1m] model suffix → model capability lookup → 1M beta header → env override → 200K default

> [1m]模型后缀 → 模型能力查询 → 1M beta header → 环境变量覆盖 → 200K默认值

The effective context window subtracts a 20K token reserve for compaction output — you can't use the full window because you need room to generate the summary that saves you.

有效上下文窗口减去20K token的整合输出预留空间——你无法使用完整窗口，因为你需要空间来生成能够拯救你的摘要。

Each layer is triggered by different conditions and has different costs. The system is designed so Layer N prevents Layer N+1 from firing whenever possible.

每一层由不同的条件触发，并有不同的成本。系统的设计使得第N层能够在其运行时阻止第N+1层触发。

[![Image 1: Image](./img_133a754d.jpg)](url)

[![Image 1: Image](./img_133a754d.jpg)](url)

*   File: src/utils/toolResultStorage.ts

*   文件：src/utils/toolResultStorage.ts

*   Cost: Disk I/O only — no API calls

*   成本：仅磁盘I/O——无API调用

*   When: Every tool result, immediately

*   时机：每个工具结果，立即执行

The Problem

问题

A single grep across a codebase can return 100KB+ of text. A cat of a large file might be 50KB. These results consume massive context and become stale within minutes as the conversation moves on.

对代码库的单次grep可能返回100KB+的文本。大文件的cat可能达到50KB。这些结果消耗大量上下文，并在几分钟内变得过时，因为对话会继续推进。

The Solution

解决方案

Every tool result passes through a budget system before entering context:

每个工具结果在进入上下文之前都要经过预算系统：

[![Image 2: Image](./img_292475fb.jpg)](url)

[![Image 2: Image](./img_292475fb.jpg)](url)

When a result exceeds its threshold:

当结果超出其阈值时：

1.   The full result is written to disk at tool-results/<sessionId>/<toolUseId>.txt

1. 完整结果被写入磁盘，路径为tool-results/<sessionId>/<toolUseId>.txt

2.   A preview (first ~2KB) is placed in context, wrapped in <persisted-output> tags

2. 一个预览（最初约2KB）被放入上下文，用<persisted-output>标签包裹

3.   The model can later use Read to access the full result if needed

3. 模型之后可以使用Read来访问完整结果（如有需要）

ContentReplacementState: Cache-Stable Decisions

ContentReplacementState：缓存稳定的决策

A critical subtlety: once a tool result is replaced with a preview, that decision is frozen in ContentReplacementState. On subsequent API calls, the same result gets the same preview — this ensures the prompt prefix remains byte-identical for prompt cache hits. This state even survives session resume by being persisted to the transcript.

一个关键的微妙之处：一旦工具结果被替换为预览，该决策就在ContentReplacementState中被冻结。在后续API调用中，相同的结果获得相同的预览——这确保了提示前缀对于提示缓存命中保持字节级一致。此状态甚至通过持久化到transcript中来在会话恢复中存活。

typescript

```typescript
ContentReplacementState = {
  seenIds: Set<string>,          // 已处理的结果（已冻结）
  replacements: Map<string, string>  // ID → 预览文本
}
```

```
ContentReplacementState = {
  seenIds: Set<string>,          // Results already processed (frozen)
  replacements: Map<string, string>  // ID → preview text
}
```

GrowthBook覆盖

GrowthBook Override

可通过tengu_satin_quoll功能标志远程调整每个工具的阈值——允许Anthropic在不进行代码部署的情况下调整特定工具的持久化阈值。

Per-tool thresholds can be remotely tuned via the tengu_satin_quoll feature flag — allowing Anthropic to adjust persistence thresholds for specific tools without a code deploy.

![Image 3](./img_0cd2c50e.jpg)

![Image 3](./img_0cd2c50e.jpg)

*   文件：src/services/compact/microCompact.ts

*   File: src/services/compact/microCompact.ts

*   成本：零到极低的API成本

*   Cost: Zero to minimal API cost

*   时机：每轮对话，API调用之前

*   When: Every turn, before the API call

微整合是最轻量级的上下文缓解。它不总结任何内容——只是清除不太可能需要的旧工具结果。

Microcompaction is the lightest-weight context relief. It doesn't summarize anything — it just clears old tool results that are unlikely to be needed.

三种不同机制

Three Distinct Mechanisms

a) 基于时间的微整合

a) Time-Based Microcompact

触发条件：自上次助手消息以来的空闲间隔超过阈值（默认值：60分钟）

Trigger: Idle gap since last assistant message exceeds threshold (default: 60 minutes)

原理：Anthropic的服务器端提示缓存约有1小时TTL。如果你一小时内没有发送请求，缓存已过期，整个提示前缀将从零开始重新token化。由于它无论如何都会被重写，因此先清除旧工具结果以减少被重写的内容。

Rationale: Anthropic's server-side prompt cache has a ~1 hour TTL. If you haven't sent a request in an hour, the cache has expired and the entire prompt prefix will be re-tokenized from scratch. Since it's being rewritten anyway, clear old tool results first to shrink what gets rewritten.

操作：用[旧工具结果内容已清除]替换工具结果内容，至少保留最近的N个结果（下限为1）。

Action: Replaces tool result content with [Old tool result content cleared], keeping at least the most recent N results (floor of 1).

配置（通过GrowthBook tengu_slate_heron）：

Configuration (via GrowthBook tengu_slate_heron):

```typescript
TimeBasedMCConfig = {
  enabled: false,           // 主开关
  gapThresholdMinutes: 60,  // 空闲1小时后触发
  keepRecent: 5             // 保留最后5个工具结果
}
```

typescript

b) 缓存微整合（缓存编辑API）

```
TimeBasedMCConfig = {
  enabled: false,           // Master switch
  gapThresholdMinutes: 60,  // Trigger after 1h idle
  keepRecent: 5             // Keep last 5 tool results
}
```

这是技术层面上最有趣的机制。它不是修改本地消息（这会使提示缓存失效），而是使用API的cache_edits机制从服务器端缓存中删除工具结果，而不使前缀失效。

b) Cached Microcompact (Cache-Editing API)

工作原理：

This is the most technically interesting mechanism. Instead of modifying local messages (which would invalidate the prompt cache), it uses the API's cache_edits mechanism to delete tool results from the server-side cache without invalidating the prefix.

1. 工具结果在出现时被注册到全局CachedMCState中

How it works:

2. 当计数超过阈值时，选择最旧的结果（减去"保留最近"的缓冲区）进行删除

1.   Tool results are registered in a global CachedMCState as they appear

3. 生成一个cache_edits块并与下一个API请求一起发送

2.   When the count exceeds a threshold, the oldest results (minus a "keep recent" buffer) are selected for deletion

4. 服务器从其缓存的前缀中删除指定的工具结果

3.   A cache_edits block is generated and sent alongside the next API request

5. 本地消息保持不变——删除仅发生在API层

4.   The server deletes the specified tool results from its cached prefix

关键安全特性：仅在主线程上运行。如果分叉的子代理（session_memory、agent_summary等）修改了全局状态，它们会损坏主线程的缓存编辑。

5.   Local messages remain unchanged — the deletion is API-layer only

c) API级上下文管理（apiMicrocompact.ts）

Critical safety: Only runs on the main thread. If forked subagents (session_memory, agent_summary, etc.) modified the global state, they'd corrupt the main thread's cache editing.

一种使用context_management API参数的新服务器端方法：

c) API-Level Context Management (apiMicrocompact.ts)

```typescript
ContextEditStrategy =
  | { type: 'clear_tool_uses_20250919',   // 清除旧工具结果
      trigger: { type: 'input_tokens', value: 180_000 },
      clear_at_least: { type: 'input_tokens', value: 140_000 } }
  | { type: 'clear_thinking_20251015',     // 清除旧思维块
      keep: { type: 'thinking_turns', value: 1 } | 'all' }
```

A newer server-side approach using the context_management API parameter:

这告诉API服务器原生处理上下文管理——客户端不需要跟踪或管理工具结果清除。

typescript

哪些工具可以整合？

```
ContextEditStrategy =
  | { type: 'clear_tool_uses_20250919',   // Clear old tool results
      trigger: { type: 'input_tokens', value: 180_000 },
      clear_at_least: { type: 'input_tokens', value: 140_000 } }
  | { type: 'clear_thinking_20251015',     // Clear old thinking blocks
      keep: { type: 'thinking_turns', value: 1 } | 'all' }
```

只有以下工具的结果会被清除：

This tells the API server to handle context management natively — the client doesn't need to track or manage tool result clearing.

FileRead、Bash/Shell、Grep、Glob、WebSearch、WebFetch、FileEdit、FileWrite

Which Tools Are Compactable?

值得注意的是：思维块、助手文本、用户消息、MCP工具结果不在此列。

Only results from these tools get cleared:

![Image 4](./img_1ce155b6.jpg)

FileRead, Bash/Shell, Grep, Glob, WebSearch, WebFetch, FileEdit, FileWrite

*   文件：src/services/SessionMemory/

Notably absent: thinking blocks, assistant text, user messages, MCP tool results.

*   成本：每次提取一次分叉代理API调用

![Image 4](./img_1ce155b6.jpg)

*   时机：对话期间定期执行（采样后钩子）

*   Files: src/services/SessionMemory/

理念

*   Cost: One forked agent API call per extraction

不要等到上下文满时再拼命总结所有内容，而是持续维护有关对话的笔记。然后当整合确实需要时，你已经准备好了摘要——无需昂贵的总结API调用。

*   When: Periodically during conversation (post-sampling hook)

会话记忆模板

The Idea

每个会话在~/.claude/projects/<slug>/.claude/session-memory/<sessionId>.md获得一个带结构化模板的markdown文件：

Instead of waiting until context is full and then desperately trying to summarize everything, continuously maintain notes about the conversation. Then when compaction IS needed, you already have a summary ready — no expensive summarization call required.

```typescript
# Session Title
_一个简短而独特的5-10词描述性标题_

Session Memory Template

# Current State
_当前正在积极处理什么？_

Each session gets a markdown file at ~/.claude/projects/<slug>/.claude/session-memory/<sessionId>.md with a structured template:

# Task specification
_用户要求构建什么？_

typescript

# Files and Functions
_重要文件及其相关性_

```
# Session Title
_A short and distinctive 5-10 word descriptive title_

# Workflow
_通常运行的Bash命令及其解释_

# Current State
_What is actively being worked on right now?_

# Errors & Corrections
_遇到的错误以及如何修复的_

# Task specification
_What did the user ask to build?_

# Codebase and System Documentation
_重要系统组件及其如何组合在一起_

# Files and Functions
_Important files and their relevance_

# Learnings
_什么效果好？什么不好？_

# Workflow
_Bash commands usually run and their interpretation_

# Key results
_如果用户要求特定输出，在此重复_

# Errors & Corrections
_Errors encountered and how they were fixed_

# Worklog
_逐步尝试和做了什么_
```

# Codebase and System Documentation
_Important system components and how they fit together_

触发逻辑

# Learnings
_What has worked well? What has not?_

会话记忆提取在两个条件同时满足时触发：

# Key results
_If the user asked for specific output, repeat it here_

自上次提取以来的token增长 ≥ 最小token数 且（自上次提取以来的工具调用数 ≥ 工具调用间隔 OR 最后一次助手回合中没有工具调用）

# Worklog
_Step by step, what was attempted and done_
```

token阈值始终是必需的——即使工具调用阈值已满足。"最后一次回合中没有工具调用"子句捕获了模型完成工作序列后的自然对话停顿。

Trigger Logic

提取执行

Session memory extraction fires when both conditions are met:

提取作为分叉子代理通过runForkedAgent()运行：

Token growth since last extraction ≥ minimumTokensBetweenUpdate AND (tool calls since last extraction ≥ toolCallsBetweenUpdates OR no tool calls in the last assistant turn)

*   querySource：'session_memory'

The token threshold is always required — even if the tool call threshold is met. The "no tool calls in last turn" clause captures natural conversation breaks where the model has finished a work sequence.

*   仅允许对记忆文件使用FileEdit（拒绝所有其他工具）

Extraction Execution

*   共享父级的提示缓存以节省成本

The extraction runs as a forked subagent via runForkedAgent():

*   通过sequential()包装器顺序运行以防止重叠提取

*   querySource: 'session_memory'

会话记忆整合：回报

*   Only allowed to use FileEdit on the memory file (all other tools denied)

当自动整合触发时，它首先尝试trySessionMemoryCompaction()：

*   Shares the parent's prompt cache for cost efficiency

1. 检查会话记忆是否有实际内容（不仅仅是空模板）

*   Runs sequentially (via sequential() wrapper) to prevent overlapping extractions

2. 使用会话记忆markdown作为整合摘要——无需API调用

Session Memory Compaction: The Payoff

3. 计算要保留的最近消息（从lastSummarizedMessageId向后扩展以满足最小值）

When autocompact triggers, it first tries trySessionMemoryCompaction():

4. 返回包含会话记忆作为摘要 + 保留的最近消息的CompactionResult

1.   Check if session memory has actual content (not just the empty template)

配置：

2.   Use the session memory markdown as the compaction summary — no API call needed

```
SessionMemoryCompactConfig = {
  minTokens: 10_000,          // 最少保留token数
  minTextBlockMessages: 5,     // 最少文本块消息数
  maxTokens: 40_000            // 保留token的硬上限
}
```

3.   Calculate which recent messages to keep (expanding backward from lastSummarizedMessageId to meet minimums)

关键洞察：会话记忆整合比完整整合便宜得多，因为摘要已经存在。没有总结器API调用，没有提示构建，没有输出token成本。会话记忆文件直接作为摘要注入。

4.   Return a CompactionResult with the session memory as summary + preserved recent messages

*   文件：src/services/compact/compact.ts

Configuration:

*   成本：一次完整API调用（输入 = 整个对话，输出 = 摘要）

```
SessionMemoryCompactConfig = {
  minTokens: 10_000,          // Minimum tokens to preserve
  minTextBlockMessages: 5,     // Minimum messages with text blocks
  maxTokens: 40_000            // Hard cap on preserved tokens
}
```

*   时机：上下文超过自动整合阈值且会话记忆整合不可用时

The key insight: Session memory compaction is dramatically cheaper than full compaction because the summary already exists. No summarizer API call, no prompt construction, no output token cost. The session memory file is simply injected as the summary.

触发条件

*   File: src/services/compact/compact.ts

有效上下文窗口 = 上下文窗口 - 20K（为输出预留）
自动整合阈值 = 有效窗口 - 13K（缓冲区）
如果tokenCountWithEstimation(messages) > 自动整合阈值 → 触发

*   Cost: One full API call (input = entire conversation, output = summary)

熔断器

*   When: Context exceeds autocompact threshold AND session memory compaction unavailable

连续3次失败后，自动整合在该会话剩余时间内停止尝试。这是在发现1279个会话各有50+次连续失败（单个会话最多3272次）后添加的，全球每天浪费约250K次API调用。

Trigger

整合算法

effective context window = context window - 20K (reserved for output) autocompact threshold = effective window - 13K (buffer) If tokenCountWithEstimation(messages) > autocompact threshold → trigger

第1步：预处理

Circuit Breaker

*   执行用户配置的PreCompact钩子

After 3 consecutive failures, autocompact stops trying for the rest of the session. This was added after discovering that 1,279 sessions had 50+ consecutive failures (up to 3,272 in a single session), wasting approximately 250K API calls per day globally.

*   从消息中剥离图片（替换为[image]标记）

The Compaction Algorithm

*   剥离技能发现/列表附件（将重新注入）

Step 1: Pre-processing

第2步：生成摘要

*   Execute user-configured PreCompact hooks

系统用一个详细的提示分叉一个总结器代理，请求9部分摘要：

*   Strip images from messages (replaced with [image] markers)

```
1. 主要请求和意图
2. 关键技术概念
3. 文件和代码部分（包含代码片段）
4. 错误和修复
5. 问题解决
6. 所有用户消息（逐字——对意图跟踪至关重要）
7. 待处理任务
8. 当前工作
9. 可选的的下一步
```

*   Strip skill discovery/listing attachments (will be re-injected)

该提示使用巧妙的两步输出结构：

Step 2: Generate Summary The system forks a summarizer agent with a detailed prompt requesting a 9-section summary:

*   首先：<analysis>块——模型组织思路的草稿区域

```
1. Primary Request and Intent
2. Key Technical Concepts
3. Files and Code Sections (with code snippets)
4. Errors and Fixes
5. Problem Solving
6. All User Messages (verbatim — critical for intent tracking)
7. Pending Tasks
8. Current Work
9. Optional Next Step
```

*   然后：<summary>块——实际的结构化摘要

The prompt uses a clever two-phase output structure:

*   <analysis>块在摘要进入上下文之前被剥离——它在不消耗整合后token的情况下提高了摘要质量

*   First: <analysis> block — a drafting scratchpad where the model organizes its thoughts

第3步：整合后恢复

*   Then: <summary> block — the actual structured summary

整合后，关键上下文被重新注入：

*   The <analysis> block is stripped before the summary enters context — it improves summary quality without consuming post-compact tokens

*   最近读取的5个文件（每个5K token，总预算50K）

Step 3: Post-compact Restoration

*   已调用的技能内容（每个5K token，总预算25K）

After compaction, critical context is re-injected:

*   计划附件（如处于计划模式）

*   Top 5 recently-read files (5K tokens each, 50K total budget)

*   延迟的工具模式、代理列表、MCP指令

*   Invoked skill content (5K tokens each, 25K total budget)

*   SessionStart钩子重新执行（恢复CLAUDE.md等）

*   Plan attachment (if in plan mode)

*   会话元数据重新追加以供--resume显示

*   Deferred tool schemas, agent listings, MCP instructions

第4步：边界消息

*   SessionStart hooks re-execute (restores CLAUDE.md, etc.)

一条SystemCompactBoundaryMessage标记整合点：

*   Session metadata re-appended for --resume display

```
compactMetadata = {
  type: 'auto' | 'manual',
  preCompactTokenCount: number,
  compactedMessageUuid: UUID,           // 边界前的最后一条消息
  preCompactDiscoveredTools: string[],  // 加载的延迟工具
  preservedSegment?: {                  // 仅会话记忆路径
    headUuid, anchorUuid, tailUuid
  }
}
```

Step 4: Boundary Message

部分整合

A SystemCompactBoundaryMessage marks the compaction point:

两个方向变体用于更精细的上下文管理：

```
compactMetadata = {
  type: 'auto' | 'manual',
  preCompactTokenCount: number,
  compactedMessageUuid: UUID,           // Last msg before boundary
  preCompactDiscoveredTools: string[],  // Loaded deferred tools
  preservedSegment?: {                  // Session memory path only
    headUuid, anchorUuid, tailUuid
  }
}
```

*   from方向：总结枢轴索引之后的消息，保持更早的消息完整。保留提示缓存因为保留的前缀未更改。

Partial Compaction

*   up_to方向：总结枢轴之前的消息，保持之后的消息。破坏缓存因为摘要更改了前缀。

Two directional variants for more surgical context management:

提示过长恢复

*   from direction: Summarize messages AFTER a pivot index, keep earlier ones intact. Preserves prompt cache because the kept prefix is unchanged.

如果整合请求本身遇到提示过长（对话太大甚至总结器无法处理）：

*   up_to direction: Summarize messages BEFORE pivot, keep later ones. Breaks cache because the summary changes the prefix.

1. 通过groupMessagesByApiRound()按API轮次对消息分组

Prompt-Too-Long Recovery

2. 删除最旧的组直到覆盖token差距（如果差距不可解析则删除20%的组）

If the compaction request itself hits prompt-too-long (the conversation is so large even the summarizer can't process it):

3. 重试最多3次

1.   Group messages by API round via groupMessagesByApiRound()

4. 如果所有重试都失败 → 抛出ERROR_MESSAGE_PROMPT_TOO_LONG

2.   Drop the oldest groups until the token gap is covered (or 20% of groups if gap is unparseable)

*   文件：src/services/extractMemories/extractMemories.ts

3.   Retry up to 3 times

*   成本：一次分叉代理API调用

4.   If all retries fail → ERROR_MESSAGE_PROMPT_TOO_LONG thrown

*   时机：每个完整查询循环结束时（模型生成最终响应且无工具调用时）

*   File: src/services/extractMemories/extractMemories.ts

目的

*   Cost: One forked agent API call

虽然会话记忆捕获当前会话的笔记，但自动记忆提取构建持久化的跨会话知识，存储在~/.claude/projects/<path>/memory/中。

*   When: End of each complete query loop (model produces final response with no tool calls)

记忆类型

Purpose

四种类型的记忆，每种都有特定的保存标准：

While Session Memory captures notes about the current session, Auto Memory Extraction builds durable, cross-session knowledge that persists in ~/.claude/projects/<path>/memory/.

[![Image 5: Image](./img_35dca476.jpg)](url)

Memory Types

记忆文件格式

Four types of memories, each with specific save criteria:

```markdown
---
name: testing-approach
description: 用户在生产事故后更喜欢集成测试而不是mock
type: feedback
---

[![Image 5: Image](./img_35dca476.jpg)](url)

集成测试必须使用真实数据库，而不是mock。

Memory File Format

**原因：** 之前的事故中mock/生产分歧掩盖了一个损坏的迁移。

markdown

**如何应用：** 为数据库代码编写测试时，始终使用测试数据库辅助工具。
```

```
---
name: testing-approach
description: User prefers integration tests over mocks after a prod incident
type: feedback
---

不要保存什么

Integration tests must hit a real database, not mocks.

提取提示明确排除：

**Why:** Prior incident where mock/prod divergence masked a broken migration.

*   代码模式、约定、架构（可从代码中推导）

**How to apply:** When writing tests for database code, always use the test database helper.
```

*   Git历史（使用git log/git blame）

What NOT to Save

*   调试解决方案（修复在代码中）

The extraction prompt explicitly excludes:

*   CLAUDE.md文件中的任何内容

*   Code patterns, conventions, architecture (derivable from code)

*   临时任务细节

*   Git history (use git log/git blame)

与主代理的互斥性

*   Debugging solutions (the fix is in the code)

如果主代理在当前回合已经写了记忆文件，则跳过提取。这防止后台代理复制主代理已经完成的工作：

*   Anything in CLAUDE.md files

```typescript
function hasMemoryWritesSince(messages, sinceUuid): boolean {
  // 扫描针对自动记忆路径的Edit/Write tool_use块
  // 如果主代理已经保存了记忆则返回true
}
```

*   Ephemeral task details

执行策略

Mutual Exclusivity with Main Agent

提取提示指示代理在其有限的回合预算内高效运作：

If the main agent already wrote memory files during the current turn, extraction is skipped. This prevents the background agent from duplicating work the main agent already did:

第1回合：并行发出所有可能更新的文件的FileRead调用
第2回合：并行发出所有FileWrite/FileEdit调用
不要在多个回合中交错读写。

function hasMemoryWritesSince(messages, sinceUuid): boolean { // Scans for Edit/Write tool_use blocks targeting auto-memory paths// Returns true if main agent already saved memories }

MEMORY.md：索引

Execution Strategy

MEMORY.md是一个索引文件，而不是记忆转储。每个条目应该是一行约150个字符以内：

The extraction prompt instructs the agent to be efficient with its limited turn budget:

- [Testing Approach](feedback_testing.md) — 真实数据库测试，prod事故后不用mock
- [User Profile](user_role.md) — 高级Go工程师，React新手，专注于可观测性

Turn 1: Issue all FileRead calls in parallel for files you might update Turn 2: Issue all FileWrite/FileEdit calls in parallel Do not interleave reads and writes across multiple turns.

硬性限制：200行或25KB——以先达到的为准。加载到系统提示中时，超出200行的行被截断。

MEMORY.md: The Index

![Image 6](./img_062e5094.jpg)

MEMORY.md is an index file, not a memory dump. Each entry should be one line under ~150 characters:

*   文件：src/services/autoDream/autoDream.ts

- [Testing Approach](feedback_testing.md) — Real DB tests only, no mocks after prod incident - [User Profile](user_role.md) — Senior Go eng, new to React, focused on observability

*   成本：一次分叉代理API调用（可能是多轮）

Hard limits: 200 lines or 25KB — whichever is hit first. Lines beyond 200 are truncated when loaded into the system prompt.

*   时机：积累足够时间和会话后，在后台执行

![Image 6](./img_062e5094.jpg)

概念

*   File: src/services/autoDream/autoDream.ts

梦境是跨会话记忆整合——一个后台进程，审查过去的会话记录并改进记忆目录。它类似于生物记忆在睡眠期间发生的整合：回顾一天的经历，组织，并整合到长期存储中。

*   Cost: One forked agent API call (potentially multi-turn)

门控序列（最便宜检查优先）

*   When: Background, after sufficient time and sessions have accumulated

梦境系统使用级联门控设计，每个检查都比下一个便宜，所以大多数回合提前退出：

The Concept

[![Image 7: Image](./img_07659775.jpg)](url)

Dreaming is cross-session memory consolidation — a background process that reviews past session transcripts and improves the memory directory. It's analogous to how biological memory consolidation happens during sleep: experiences from the day are reviewed, organized, and integrated into long-term storage.

锁机制

Gate Sequence (Cheapest Check First)

锁文件位于<memoryDir>/.consolidate-lock，起到双重作用：

The dream system uses a cascading gate design where each check is cheaper than the next, so most turns exit early:

路径：<autoMemPath>/.consolidate-lock
内容：进程PID（单行）
mtime：lastConsolidatedAt时间戳（锁本身就是时间戳）

[![Image 7: Image](./img_07659775.jpg)](url)

* 获取：写入PID → mtime = now。重新读取时验证PID（竞态保护）。

The Lock Mechanism

* 成功：mtime保持在now（标记整合时间）。

The lock file at <memoryDir>/.consolidate-lock serves double duty:

* 失败：rollbackConsolidationLock(priorMtime)通过utimes()回滚mtime。

Path: <autoMemPath>/.consolidate-lock Body: Process PID (single line) mtime: lastConsolidatedAt timestamp (the lock IS the timestamp)

* 陈旧：如果mtime > 60分钟且PID未运行 → 回收。

*   Acquire: Write PID → mtime = now. Verify PID on re-read (race protection).

* 崩溃恢复：检测到死PID → 下一个进程回收。

*   Success: mtime stays at now (marks consolidation time).

四阶段整合

*   Failure: rollbackConsolidationLock(priorMtime) rewinds mtime via utimes().

梦境代理收到一个结构化提示，定义四个阶段：

*   Stale: If mtime > 60 minutes old AND PID is not running → reclaim.

第1阶段——定向：

*   Crash recovery: Dead PID detected → next process reclaims.

* ls记忆目录

Four-Phase Consolidation

* 阅读MEMORY.md以了解当前索引

The dream agent receives a structured prompt defining four phases:

* 浏览现有主题文件以避免创建重复

Phase 1 — Orient:

第2阶段——收集近期信号：

*   ls the memory directory

* 如果存在则审查每日日志（logs/YYYY/MM/YYYY-MM-DD.md）

*   Read MEMORY.md to understand the current index

* 检查漂移的记忆（与当前代码库矛盾的事实）

*   Skim existing topic files to avoid creating duplicates

* 狭隘地搜索会话记录以获取特定上下文：
```bash
grep -rn "<狭隘术语>" transcripts/ --include="*.jsonl" | tail -50
```

Phase 2 — Gather Recent Signal:

* "不要穷尽阅读记录。只看你已经怀疑重要的东西。"

*   Review daily logs (logs/YYYY/MM/YYYY-MM-DD.md) if present

第3阶段——整合：

*   Check for drifted memories (facts that contradict current codebase)

* 写入或更新记忆文件

*   Grep session transcripts narrowly for specific context:grep -rn "<narrow term>" transcripts/ --include="*.jsonl" | tail -50

* 将新信号合并到现有主题文件而不是创建近似重复

*   "Don't exhaustively read transcripts. Look only for things you already suspect matter."

* 将相对日期转换为绝对日期（"昨天" → "2026-03-30"）

Phase 3 — Consolidate:

* 从源头上删除矛盾的事实

*   Write or update memory files

第4阶段——修剪和索引：

*   Merge new signal into existing topic files rather than creating near-duplicates

* 更新MEMORY.md以保持在200行/25KB以下

*   Convert relative dates to absolute ("yesterday" → "2026-03-30")

* 删除指向过时/错误/替代记忆的指针

*   Delete contradicted facts at the source

* 缩短冗长的索引条目（细节属于主题文件）

Phase 4 — Prune and Index:

* 解决文件间的矛盾

*   Update MEMORY.md to stay under 200 lines / 25KB

工具约束

*   Remove pointers to stale/wrong/superseded memories

梦境代理在严格限制下运作：

*   Shorten verbose index entries (detail belongs in topic files)

* Bash：仅允许只读命令（ls、find、grep、cat、stat、wc、head、tail）

*   Resolve contradictions between files

* Edit/Write：仅允许写入记忆目录路径

Tool Constraints

* 禁止MCP工具、Agent工具、破坏性操作

The dream agent operates under strict restrictions:

UI展示

*   Bash: Read-only commands only (ls, find, grep, cat, stat, wc, head, tail)

梦境作为后台任务出现在页脚药丸中，采用两阶段状态机：

*   Edit/Write: Only to memory directory paths

DreamPhase：'starting' → 'updating'（首次Edit/Write落地时）
Status：running → completed | failed | killed

*   No MCP tools, no Agent tool, no destructive operations

用户可以从后台任务对话框杀死梦境——锁mtime被回滚以便下次会话重试。

UI Surfacing

进度跟踪

Dreams appear as background tasks in the footer pill, with a two-phase state machine:

梦境代理的每个助手回合都被监视：

DreamPhase: 'starting' → 'updating' (when first Edit/Write lands) Status: running → completed | failed | killed

* 捕获文本块用于UI显示

Users can kill a dream from the background tasks dialog — the lock mtime is rolled back so the next session can retry.

* 计算tool_use块

Progress Tracking

* 收集用于完成摘要的Edit/Write文件路径

Each assistant turn from the dream agent is watched:

* 实时显示最多30个最近回合

*   Text blocks captured for UI display

*   文件：src/utils/forkedAgent.ts、src/tools/AgentTool/、src/tools/SendMessageTool/

*   Tool_use blocks counted

*   成本：因模式而异

*   Edit/Write file paths collected for the completion summary

*   时机：代理生成、后台任务、队友协调

*   Capped at 30 most recent turns for live display

分叉代理模式

*   Files: src/utils/forkedAgent.ts, src/tools/AgentTool/, src/tools/SendMessageTool/

Claude Code中几乎每个后台操作（会话记忆、自动记忆、梦境、整合、代理摘要）都使用分叉代理模式。这就是基础：

*   Cost: Varies by pattern

```typescript
CacheSafeParams = {
  systemPrompt: SystemPrompt,      // 必须与父级字节级相同
  userContext: { [k: string]: string },
  systemContext: { [k: string]: string },
  toolUseContext: ToolUseContext,   // 包含工具、模型、选项
  forkContextMessages: Message[],  // 父级的对话（缓存前缀）
}
```

*   When: Agent spawning, background tasks, teammate coordination

分叉创建一个具有克隆可变状态的隔离上下文：

The Forked Agent Pattern

*   readFileState：克隆的LRU缓存（防止交叉污染）

Nearly every background operation in Claude Code (session memory, auto memory, dreaming, compaction, agent summaries) uses the forked agent pattern. This is the foundation:

*   abortController：子控制器链接到父级

```
CacheSafeParams = {
  systemPrompt: SystemPrompt,      // Must be byte-identical to parent
  userContext: { [k: string]: string },
  systemContext: { [k: string]: string },
  toolUseContext: ToolUseContext,   // Contains tools, model, options
  forkContextMessages: Message[],  // Parent's conversation (cache prefix)
}
```

*   denialTracking：新的跟踪状态

The fork creates an isolated context with cloned mutable state:

*   ContentReplacementState：克隆（保留缓存稳定决策）

*   readFileState: Cloned LRU cache (prevents cross-contamination)

但通过保持相同的缓存关键参数来共享提示缓存。API看到相同的前缀并提供缓存命中。

*   abortController: Child controller linked to parent

Agent工具：生成分叉代理

*   denialTracking: Fresh tracking state

Agent工具支持多种生成模式：

*   ContentReplacementState: Cloned (preserves cache-stable decisions)

[![Image 8: Image](./img_12778fae.jpg)](url)

But it shares the prompt cache by keeping identical cache-critical parameters. The API sees the same prefix and serves a cache hit.

分叉防递归：分叉子代理在其工具池中保留Agent工具（以保持缓存相同的定义），但检测对话历史中的<fork_boilerplate_tag>以拒绝递归分叉尝试。

Agent Tool: Spawning Sub-Agents

用于缓存共享的分叉消息构造：

The Agent tool supports multiple spawning patterns:

所有分叉子代理生成字节级相同的API请求前缀：
1. 完整的父级助手消息（所有tool_use块、思维、文本）
2. 带有以下内容的单条用户消息：
   - 每个tool_use的相同占位符结果
   - 每个子代理的指令文本块（只有这个不同）
→ 跨并发分叉最大化提示缓存共享

[![Image 8: Image](./img_12778fae.jpg)](url)

SendMessage：代理间通信

Fork anti-recursion: Fork children keep the Agent tool in their tool pool (for cache-identical definitions) but detect the <fork_boilerplate_tag> in conversation history to reject recursive fork attempts.

SendMessage工具支持代理间的运行时通信：

Fork message construction for cache sharing:

```typescript
SendMessage({
  to: 'research-agent',  // 或'*'广播、'uds:<路径>'、'bridge:<id>'
  message: 'Check Section 5',
  summary: 'Requesting section review'
})
```

All fork children produce byte-identical API request prefixes: 1. Full parent assistant message (all tool_use blocks, thinking, text) 2. Single user message with: - Identical placeholder result for every tool_use - Per-child directive text block (only this differs) → Maximum prompt cache sharing across concurrent forks

路由逻辑：

SendMessage: Inter-Agent Communication

1. 按名称的进程内子代理 → queuePendingMessage() → 在下一个工具轮次边界耗尽

The SendMessage tool enables runtime communication between agents:

2. 环境团队（基于进程）→ writeToMailbox() → 基于文件的邮箱

SendMessage({ to: 'research-agent', // or '*' for broadcast, 'uds:<path>', 'bridge:<id>' message: 'Check Section 5', summary: 'Requesting section review' })

3. 跨会话 → 通过bridge/UDS的postInterClaudeMessage()

Routing logic:

用于生命周期控制的结构化消息：

1.   In-process subagent by name → queuePendingMessage() → drained at next tool round boundary

*   shutdown_request / shutdown_response — 优雅的代理关闭协调

2.   Ambient team (process-based) → writeToMailbox() → file-based mailbox

*   plan_approval_response — 领导批准/拒绝队友计划

3.   Cross-session → postInterClaudeMessage() via bridge/UDS

代理可以在三个范围内跨调用维护持久化记忆：

Structured messages for lifecycle control:

[![Image 9: Image](./img_09cdac1c.jpg)](url)

*   shutdown_request / shutdown_response — Graceful agent shutdown coordination

代理摘要：定期进度快照

*   plan_approval_response — Leader approves/rejects teammate plans

对于协调器模式的子代理，一个计时器每30秒分叉对话以生成3-5词的进度摘要：

Agents can maintain persistent memory across invocations in three scopes:

好："Reading runAgent.ts"
好："Fixing null check in validate.ts"
差："Investigating the issue"（太模糊）
差："Analyzed the branch diff"（过去式）

[![Image 9: Image](./img_09cdac1c.jpg)](url)

使用Haiku（最便宜的模型）并拒绝所有工具——这是一个纯文本生成任务。

Agent Summary: Periodic Progress Snapshots

![Image 10](./img_3731a0c8.jpg)

For coordinator-mode sub-agents, a timer forks the conversation every 30 seconds to generate a 3-5 word progress summary:

文件：src/query.ts

Good: "Reading runAgent.ts" Good: "Fixing null check in validate.ts" Bad: "Investigating the issue" (too vague) Bad: "Analyzed the branch diff" (past tense)

[![Image 11](./img_19ae7313.jpg)](url)

Uses Haiku (cheapest model) and denies all tools — it's a pure text generation task.

![Image 12](./img_11c0ced2.jpg)

![Image 10](./img_3731a0c8.jpg)

Claude Code架构中最复杂的方面之一是其痴迷的提示缓存优化。几乎每个设计决策都考虑缓存影响。

File: src/query.ts

Anthropic的API在服务器端缓存提示前缀（约1小时TTL）。缓存命中意味着你只需为新token付费。缓存未命中意味着重新token化整个提示。在200K token时，这就是每次请求约$0.003和约$0.60之间的差异。

[![Image 11: Image](./img_19ae7313.jpg)](url)

缓存保留模式

![Image 12](./img_11c0ced2.jpg)

1. CacheSafeParams：每个分叉代理（会话记忆、整合、梦境、提取）继承父级完全相同的系统提示、工具和消息前缀。分叉的API请求具有相同的前缀 → 缓存命中。

One of the most sophisticated aspects of Claude Code's architecture is its obsessive prompt cache optimization. Nearly every design decision considers cache impact.

2. renderedSystemPrompt：分叉线程化父级已经渲染的系统提示字节，避免渲染分歧（例如，GrowthBook标志值在渲染之间发生变化）。

Anthropic's API caches prompt prefixes server-side (~1 hour TTL). A cache hit means you only pay for new tokens. A cache miss means re-tokenizing the entire prompt. At 200K tokens, that's the difference between ~$0.003 and ~$0.60 per request.

3. ContentReplacementState克隆：工具结果持久化决策被冻结。相同的结果在每次API调用时获得相同的预览 → 稳定前缀。

Cache-Preserving Patterns

4. 缓存微整合：使用cache_edits修改服务器缓存而不更改本地前缀 → 无缓存中断。

1. CacheSafeParams: Every forked agent (session memory, compaction, dreaming, extraction) inherits the parent's exact system prompt, tools, and message prefix. The fork's API request has an identical prefix → cache hit.

5. 分叉消息构造：所有分叉子代理获得字节级相同的前缀。只有最终指令不同 → 跨并发分叉最大化缓存共享。

2. renderedSystemPrompt: The fork threads the parent's already-rendered system prompt bytes, avoiding re-rendering divergence (e.g., GrowthBook flag value changes between renders).

6. 整合后缓存中断通知：整合后，notifyCompaction()重置缓存基准，以便预期的整合后缓存未命中不会被标记为异常。

3. ContentReplacementState cloning: Tool result persistence decisions are frozen. The same results get the same previews on every API call → stable prefix.

系统通过promptCacheBreakDetection.ts主动监控意外缓存未命中，并将它们标记以便调查。已知的良好缓存中断（整合、微整合等）被预先注册以避免误报。

4. Cached microcompact: Uses cache_edits to modify the server cache without changing the local prefix → no cache break.

上下文阈值

5. Fork message construction: All fork children get byte-identical prefixes. Only the final directive differs → maximum cache sharing across concurrent forks.

[![Image 13: Image](./img_1b709e52.jpg)](url)

6. Post-compact cache break notification: After compaction, notifyCompaction() resets the cache baseline so the expected post-compact cache miss isn't flagged as an anomaly.

工具结果预算

The system actively monitors for unexpected cache misses via promptCacheBreakDetection.ts, flagging them for investigation. Known-good cache breaks (compaction, microcompact, etc.) are pre-registered to avoid false positives.

[![Image 14: Image](./img_1106a8c6.jpg)](url)

Context Thresholds

会话记忆

[![Image 13: Image](./img_1b709e52.jpg)](url)

[![Image 15: Image](./img_2fcc2fd2.jpg)](url)

Tool Result Budgets

整合

[![Image 14: Image](./img_1106a8c6.jpg)](url)

[![Image 16: Image](./img_0f9c177d.jpg)](url)

Session Memory

梦境

[![Image 15: Image](./img_2fcc2fd2.jpg)](url)

[![Image 17: Image](./img_2aa158ec.jpg)](url)

Compaction

微整合

[![Image 16: Image](./img_0f9c177d.jpg)](url)

[![Image 18: Image](./img_0db591a3.jpg)](url)

Dreaming

每个上下文管理层都被设计为阻止下一个更昂贵的层级触发：

[![Image 17: Image](./img_2aa158ec.jpg)](url)

* 工具结果存储防止微整合需要清除太多内容

Microcompact

* 微整合防止会话记忆整合

[![Image 18: Image](./img_0db591a3.jpg)](url)

* 会话记忆整合防止完整整合

Every context management layer is designed to prevent the next, more expensive layer from firing:

* 完整整合防止上下文溢出错误

*   Tool result storage prevents microcompact from needing to clear as much

几乎每个设计决策都考虑提示缓存影响。系统采取非凡措施保持API请求前缀字节级相同：冻结的ContentReplacementState、渲染的系统提示线程化、cache_edits API、相同的分叉消息构造。

*   Microcompact prevents session memory compaction

分叉代理获得克隆的可变状态（防止交叉污染）但共享提示缓存前缀（防止成本爆炸）。这是一个谨慎的平衡——太多的隔离浪费缓存，太多的共享导致bug。

*   Session memory compaction prevents full compaction

* 自动整合：3次失败限制

*   Full compaction prevents context overflow errors

* 梦境扫描：10分钟节流

Almost every design decision considers prompt cache impact. The system goes to extraordinary lengths to keep API request prefixes byte-identical: frozen ContentReplacementState, rendered system prompt threading, cache_edits API, identical fork message construction.

* 梦境锁：基于PID的互斥锁与陈旧检测

Forked agents get cloned mutable state (preventing cross-contamination) but share the prompt cache prefix (preventing cost explosion). This is a careful balance — too much isolation wastes cache, too much sharing causes bugs.

* 会话记忆：顺序执行包装器

*   Autocompact: 3-strike limit

* 提取记忆：与主代理写入的互斥性

*   Dream scan: 10-minute throttle

每个系统静默失败并让下一层处理。会话记忆整合失败返回null → 运行完整整合。梦境锁获取失败 → 下次会话重试。提取记忆错误 → 记录而非抛出。

*   Dream lock: PID-based mutex with stale detection

几乎每个系统都由GrowthBook功能标志控制：

*   Session memory: Sequential execution wrapper

*   tengu_session_memory — 会话记忆

*   Extract memories: Mutual exclusivity with main agent writes

*   tengu_sm_compact — 会话记忆整合

Each system fails silently and lets the next layer catch. Session memory compaction returns null on failure → full compaction runs. Dream lock acquisition fails → next session retries. Extract memories errors → logged, not thrown.

*   tengu_onyx_plover — 梦境

Nearly every system is gated by GrowthBook feature flags:

*   tengu_passport_quail — 自动记忆提取

*   tengu_session_memory — session memory

*   tengu_slate_heron — 基于时间的微整合

*   tengu_sm_compact — session memory compaction

*   CACHED_MICROCOMPACT — 缓存编辑微整合

*   tengu_onyx_plover — dreaming

*   CONTEXT_COLLAPSE — 上下文折叠

*   tengu_passport_quail — auto memory extraction

*   HISTORY_SNIP — 消息剪切

*   tengu_slate_heron — time-based microcompact

这允许在没有代码部署的情况下快速回滚任何有问题的系统。

*   CACHED_MICROCOMPACT — cache-editing microcompact

*   上下文折叠 ↔ 自动整合（折叠以自己的方式管理上下文）

*   CONTEXT_COLLAPSE — context collapse

*   主代理记忆写入 ↔ 后台提取（防止重复）

*   HISTORY_SNIP — message snipping

*   会话记忆整合 ↔ 完整整合（SM优先尝试，完整作为后备）

This allows rapid rollback without code deploys if any system causes problems.

*   自动整合 ↔ 子代理查询源（防止死锁）

*   Context Collapse ↔ Autocompact (collapse manages context its own way)

*   Main agent memory writes ↔ Background extraction (prevents duplication)

*   Session memory compaction ↔ Full compaction (SM tried first, full is fallback)

*   Autocompact ↔ Subagent query sources (prevents deadlocks)
