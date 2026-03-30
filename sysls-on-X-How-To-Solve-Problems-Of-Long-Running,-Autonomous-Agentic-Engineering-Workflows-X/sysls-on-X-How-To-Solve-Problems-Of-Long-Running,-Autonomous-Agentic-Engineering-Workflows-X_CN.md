---
title: "sysls on X: "How To Solve Problems Of Long Running, Autonomous Agentic Engineering Workflows" / X"
source: "https://x.com/systematicls/status/2038241033755168959?s=52&t=jjVOMAzDZNfuD4kcqctqJw"
saved_at: "2026-03-30"
tags: ["AI Agent", "X/Twitter"]
---

# sysls on X: "How To Solve Problems Of Long Running, Autonomous Agentic Engineering Workflows" / X

Title: sysls on X: "How To Solve Problems Of Long Running, Autonomous Agentic Engineering Workflows" / X

URL Source: https://x.com/systematicls/status/2038241033755168959?s=52&t=jjVOMAzDZNfuD4kcqctqJw

Markdown Content:
If you want to design a harness for really long-running autonomous systems, you should understand the following deeply.

At its core, all harness design is to overcome the problems of agents either becoming lazy and cutting corners or being confused and stupid.

, but a well written harness can go a long way.

Not gaining sufficient context before starting a task and therefore acting on wrong or missing information before it has begun. To overcome this, you need to systematically check for incomplete and/or contradictory information before starting on the task — because this will propagate once it starts.

This is the part where the agent is deciding on the attack vectors to solve the problem. The biggest problem here is choosing the wrong attack vectors, which results in implementing something entirely wrong.

Choosing a wrong attack vector because of stupidity rarely happens anymore, but choosing a wrong attack vector because of misalignment — misinterpreting what the user wants — is still pretty common.

To overcome this, you need to make sure that your agent is covering all related files before it has even started planning. An important part of this is ensuring that your repository contains no contradictory information.

Your agents don't live with the consequences of short-term, quick fix solutions. This is like hiring cheap software engineering labor, you may get something that works but it's going to result in a lot of tech debt.

The way to resolve this is to remind your agents at the "planning phase" to implement solutions that scale, that fit into the bigger picture, is easy to maintain, and respect good software engineering paradigms. Basically, you want your agents to think like a founder, not a part-time engineer.

You can get your agents to come up with N (e.g. N=5) different plans, have another agent pick the plan that will result in an implementation that is easier to maintain and scores higher on "clean-code principles".

This is the part where the agent is actually working on the problem. The biggest problem here is context exhaustion, by miles. Given a good plan and the right context, virtually all frontier model agents are able to complete sufficiently small tasks with close to one-shot capability now. Problems only arise when dealing with complex, multi-session problems that consume millions of tokens.

As I've written before, virtually all agents have some kind of context anxiety, and as a function of time, they become more and more desperate to end the session. This is extremely pervasive with Claude. To overcome this, you need to do smart session handoffs where you can relieve your agents of their context. You will then face a new problem — how to maximize context fidelity in your session handoffs.

You want to make sure that your handoff prompt contains sufficient detail so that the new agent in a new session can pick up everything it needs to continue the task in an information-dense way. Understand that what you are doing here is essentially a form of compaction — and the reason to believe you can do it better than native providers is that you have a better understanding of your repository structure than the foundation model providers do.

Other than context bloat, the second biggest problem is what I call planning stickiness. It is the risk where your agent deviates from the plan and essentially does whatever it wants. The most common expression of this is: you say do A, which is lengthy, painful, and sophisticated. Your agent does A', which it reasons is a reasonably close approximation to A, but which will not get you remotely close to your destination.

This is not only problematic as an outcome, but it is especially problematic when you realize that all software being composable often means that every downstream piece of code depending on A is now wired for A' instead — which means everything built from A' onwards is effectively wrong.

To solve this, you need to verify early and often that the solution to a task is implemented well and in accordance with your expectations. This will prevent cascading failures in your task list.

Agents have a deep fear of complexity. If you ask them to implement a 5-line function, no problem. If you make them believe they are going to have to write a 50,000-line class, they start to weasel their way out of it.

The worst offenses here are either writing stubs and calling it a day, or worse, declaring it out of scope for the session and ending it.

My best guess is that somewhere in the RL process, agents have learned that when working on highly complex tasks, they tend to get a lot of things wrong, are heavily penalized for it, and therefore aggressively avoid it.

Ironically, humans have this problem too. Most people imagine the gargantuan amount of work a project requires and procrastinate on it forever. Productivity coaches will tell you that the way to overcome this is to start with the simplest version of the task — the very first step. In this way the activation energy is nearly zero, and you immediately shift from "getting started" to "in progress."

It is similar for agents. You need to break a complex problem into many different sub-tasks that do not seem as daunting — where every task is a sub-hundred-line task, and you string 500 of them together.

An interesting side effect of having studied productivity methods and being a practitioner of them is realizing how effective they are at managing agents as well. It is very clear to me that agent psychology is created in our image.

Agents take the shortest path to verification. They will write weak tests, watch them pass, and use that as reason to declare success.

The more context pressure there is to "verify" work, the more atrocious this becomes. At its worst, suppose you have a function that does behavior A. The agent will write a test for behavior A', watch it pass, and declare that the function works.

The way to mitigate this is to ensure that the agent writing the verification tests is operating with as fresh a context as possible, and is a dedicated agent planning out the verification. It is then important that you are verifying the exact production-ready behavior you are looking for.

That means if you are testing whether a button on your front end works, do not test whether a generic button works. Think about what it would actually take to know the button works:

*   You need to see a screenshot confirming the button is actually there.

*   You need to actually simulate clicking the button.

*   The button needs to trigger something in your backend to deliver whatever payload it is supposed to deliver.

Until you can verify that something actually works — it doesn't. Trust me, I've worked with agents long enough to say this with confidence.

As it stands today, agents write barely acceptable code and do nothing to reduce the entropy in your repository. What happens is that they change function X to have behavior B instead of behavior A, but all documentation still references behavior A. Your agent is not going to fix that for you.

Repeat this 100 times and you end up with an unmaintainable repository where your agent is constantly confused and making poor decisions.

The best way to overcome this is to allocate tokens for an agent with a fresh context, after every long-running session, to clean up state, resolve contradictions, handle merge conflicts, remove dead code and stale documentation, and so on.

The tools available to solve the above problems within native harnesses — Claude Code, Codex, etc. — are very limited. Codex, for example, does not even have hooks.

More importantly, when you get Claude to act as the orchestrator in your harness, it becomes extremely bloated with orchestration context that is irrelevant to the actual task list at hand. You actually want your agent orchestration layer to exist on top of your task lists.

For example, you can have an agent whose sole job is ensuring that every session comes with an algorithmic contract that must be fulfilled before the session can end. This agent monitors the state of the contract, nudges agents toward contract stickiness, and spawns independent agents with fresh context to judge the quality of the work done and independently verify the "doneness" of the task.

By having your own independent harness, you have the ability to create custom workflows that directly address all the ways agents can be stupid.

Finding that your agents have a lot of complexity fear because of the nature of your work? Create an agent to classify whether the current prompt will result in a simple or high-complexity project. If high complexity, spawn another agent that breaks the project into as many bite-sized tasks as possible until the end outcome matches the original prompt.

Finding that your agents are not keeping your repository in a good state? At the end of every session, spawn agents that analyze the blast radius of your changes and ensure that everything your change touches is contradiction-free and clean — however you define clean.

Lastly, and most importantly — collect detailed telemetry on everything your agent orchestration layer takes in and produces (prompts, traces, outcomes) and come up with rubrics to judge the quality of your harness. Iteration is king, and this will allow you to inch toward better and better harnesses.

As a side-note: We've built an extremely opinionated harness that solves all of these problems in an opinionated fashion. We're really proud of it and it has become our daily driver in coding. We've also evolved it over many years of iteration and are going to open-source it once it's "public-use" ready.

For the vast majority of people, starting with a vanilla setup using native features will be good enough. But for those who need a lot more firepower from their agents, this article is designed to put into words all the problems you will likely face when using agents in long-running autonomous engineering projects.