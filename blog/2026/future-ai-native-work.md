# The future of AI-native work

I had a chance to reflect at the past half year we've been building the team and culture at [Sycamore](https://sycamore.so) after a friend asked me what AI-native development actually feels like these days.

I think my answer would have sounded absurd to me even a year ago: I spend a lot less time writing code, I spend a lot less time reviewing code line-by-line, and I feel more responsible for the software.

The lazy version of the AI coding story is that engineers stopped caring and let models spray slop into production. I don't think this is what's happening in the best teams.

## Token time

At [FirstQuadrant](/projects/tags/firstquadrant), I lived in the world of tab autocomplete. I was one of those people who tried to squeeze every possible ounce out of Cursor. I even got a little Tab key from them for being in the top 5% of tab users, which is a pretty funny thing to be proud of and also, apparently, something I am still proud of. But this was the world of 2023.

That world was still recognizably software engineering. I had the codebase in my head. We had about 200,000 lines of code after two and a half years of building and rebuilding. I knew where everything was. If something broke, I could usually imagine the path from the frontend event to the database write without opening the repo.

Now, at Sycamore, the scale feels different. A small team can produce in a couple of weeks what used to take literal years. You walk into the office and see someone with a monitor split between Codex, Claude Code, review agents, logs, terminals, and docs. While I was on this call sharing these details with my friend, I had three agents running in the background. Two were stuck in review loops, which meant I knew they would not need me for a while.

This changes the unit of work.

In the old world, engineering time and human time were basically the same thing. Sri said he wanted the team to spend 20% of our time on observability, that meant roughly one day a week. Monday to Friday, somewhere in there, I would give observability a day of my attention.

That sentence means something else now. Now, he said, we want to spend 20% of our token time.

If I have five agents running, 20% of my token time can go to observability while 99% of my human time stays on new product work. One agent can spend the week crawling through the codebase, adding instrumentation, writing tests, opening PRs, and going through reviews. My job is not to personally type every log line. My job is to make sure the agent has the right spec, the right context, the right constraints, and the right definition of done.

That is the first new concept I keep coming back to: token time.

## The spec is where the coding moved

When I was writing most of the code myself, I discovered edge cases while building. I would start with a rough idea, write the first version, hit a weird state, adjust the abstraction, notice the UI needed another empty state, change the API, then keep going. The thinking and the typing were tangled together.

With agents, that stops working.

If you give an agent a vague spec, it will happily produce a precise implementation of your vague thinking. That is worse than doing nothing because it looks like progress. The PR exists, the tests may even pass, but the shape will be wrong.

So the work moves earlier. You spend real time with the model before implementation. You ask it to attack the spec, you ask it to find missing states, to list every edge case, compare approaches, self-grill. You make the hidden assumptions visible.

A good spec becomes a contract. If the model implements it perfectly, the result should be right.

This is the part that still feels unintuitive to a lot of very good engineers. They are used to carrying architectural responsibility through direct contact with the code. They want to touch every line because they know they will be on the hook later.

I get that. I felt that.

But I have changed my mind. The models are good enough now, especially inside a good harness, that the bottleneck is less often "can it write better code that I can?" (hint: yes) and more often "did I explain the work well enough, and did I build the right guardrails around it?"

## Reviewing the reviewer bots

At some point, reviewing every line stops being a serious plan. If the output volume is high enough, human line-by-line review becomes theater. You pretend you looked carefully while catching the obvious thing and missing the important thing because your brain was not designed to diff thousands of model-generated lines every day.

So we changed the loop.

A coding agent opens a draft PR, and multiple review agents review it. Different models have different personalities, which is weird but very real. One is pedantic about types, the other is better at security, while a third is annoyingly good at noticing product inconsistencies. They leave comments, and the coding agent decides what to accept, making the changes and triggering the reviewers again. This repeats until the PR is clean.

Then the human reviews the system, but maybe not the diff. Did the agent understand the spec? Did the tests cover the behavior we care about? Did the review agents disagree on anything important? Did the implementation preserve the architecture? Are there logs, migrations, permissions, audit trails, and failure states? Is this something I can explain tomorrow?

This is also very interesting while hiring. The kind of engineer I want to hire now is not someone who says "I wrote every line" (increasingly false) but they also cannot say "the agent wrote it, I have no idea how it works" (instant rejection).

The bar is thinner and harder: I did not type every line, but I can explain every important decision and take ownership for the output.

## Tests got weirder and better

Unit tests are now cheap enough that you might as well generate them for everything. I am less emotionally attached to them than I used to be, because lot of unit tests are just regression fences around current behavior. That is potentially useful, but it is not where the real confidence comes from.

The fun part is end-to-end and integration testing.

In 2026, agents can run the app. They can open the browser, click around, submit forms, watch animations, hit APIs, inspect logs, and attach an MP4 to a PR when the UI changes. They can run the whole stack locally and verify that a button in React causes the right backend event and the right frontend state change.

This is much closer to how users experience software.

We also have agents running overnight against dev environments. They create accounts, type prompts, click through workflows, and file issues when something breaks. Every morning, we find out if there's something broken. Sometimes it is a real bug, and sometimes it is a flaky assumption. But sometimes, it is a product detail that nobody wrote down but everyone sort of expected.

In the old world, you might have hired QA for this. In the new, dedicated QA as a separate function feels less obvious. The human still decides what matters, what is acceptable, and what should be fixed. But the repetitive exploration can run while everyone sleeps.

This is where the "agents working overnight" phrase becomes real instead of a demo trick. Not magic, a loop: act, observe, file, fix, review, repeat.

## Context is now infrastructure

The thing I underestimated earlier was how much of AI-native work is just knowledge management.

We have skills in the monorepo that agents can read before doing specific work. We have standard libraries for common patterns so agents do not reinvent authentication, reviews, permissions, or other load-bearing pieces every time. We commit architectural notes, decision records, product reasoning, technical docs, and even meeting transcriptions next to the code.

The repo is the working memory of the company.

My current feeling about that last one is pretty extreme: if a meeting was not recorded, it did not happen. If an architectural decision happened in a meeting and the agent cannot find it later, the decision may as well be folklore.

This is why I think the context problem is more solved than people assume. Maybe it's not perfectly solved yet, but the frontier models and harnesses are surprisingly good at finding the needle if you actually give them the haystack in a form they can search.

Bad context still creates bad work, sure, but lack of context is far worse when auto-compaction and subagents are so good.

## Technical debt changed shape

Another thing I used to think is that technical debt is something you accumulate because fixing it is expensive. You make the tradeoff knowingly, and then six months later the interest comes due.

In an AI-native codebase, some of that changes. If a bug is cheap to find, cheap to fix, cheap to test, and cheap to review, then the half-life of certain kinds of debt gets much shorter. You can have agents that look at all of today's commits overnight, identify messy patterns, and open cleanup PRs before the mess becomes sediment.

Bad abstractions, specs, or tests are still expensive. If your rails are weak, agents do not save you. If anything, they help you create a larger mess faster. This matches what the [2025 DORA report](https://dora.dev/dora-report-2025/) says in a more general way: AI amplifies the organization. Strong engineering systems get stronger, confused systems get more confused.

So I am less worried about every imperfect line of code and more worried about whether the system can notice, correct, and learn. A self-improving codebase is one where the loops are good enough that imperfection does not sit still for long.

## The calendar changed too

I used to prefer batching meetings together. Put all the calls in one block, then protect a long stretch for deep work.

Now I want gaps.

A 30-minute break between meetings is enough time to read where an agent got stuck and sharpen the next steer. Then I can go back into meetings while the work continues.

This is new for me as a manager too. When I failed to protect enough IC time, I lost more than my own output; I lost output of the agents I would have been managing. One missing engineer is not one missing pair of hands anymore, it can be five missing agent sessions running all day.

That sounds cold, but it has made me happier. I am doing more real product work again because the unit of contribution went from "how many uninterrupted hours did I personally type?" to "how much useful work did I set in motion, and did I keep enough judgment in the loop?"

Context switching becomes a serious skill here. In one hour, I may jump between a UI task, a platform change, an enterprise customer deck, and an observability rollout. These used to be different human jobs. Now they can be different agent sessions, and the human skill is quickly reconstructing enough context to make the next good decision.

Founders may have an unfair advantage here because founder work is already context-switching chaos. Sales call, investor update, bug, hiring, customer escalation, product decision. The AI-native version just adds more parallel threads, which is why _Former founder_ is one of the most-chased roles top companies are hiring for these days.

## Hiring for this is strange

When we evaluate people, both extremes are bad.

If someone says, "I wrote all the code myself, do not worry", that is not the flex it used to be as it may mean they have not learned the new leverage.

If someone says, "The agent wrote it and I cannot explain it", that is worse as it means they have outsourced judgment.

The person you want is somewhere in the middle. They can run multiple sessions and use agents aggressively without becoming passive, while being able to defend architectural decisions. They have taste.

This is a weird profile. Less senior IS and more engineering manager (of agents)/tech lead/product thinker/systems designer compressed into one person.

This is why finding the best people seems harder. The tools make the output easier and judgment more valuable.

## The transition period

I do not want to pretend this transition is emotionally easy for everyone.

A lot of people are worried, and they are not wrong to be worried. The job is changing quickly, and skills that made someone excellent five years ago are becoming less central. Some people feel like the ground is moving under them... but it is.

Refusing to adapt is the wrong response. The code is no longer the scarce thing. We need people with the right judgment, taste, context, trust, and the ability to design loops that improve without constant supervision.

That is a very different kind of work. It is still work; it might even be more work in some ways (I'm working harder than I ever have) because you are responsible for more surface area with less direct contact. You have to be comfortable saying, "I did not write this, but I own it".

I find myself thinking about that sentence; it may be the core of AI-native work. I did not write this, but I own it.

## The future

After FirstQuadrant, I thought I knew what AI-assisted development looks like with my shiny Cursor tab key... but now I think that the next stage is about parallel systems of agents working inside rails that humans design, maintain, and inspect.

We need to separare human time from token time and move engineering from coding and even code review toward specification, orchestration, verification, and taste.

The best teams will clearly not be the ones that generate the most code fastest (move fast!), they'll be the ones that build the best loops for planning, review, testing, cleanup, memory, compliance... loops that let the company move faster without pretending trust no longer matters.

I am still early in this... we all are. But the feeling is unmistakable: the future of work is humans caring at a different layer of work.
