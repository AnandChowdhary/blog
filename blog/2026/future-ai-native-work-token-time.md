---
date: 2026-05-28
draft: true
---

# Token time

A friend asked me this week what AI-native development actually feels like now.

I think my answer would have sounded absurd to me even a year ago: I spend a lot less time writing code, I spend a lot less time reviewing code line by line, and I feel more responsible for the software than before.

That last part is the important one.

The lazy version of the AI coding story is that engineers stop caring and let models spray code into production. That is not what is happening in the best teams. The job has not disappeared. It has moved up a level.

At FirstQuadrant, I lived in the world of tab autocomplete. I was one of those people who tried to squeeze every possible ounce out of Cursor. I even got a little badge from them for being in the top 5% of tab users, which is a very funny thing to be proud of and also, apparently, something I am still proud of.

That world was still recognizably software engineering. I had the codebase in my head. We had about 200,000 lines of code after two and a half years of building. I knew where everything was. If something broke, I could usually imagine the path from the frontend event to the database write without opening the repo.

Now, at Sycamore, the scale feels different. A small team can produce in a couple of weeks what used to take years. People have multiple coding agents running in parallel. You walk into the office and see someone with a monitor split between Codex, Claude Code, review agents, logs, terminals, and docs. While I was on this call, I had three agents running in the background. Two were stuck in review loops, which meant I knew they would not need me for a while.

This changes the unit of work.

In the old world, engineering time and human time were basically the same thing. If I said I wanted to spend 20% of my time on observability, that meant roughly one day a week. Monday to Friday, somewhere in there, I would give observability a day of my attention.

That sentence means something else now.

If I have five agents running, 20% of my token time can go to observability while 99% of my human time stays on new product work. One agent can spend the week crawling through the codebase, adding instrumentation, writing tests, opening PRs, and going through reviews. My job is not to personally type every log line. My job is to make sure the agent has the right spec, the right context, the right constraints, and the right definition of done.

That is the first new concept I keep coming back to: token time.

## The spec is where the coding moved

When I was writing most of the code myself, I discovered edge cases while building. I would start with a rough idea, write the first version, hit a weird state, adjust the abstraction, notice the UI needed another empty state, change the API, then keep going. The thinking and the typing were tangled together.

With agents, that stops working.

If you give an agent a vague spec, it will happily produce a precise implementation of your vague thinking. That is worse than doing nothing because it looks like progress. The PR exists. The tests may even pass. But the shape is wrong.

So the work moves earlier. You spend real time with the model before implementation. You ask it to attack the spec. You ask it to find missing states. You ask it to list every edge case. You ask it to compare approaches. You make the hidden assumptions visible. By the time the coding agent starts, the spec should feel almost boring.

That boredom is the point.

A good spec becomes a contract. If the model implements it perfectly, the result should be right. If the result is wrong, the failure is often in the spec, not in the typing.

This is the part that still feels unintuitive to a lot of very good engineers. They are used to carrying architectural responsibility through direct contact with the code. They want to touch every line because they know they will be on the hook later.

I get that. I felt that.

But I have changed my mind. The models are good enough now, especially inside a good harness, that the bottleneck is less often "can it write code?" and more often "did we explain the work well enough, and did we build the rails around it?"

## Reviewing the reviewer bots

The strangest sentence I said on the call was: we review the reviewer bots.

At some point, reviewing every line stops being a serious plan. If the output volume is high enough, human line-by-line review becomes theater. You pretend you looked carefully. You catch the obvious thing. You miss the important thing because your brain was not designed to diff thousands of model-generated lines every day.

So we changed the loop.

A coding agent opens a draft PR. Multiple review agents review it. Different models have different personalities, which is weird but very real. One is pedantic about types. One is better at security. One is annoyingly good at noticing product inconsistencies. They leave comments. The coding agent decides what to accept, makes changes, and triggers the reviewers again. This repeats until the PR is clean.

Then the human reviews the system, not just the diff.

Did the agent understand the spec? Did the tests cover the behavior we care about? Did the review agents disagree on anything important? Did the implementation preserve the architecture? Are there logs, migrations, permissions, audit trails, and failure states? Is this something I can explain tomorrow without pretending I wrote it myself?

That last question matters a lot.

The future engineer is not someone who says, "I wrote every line." That is increasingly false, or at least not the highest-leverage claim. But the future engineer also cannot say, "The agent wrote it, I have no idea how it works." Instant rejection.

The bar is thinner and harder: I did not type every line, but I can explain every important decision.

## Tests got weirder and better

Unit tests are now cheap enough that you might as well generate them for everything. I am less emotionally attached to them than I used to be. A lot of unit tests are just regression fences around current behavior. That is useful, but it is not where the real confidence comes from.

The fun part is end-to-end testing.

Agents can run the app. They can open the browser, click around, submit forms, watch animations, hit APIs, inspect logs, and attach an MP4 to a PR when the UI changes. They can run the whole stack locally and verify that a button in React causes the right backend event and the right frontend state change.

This is much closer to how users experience software.

We also have agents running overnight against dev environments. They create accounts, type prompts, click through workflows, and file issues when something breaks. Every morning, there is usually something. Sometimes it is a real bug. Sometimes it is a flaky assumption. Sometimes it is a product detail that nobody wrote down but everyone sort of expected.

In the old world, you might have hired QA for this. In this world, dedicated QA as a separate function feels less obvious. The human still decides what matters, what is acceptable, and what should be fixed. But the repetitive exploration can run while everyone sleeps.

This is where the "agents working overnight" phrase becomes real instead of a demo trick. It is not magic. It is a loop: act, observe, file, fix, review, repeat.

## Context is now infrastructure

The thing I underestimated earlier was how much of AI-native work is just knowledge management with higher stakes.

We have skills in the monorepo that agents can read before doing specific work. We have standard libraries for common patterns so agents do not reinvent authentication, reviews, permissions, or other load-bearing pieces every time. We commit architectural notes, decision records, product reasoning, and technical docs next to the code.

The repo is not just code anymore. It is the working memory of the company.

Meetings matter here too. My current feeling is pretty extreme: if it was not recorded, it did not happen. That sounds harsh, but it is practical. If an architectural decision happened in a meeting and the agent cannot find it later, the decision may as well be folklore.

So meeting transcripts, summaries, technical discussions, customer context, and planning notes get indexed and pushed somewhere agents can use them. When an agent asks, "Why does RBAC work this way?" the answer should not live in one person's head or in a Slack thread from three months ago. It should be findable.

This is why I think the context problem is more solved than people assume. Not perfectly solved. But the frontier models are surprisingly good at finding the needle if you actually give them the haystack in a form they can search.

Bad context still creates bad work. But lack of context is increasingly an organizational choice, not a model limitation.

## Technical debt changed shape

I used to think of technical debt as something you accumulate because fixing it is expensive. You make the tradeoff knowingly. Then six months later, the interest comes due and everyone acts surprised.

In an AI-native codebase, some of that changes. If a bug is cheap to find, cheap to fix, cheap to test, and cheap to review, then the half-life of certain kinds of debt gets much shorter. You can have agents that look at today's commits overnight, identify messy patterns, and open cleanup PRs before the mess becomes sediment.

That does not mean debt disappears. It moves.

Bad abstractions are still expensive. Bad specs are expensive. Bad tests are expensive. Bad context is very expensive. If your rails are weak, agents do not save you. They help you create a larger mess faster.

This matches what the [2025 DORA report](https://dora.dev/dora-report-2025/) says in a more general way: AI amplifies the organization. It does not fix the organization. Strong engineering systems get stronger. Confused systems get more confused, just with more output.

So I am less worried about every imperfect line of code and more worried about whether the system can notice, correct, and learn. A self-improving codebase is not one where the model writes perfect code. It is one where the loops are good enough that imperfection does not sit still for long.

## The calendar changed too

I used to prefer batching meetings together. Put all the calls in one block, then protect a long stretch for deep work.

Now I want gaps.

A 30-minute break between meetings is enough time to read where an agent got stuck, sharpen the next prompt, approve a direction, write a better spec, or kick off the next task. Then I can go back into meetings while the work continues. The break is not dead time. It is the handoff.

This is new for me as a manager too. When I failed to protect enough IC time, I did not just lose my own output. I lost the output of the agents I would have been managing. One missing engineer is not one missing pair of hands anymore. It can be five missing agent sessions running all day.

That sounds cold, but it has made me happier. I am doing more real product work again because the unit of contribution is not "how many uninterrupted hours did I personally type?" It is "how much useful work did I set in motion, and did I keep enough judgment in the loop?"

Context switching becomes a serious skill here. In one hour, I may jump between a UI task, a platform change, an enterprise customer deck, and an observability rollout. These used to be different human jobs. Now they can be different agent sessions, and the human skill is quickly reconstructing enough context to make the next good decision.

Founders may have an unfair advantage here because founder work is already context-switching chaos. Sales call, investor update, bug, hiring, customer escalation, product decision. The AI-native version just adds more parallel threads.

## Hiring for this is strange

This is one of the hardest parts.

When we evaluate people, both extremes are bad.

If someone says, "I wrote all the code myself, do not worry," that is not the flex it used to be. It may mean they have not learned the new leverage.

If someone says, "The agent wrote it and I cannot explain it," that is worse. It means they have outsourced judgment.

The person you want is somewhere in the middle. They can run multiple sessions. They can use agents aggressively without becoming passive. They can defend architectural decisions. They can read a transcript, understand where the work is, and redirect it. They have taste. They know when the model is being clever in the wrong direction.

This is a weird profile. It is not just "prompt engineer" and it is not just "senior software engineer" with a new tool. It is closer to engineering manager, tech lead, product thinker, and systems designer compressed into one person, even for IC work.

That is why hiring feels harder, not easier.

The tools make output easier. They make judgment more valuable.

## AI-native is not a tool choice

There is a version of this conversation where someone asks, "Should we use Codex or Claude Code or Copilot?" Those are reasonable questions. [OpenAI Codex CLI](https://developers.openai.com/codex/cli) can read, change, and run code locally. [Claude Code](https://www.anthropic.com/news/enabling-claude-code-to-work-more-autonomously) keeps getting more autonomous. [GitHub Copilot's coding agent](https://github.blog/news-insights/product-news/github-copilot-meet-the-new-coding-agent/) can take issues and open draft PRs.

But the tool choice is not the transformation.

The transformation is building the factory around the tools. Specs. Skills. Review loops. End-to-end tests. Sandboxes. Security scans. Compliance gates. Documentation. Meeting memory. Standard libraries. Human approval at the right level of abstraction.

That is what enterprises are actually asking for when they ask how to become AI-native. They are not asking for a chatbot in the IDE. They are asking how to change the way work moves through the company without losing trust.

This is especially obvious in enterprise environments. The bar is not "can an agent build the feature?" The bar is "can an agent build the feature while preserving governance, auditability, security, compliance, and the parts of institutional knowledge that are usually trapped in people's heads?"

That is a much more interesting problem.

## The uncomfortable part

I do not want to pretend this transition is emotionally easy.

A lot of people are worried, and they are not wrong to be worried. The job is changing quickly. Skills that made someone excellent five years ago are becoming less central. Some people feel like the ground is moving under them because it is.

I also think refusing to adapt is the wrong response.

The code is no longer the scarce thing. The scarce things are judgment, taste, context, trust, and the ability to design loops that improve without constant supervision.

That is a very different kind of work. It is still work. It might be more work in some ways, because you are responsible for more surface area with less direct contact. You have to be comfortable saying, "I did not write this, but I own it."

I keep thinking about that sentence.

It may be the core of AI-native work.

## Where I land

After FirstQuadrant, I thought I knew AI-assisted development. I did not. Tab autocomplete was not the destination. It was the bridge.

The next phase is not about autocomplete. It is not even about one agent doing one task. It is about parallel systems of agents working inside rails that humans design, maintain, and inspect. It is about separating human time from token time. It is about moving engineering from typing and line review toward specification, orchestration, verification, and taste.

The best teams will not be the ones that generate the most code. They will be the ones that build the best loops.

Loops for planning. Loops for review. Loops for testing. Loops for cleanup. Loops for memory. Loops for compliance. Loops that let the company move faster without pretending trust no longer matters.

I am still early in this. We all are. But the feeling is unmistakable: the future of work is not fewer humans caring about the work.

It is humans caring at a different layer.
