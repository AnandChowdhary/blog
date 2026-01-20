---
date: 2025-01-20
draft: true
---

# The most radical programmer I've met doesn't use a laptop

A few months ago, I had a conversation that made me feel like I'd been doing Year of Agents wrong. Not in the "oops I didn't turn on /plan mode" way, but in the "oh no, I've fundamentally misunderstood who's leading this revolution" way.

I was chatting with a distinguished principal research engineer at \[big tech] - someone with multiple decades of experience at the company, deep in research, working on the future of agentic workflows. The kind of person you'd expect to have strong opinions about proper software architecture and maybe a slight disdain for anyone who doesn't understand monads.

I was thinking about an idea in the agent orchestration space and had recently built Continuous Claude, a way to run coding agents autonomously for large tasks by breaking them down into many pull requests, something now popularized as the Ralph loop. We were discussing our workflows when we told me that he hasn't touched his laptop in four months.

## The phone-only workflow

"I don't use an IDE anymore," he told me casually, like he was mentioning he'd switched to oat milk. "When you use an IDE and you're looking at tokens flying down the screen, it's like... you're watching a ginormous waste of time because you could have 10 agents running at the same time doing that work."

I must have made a face, because he continued: "Look at our codebase. I haven't written a single line of Go. And I think we have 300,000 lines of Go so far." He does everything from the GitHub Mobile app.

Here's his workflow: When he has an idea, he opens the GitHub app on his phone, creates an issue or assigns a task to Copilot agent, and waits. Twenty minutes later, he gets a notification - like "Instagram, but for code". A pull request appears, he reviews it, maybe leaves some comments, and either merges or requests changes. The agent iterates, he moves on to the next thing.

But that's not even the wild part.

He's built a fleet of GitHub Actions workflows that run every day. One looks for code duplication and cleans it up, another adds logging statements to files - five files a day, just steady improvement; while another monitors test coverage and suggests improvements. Another watches for dependency updates, reads the changelogs, and makes the necessary code changes (not just bumping versions like Dependabot, but actually updating the code to use new APIs).

Every morning, he wakes up to pull requests from coding agents that have been working while he slept. He reviews them over coffee. If a PR isn't perfect, he might just merge it anyway because he has another agent that runs daily to clean up sloppy code. "I can see the agent fucked up," he said, "but I still merge it because I now have unsloppers running daily and cleaning up that debt."

He calls this "daily ops" - the idea that your codebase should improve every single day through scheduled automation, like a newspaper delivery but for incremental code quality.

When he needs to design a new agent workflow, he doesn't sit at a computer. He puts on his headphones, opens ChatGPT voice mode, and goes to pick up his dog's poop (literally!). He has a conversation with ChatGPT while walking, refining the prompt through every turn, and by the time he's back, he has a ready-to-paste prompt for Copilot agent. The cognitive overhead of launching an IDE, finding the right file, and typing? Gone.

## The experience multiplier

Here's what broke my brain: this wasn't the person I expected to be living in the agentic future.

In my mental model, the people going full agent-mode were 17-year-old YC founders who don't know how to write code in a pre-LLM era. I did not expect a 50-something OG programming veteran with more than my lifespan in experience to be more radical than me. I've been building AI products for years, I built the tool for running Claude Code in automated loops, and I'm still opening Cursor every morning like some kind of dinosaur.

When I said as much to him, he laughed. "Senior devs, you would be surprised. The amount of principal and distinguished engineers here are going full agentic... We've been reviewing PRs our entire career. We've been training interns, new hires. When you're doing agentic, you're playing chess on 10 boards. You're just monitoring an army of interns. Most of the time you spend code reviewing. It's a muscle that a 17-year-old doesn't have."

And that's when it clicked.

The conventional wisdom is that AI coding tools help junior developers punch above their weight. Give a bootcamp grad Copilot and suddenly they can write production code! Democratization of coding! Everyone's a developer now!

The data tells a different story. [Fastly's research](https://www.fastly.com/blog/senior-developers-ship-more-ai-code) found that about a third of senior developers (10+ years of experience) say over half their shipped code is AI-generated - nearly 2.5x the rate of junior developers. Seniors are writing code [22% faster with AI tools](https://getdx.com/blog/ai-assisted-engineering-q4-impact-report-2025/), while juniors see only 4% improvement.

Why? Because AI coding isn't about generating code. It's about reviewing code. It's about knowing what to ask for. It's about recognizing when the output is wrong, which requires having seen enough right code to know the difference.

He said it perfectly: "The way we're going to teach CS is going to change. We're going to have to focus on fundamentals and actually on understanding. It's way harder to read someone's code and understand what the hell that thing is doing because you have to be able to run the program in your head. It's a much harder exercise."

He can't type two lines of Go without making ten typos - he doesn't have the muscle memory. But he's reviewed half a million lines of it. He can read that code efficiently. And in the agentic world, reading is the skill that matters.

Meanwhile, on the other end of the experience spectrum, things are getting grim for people just getting started. [Stanford research](https://www.cnn.com/2025/08/28/tech/computer-science-graduates-job-hunt-ai) found that employment among software developers aged 22 to 25 fell nearly 20% between 2022 and 2025. Salesforce announced they'd stop hiring new software engineers entirely.

As one senior engineer [put it](https://www.cio.com/article/3509174/ai-coding-assistants-wave-goodbye-to-junior-developers.html): "Why hire a junior for $90K when GitHub Copilot costs $10?"

The irony? Everyone thought AI would be the great equalizer - finally, anyone can code! Instead, it's becoming a force multiplier that makes experienced people exponentially more productive while making inexperienced people only marginally better. If you've been programming for several years, you get an army of AI interns. If you're just starting out, you get... a slightly smarter autocomplete that you don't know how to use properly.

I've been programming for over 15 years, and I feel the multiplier effect viscerally. I know what's right, what's wrong, and I know how to prompt these tools correctly because I've spent years in the AI space. I know how to give context, how to structure requests, how to evaluate outputs. With my background in design, I know how to go from slop to production-ready API and UI/UX design. The AI doesn't make me a better programmer - it makes my existing skills worth more.

## My own intervention

After that call, I felt embarrassed. Here I am, building AI products, writing about AI, literally creating tools for autonomous coding - and I'm still manually typing in Cursor like it's 2023. Don't get me wrong: I was using Claude Code aggressively, just not totally.

So I gave myself a challenge: starting in October, I would not write code manually. (Almost) everything goes through a coding agent.

And here's the thing: it worked.

It's now January, and nothing has changed. I'm still using a coding agent as my primary way of interacting with code. I built out Continuous Claude properly - it topped Hacker News and hit 1k+ stars on GitHub. I've been running it overnight and waking up to pull requests, just like that engineer described. Hundreds of commits, high signal-to-noise ratio, steady improvement while I sleep.

The mental shift was harder than the technical shift. The tools were already there. What I had to overcome was the identity attachment and start a new way to building. But talking to him helped me reframe it: I've been promoted from individual contributor to engineering manager, except my reports are AI agents who work 24/7 and never complain about the coffee.

The best advice he gave me was this: "Just close your laptop for a week. Code on your phone. Because it's actually a forcing function. Anything I want to do that's not well supported, yeah, I need to write an agent for it. So I can't cheat."

When you can't open Cursor, you're forced to think differently. You can't fall back on muscle memory. You have to express your intent clearly enough that an agent can execute it. And in doing so, you discover just how much of "coding" was actually just typing - mechanical translation of ideas you already had into syntax you already knew.

The ideas were always the hard part. The typing was busywork we convinced ourselves was valuable because it felt like work.

## What this actually means

I don't think every programmer needs to throw away their laptop. This guy was operating at a certain scale and seniority where his time was best spent on architecture and review. Most of us still need to understand code at a visceral level, and writing it is part of how we learn.

But I do think the direction is clear. IDEs as we know them are on the way out. The future is agent orchestration - spinning up multiple AI workers, reviewing their output, providing feedback, and maintaining the quality bar across a fleet of automated contributors.

The people who will thrive are the ones who can:
1. Express intent clearly (prompting is the new programming)
2. Review code efficiently (reading > writing)
3. Design systems that can be improved incrementally by agents
4. Think in workflows, not keystrokes

The person I spoke to has been a top performer because he keeps reinventing himself. "If I wouldn't do this kind of stuff," he told me, "I would not survive 20+ years here."

That's the real lesson. Not that we should all code from our phones (though, honestly, maybe we should try it). But that the most successful technologists are the ones who recognize paradigm shifts early and adapt, even when it means abandoning skills they spent decades developing.

The most radical programmer I've met doesn't write code. He reviews it, orchestrates it, and improves it in his sleep. And he's been doing this longer than some of his colleagues have been alive.

Maybe it's time the rest of us caught up.
