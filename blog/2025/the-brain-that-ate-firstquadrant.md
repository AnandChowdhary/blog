---
date: 2025-12-01
draft: true
---

# The brain that ate FirstQuadrant

This is the fifth and final chapter in my five-year retrospective. After [building the first AI SDR](/blog/2025/building-the-first-as-sdr) and fighting Gmail's spam filters to reach $20k MRR, we discovered our real product wasn't email automation at all - it was an AI reasoning engine we called the Brain. This is the story of how we only found idea-market fit, ran out of money, and sold our company's assets.

## The accidental discovery

In August 2024, we hit a milestone that seemed impossible just months earlier: we were cash flow positive. $25K MRR, actual profits, and for exactly one glorious month, we weren't bleeding money. Carlo and I celebrated by doing what we always did when things went well - immediately making them more complicated.

The thing is, we'd been so focused on the email automation part of FirstQuadrant that we'd missed what was actually magical. Customers weren't excited about our ability to send emails (everyone could send emails). They were blown away by how our AI decided _what_ to do next.

One customer put it perfectly: "I don't care about the emails. I care that your AI knows when to follow up, when to give up, when to reschedule, and when to loop in my manager. It's like having a sales ops person who never sleeps."

We called this decision engine "the Brain" - mostly as an internal joke because saying "our proprietary AI reasoning engine" made us sound like enterprise software salespeople. The Brain would look at an email thread, understand the context, check the calendar, review past interactions, and decide: Should we follow up? Book a meeting? Update the CRM? Archive this lead? Send a different message?

The wild part? We'd built the Brain almost by accident. It started as a simple classifier to decide if replies were positive, negative, or needed human intervention. But over two years of prompt engineering, edge case handling, and customer feedback, it had evolved into something much more sophisticated. It could understand deal progression, identify buying signals, manage complex multi-threaded conversations, and even know when to shut up (harder than it sounds for AI).

## Building the all-in-one platform nobody asked for

By September 2024, we made a classic founder mistake: we decided to build everything. If customers loved the Brain for email, surely they'd love it for their entire sales workflow? We'd become the AI-powered CRM! The Salesforce killer! The everything platform!

"Let's build pipeline management," Carlo said during one of our 11 PM strategy sessions.
"And relationship intelligence," I added, three Red Bulls deep.
"And website visitor identification!"
"And campaign automation!"
"And deal scoring!"
"And..."

You see where this is going.

We spent the next three months in pure building mode. The Brain grew from handling emails to managing entire deal lifecycles. It would track every interaction, update deal stages, create tasks, schedule follow-ups, nurture old relationships, qualify inbound leads, and even tell you which deals were about to die (spoiler: usually the ones where the champion just changed their Slack status to "Former [Company Name]").

The technical complexity was staggering. Every new feature meant new edge cases. What happens when someone replies from a different email? When a meeting gets rescheduled three times? When the CEO randomly joins an email thread? When someone says "yes" but means "yes, please never contact me again"?

Our codebase became a monument to edge cases. We had more if-statements than a philosophy textbook. The Brain's prompt had grown to 20,000 tokens - basically a small novel instructing GPT on the intricacies of B2B sales. One section just handled out-of-office replies. Another dealt with the phrase "circle back" in its seventeen different meanings.

But here's the thing: it actually worked. By December, the Brain was genuinely impressive. It could take a messy inbox and turn it into organized, progressing deals. It knew when to be persistent and when to back off. It could spot buying signals that humans missed. One customer closed a $50K deal because the Brain noticed their prospect had changed their LinkedIn title to include "budget owner" and suggested reaching out again.

## The Brain takes over

In January 2025, we had a revelation that seems obvious in hindsight: we were building the product backwards. Instead of starting with use cases and adding AI, we'd built an AI brain and were desperately searching for use cases to feed it.

So we flipped everything. The new FirstQuadrant wouldn't be an email tool with AI. It would be an AI sales brain that happened to send emails. The entire product would revolve around the Brain making decisions and taking actions, with humans supervising rather than driving.

The UI change was radical. Instead of a traditional CRM with some AI features sprinkled on top, we built an "Actions" view that showed what the Brain wanted to do next. Every morning, you'd open FirstQuadrant to see a list: "Follow up with John about pricing," "Schedule meeting with Sarah," "Update deal stage for Acme Corp," "Check in on stalled GlobalTech deal."

You could approve, reject, or modify each action. The Brain would learn from your decisions (in theory - in practice, it mostly just got confused and started suggesting everyone should "circle back next quarter"). But the mental model had shifted. You weren't using a tool; you were managing an AI employee.

We launched this new version on Bookface in April 2025 with the tagline: "FirstQuadrant - Maximize B2B sales with human-centered AI." The post hit the top 1% of all time. We had 400 waitlist signups in 48 hours. MRR jumped to $13K.

And then, because the universe has a sense of humor, everything started falling apart.

## Good metrics don't pay bills

Here's something they don't teach you at YC: you can have all the vanity metrics and still run out of money. By May 2025, our dashboard looked impressive. New signups every week. NPS was 72. Weekly active usage was growing. We were getting spontaneous LinkedIn shoutouts. What we weren't showing anyone was the churn graph - a ski slope that would make the Alps jealous.

We were also completely broke.

The problem was our unit economics had gotten worse, not better. The Brain was expensive to run. Every decision required multiple GPT-4 calls. Every email generated cost tokens. Every deal update, every task created, every insight surfaced - ka-ching, ka-ching, ka-ching. Our OpenAI bill hit $15,000 in June while our revenue was $11,000. We were literally paying for the privilege of having customers.

Meanwhile, customers expected to pay SaaS prices for AGI capabilities. They'd happily pay $300/month for unlimited AI reasoning that cost us $500/month to provide. When we tried raising prices, they'd leave for some barely functional "AI SDR" charging $99/month. Never mind that our Brain could actually think while theirs could barely spell. In a market where everyone's shopping for silver bullets, the cheapest promise always wins - even if it doesn't work.

We tried everything to fix the math. Caching prompts (saved 30%, not enough). Switching to Claude (cheaper but dumber about sales). Building our own fine-tuned models (worked great until they started telling everyone to "leverage synergies" in every email). Using GPT-3.5 for non-critical decisions (the Brain became obviously stupider and customers noticed immediately).

The real killer was credit consumption. Every action the Brain took cost credits. But customers wanted the Brain to do everything - monitor every email, update every field, track every interaction. One customer imported 10,000 contacts and wondered why their credits vanished in an hour. Another had the Brain running on support tickets and was surprised when it tried to sell their documentation to confused users asking for help.

By July, we had a choice: raise prices 3x and lose most customers, or keep bleeding money until we died. We chose option C: try to raise funding. Again.

## The fundraising death march

August 2025. MRR: $8,900. Runway: 5 months. Morale: "End of an era" (actual Slack message).

We put together our best pitch deck yet. 40 slides of pure storytelling gold. The problem (sales busywork), the solution (autonomous AI), the traction (paying customers!), the vision (every company gets an AI sales team). We even had a slide showing how we'd survived pivoting from furniture to AI, proving we were "resilient founders" (translation: too stubborn to quit).

The investor conversations were painful in their predictability:

"Love the product, but worried about OpenAI building this."
"Impressive tech, but can you expand beyond sales?"
"Great traction, but what's your moat?"
"Solid MRR, but that churn rate..."

That last one always killed us. 40% monthly churn sounds bad because it is bad. We'd explain it was "normal for sales tools" and "customers are just experimenting with AI," but even we didn't believe ourselves.

My favorite was a VC who spent 30 minutes explaining why CRMs would never be disrupted, then asked if we could pivot to building CRM plugins instead. Sure, let me just throw away two years of work to build a Salesforce app that does 10% of what we already built.

We lowered our ask from $2M to $1M to $500K. Still nothing. VCs were scared of AI infrastructure costs. Angels wanted to see more revenue. YC partners were supportive but couldn't write checks. Our existing investors were tapped out or had moved on to shinier things.

Meanwhile, the product kept improving. We shipped HubSpot integration (customers loved it). We made the Brain faster and smarter. We fixed hundreds of bugs. We even figured out how to make money on some accounts by optimizing our prompts and caching strategies.

But it didn't matter. September's MRR dropped to $6,500 as the revolving door spun faster. Three enterprise deals we'd been counting on fell through because they needed Salesforce integration "yesterday" and we needed three months to build it. Our biggest customer churned after just four months - classic sales tech pattern: sign up, try it, realize it's not the silver bullet, cancel. Their new head of sales wanted to "bring everything in-house" (translation: they'd rather fail with their own system than with ours).

The writing wasn't just on the wall; it was in 72-point bold Helvetica with neon underlining.

## The fire sale

On October 15, 2025, Carlo and I had our final founder call. We'd been doing these calls for five years, through furniture pivots, YC, product launches, and more near-death experiences than a medical drama. This one was different.

"We have maybe six weeks of runway left," Carlo said.
"We could try one more pivot," I suggested half-heartedly.
"To what? We've already pivoted from furniture to AI. What's next, crypto?"
We both laughed. Then silence.
"It's time," Carlo finally said.
"Yeah," I agreed. "It's time."

The wind-down was surprisingly systematic. We'd learned from Pabio's messy liquidation. This time, we'd do it right. Notify customers early. Offer full exports. Help them transition. Maybe even find a buyer for the technology.

The customer calls were the hardest part. These weren't just users; they were people who'd believed in us, dealt with our bugs, and shaped our product. Each call felt like a small funeral.

"I'm devastated," one customer said. "FirstQuadrant changed how we do sales."
"Can't you just raise prices?" another asked. "I'd happily pay double."
"What if we pre-paid for a year?" offered a third.

But it was too late. Even if every customer doubled their payment, we'd still be losing money. The infrastructure costs, the team (just us two, but still), the services, the stress - it wasn't sustainable.

The acquisition interest came quickly. Turns out, companies love buying distressed assets. We had conversations with five potential buyers in two weeks. They all wanted the same thing: the Brain.

Not the email automation. Not the CRM features. Not even our customer base. Just the Brain - the AI reasoning engine we'd accidentally built while trying to send better cold emails.

The final deal was anticlimactic. A competitor bought our core IP, including the Brain's architecture and our prompt library (two years of edge cases documented in excruciating detail). The price was enough to pay back some investors and cover the shutdown costs. Not the exit we'd dreamed of, but better than bankruptcy.

On November 1, 2025, FirstQuadrant officially shut down. I pushed the final commit: "End of an era." Carlo archived the Slack workspace. Five years of work, reduced to a ZIP file and a wire transfer.

## Epilogue: The brain lives on

As I write this, pieces of FirstQuadrant are scattered across the AI sales landscape. Our Brain technology powers features in three different sales tools. Our prompt engineering patterns show up in open-source projects. Several customers have told me they still use workflows we designed, just implemented in different tools.

Carlo went back to Switzerland and is consulting for AI companies, helping them avoid our mistakes. He occasionally sends me messages about furniture he sees, always with the caption "at least it's not a subscription."

I'm in Bangalore, building again. Because apparently I learned nothing and immediately started another AI company. This time it's different though (narrator: it was not different).

The funny thing about failure is how normal it becomes. FirstQuadrant was our second failed company after Pabio. You'd think it would get easier, but it doesn't. It just gets more familiar. The stages of grief compressed but not eliminated.

But here's what I learned: we were right about the core insight. Every company does need an AI sales brain. The technology will get cheaper. The models will get better. The infrastructure will stabilize. Someone will build the billion-dollar version of what we attempted.

It just won't be us. And that's okay. We gave it our best shot, built something genuinely novel, and pushed the boundary of what AI could do in sales. We just ran out of money before the market caught up to the vision.

Would I do it again? In a heartbeat. Would I do it differently?

Every single thing.

## Three takeaways

After five years of building and losing two companies, here are the three most important lessons that actually matter:

**Churn is the only metric that doesn't lie.**  
We could sign up new customers every week, but they'd leave just as fast, chasing the next AI SDR that promised to revolutionize outbound. That's not product-market fit; it's a revolving door. In sales tech, everyone's looking for the silver bullet, and when your product doesn't deliver instant magic, they move on. High churn means you're a vitamin in a market shopping for painkillers. We kept celebrating new signups while ignoring that our bucket had no bottom.

**The best product is often the accidental one.**  
We spent two years trying to build an AI SDR, but what we actually built was an autonomous reasoning engine for sales. The Brain - our core innovation - emerged from necessity, not strategy. Every startup thinks they know what they're building, but the real product is usually hiding in plain sight, disguised as a feature or a technical detail. If we'd recognized the Brain as our product earlier, we might have built a focused reasoning engine instead of an everything platform.

**Timing isn't everything; it's the only thing.**  
We were too early for AI agents (2023), too late for simple AI wrappers (2024), and too broke for the autonomous agent wave (2025). Our Brain was groundbreaking when models were weak, table stakes when models got strong, and too expensive when everyone expected AI for free. The graveyard of startups isn't filled with bad ideas; it's filled with good ideas at the wrong time. We built tomorrow's technology on yesterday's infrastructure with today's pricing expectations. That math never works.

Looking back, FirstQuadrant was a technical success and a business failure. We proved AI could autonomously manage sales workflows. We just couldn't prove anyone would stick around long enough to make it matter. In sales tech, everyone's always looking for the next thing, and we were just another stop on their endless journey to outbound nirvana.

But the Brain lives on - in our competitors' products, in open-source projects, in the knowledge that yes, AI can actually think about sales. We didn't build a unicorn, but we built something that mattered.

Sometimes that has to be enough.
