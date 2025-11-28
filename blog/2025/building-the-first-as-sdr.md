---
date: 2025-11-29
draft: true
---

# Building the first AI SDR

This is the fourth chapter in my five-year retrospective. We tried to [move fast and save things](/blog/2025/move-fast-and-save-things) after discovering we were losing money on every sofa and had to liquidate our furniture inventory in 72 hours, and ended up inventing the first sales agent in the post-ChatGPT era.

January 2023. My highschool sweetheart Sukriti and I were about to get married in a beautiful ceremony in India. Except I wasn't really there - not mentally, anyway. While my then-fiancée was coordinating with vendors, finalizing the guest list, choosing flowers, and handling the thousand tiny decisions along with my family that make a wedding happen, I was on my laptop in the corner, debugging GPT-3 prompts. Our furniture business was collapsing in Switzerland, Carlo and I were frantically pivoting to AI, and I was physically present but emotionally checked out of my own wedding preparations.

I need to say this clearly: Sukriti and my family did everything - they carried the entire weight of the wedding while I contributed approximately nothing except stress and distraction. I should have been there more. I should have put the laptop away. I should have been a better partner in those weeks. But when you're watching one company die while trying to birth another, your judgment gets clouded. She deserved better, and I'm still grateful she married me anyway.

## Selling a product that didn't exist

Here's where things get wonderfully stupid. We didn't have a product. We didn't have a prototype. We didn't even have a backend. What we had was audacity and Figma.

For weeks before the wedding, while our furniture business was being dismantled piece by piece, Carlo and I had been secretly playing with GPT-3. We'd type prompts, watch the AI respond, and text each other "this is insane" in the middle of the night. Carlo even had GPT-3 write our investor update about Pabio's collapse, and when investors complimented the clarity of our communication, we just smiled and nodded.

The AI outbound idea kept winning our scoring sheets. Every founder we talked to had the same complaint: outbound sales was either impossibly expensive (hire SDRs) or impossibly time-consuming (do it yourself). At Carlo's previous company Cleverclip, he'd built an 8-person SDR team that generated millions in revenue. But the reality of an SDR's life is soul-crushing: endless LinkedIn stalking, crafting "personalized" messages that were really just templates with `{FirstName}` variables, and praying for a 2% response rate.

That's when it clicked: what if GPT could write actually personalized sales emails? Not just `Hi {FirstName}, I see you work at {Company}` but real, researched, contextual outreach that didn't sound like it was written by a robot pretending to be human?

So we did something unorthodox: we decided to sell it before building it.

A few weekends before the wedding, Carlo designed pixel-perfect mockups of the product in Figma, and I turned them into static HTML and CSS - emphasis on static. No backend, no database, no AI. Just screen recording in a browser to like a real product. You could click buttons that did absolutely nothing except navigate to another fake screen. It had prospecting, email generation, scheduling, sending, and reporting.

![The fake idea evaluator we used to test demand](/assets/building-the-first-as-sdr/idea-evaluator.png)

Before we launched, I had another unorthodox idea: we'd charge $10 to join the waitlist.

Yep - we'd charge people money to maybe, potentially, possibly get access to a product that didn't exist yet. I figured signing up for waiting list is free, but if you're taking your credit card out and actually paying $10, that's a very strong signal.

We stitched together some GIFs and wrote a Launch Bookface post (YC's internal forum) announcing FirstQuadrant: "a GPT-based outbound sales tool that (actually!) fully automates your B2B outbound activities." The "(actually!)" was doing a lot of heavy lifting considering the product actually didn't exist yet.

The response was immediate and overwhelming. Hundreds of upvotes, dozens of comments, and people asking how to sign up. But more importantly: people were actually paying. Within hours, the first $10 hit our Stripe account. Then another. And another. By the end of the first day, we had dozens of paid signups. In the next few weeks, hundreds. We made more money from our non-existent product's waiting list than we'd made from actual furniture rentals in our first few months.

Meanwhile, back in Switzerland, our furniture company was still dying. The acquisition deal was in negotiations, our debt financing partner was ghosting us, and customers were asking where their sofas were. Every morning started with a surreal context switch: check the Pabio liquidation spreadsheet, then check the FirstQuadrant waitlist revenue.

The $10 fee turned out to be genius for unexpected reasons. First, it gave us incredibly high-quality feedback. People who pay even a small amount feel invested and give thoughtful input. Second, it created urgency - people don't want to "waste" their $10, so they actively engaged when we reached out. Third, and most importantly, it gave us their email and payment info, making it much easier to convert them to paying customers later.

We looked at each other over Zoom and realized: we actually had to build this thing now. We'd sold a product that didn't exist, and now hundreds of people were waiting for it.

## AI SDR in 3 weeks

Our plan for Q1 2023 was aggressive: January was for the "fake" launch and validation. February was for building the actual functioning MVP. March was for acquiring first paying customers. We even had dreams of a Product Hunt and TechCrunch launch announcing both the Pabio acquisition and FirstQuadrant simultaneously - the ultimate phoenix-from-the-ashes story (the acquisition fell throug, so this didn't happen anyway).

The next few weeks were a blur of 18-hour coding days and endless GPT-3 prompt engineering. We discovered that getting GPT to write emails was easy. Getting it to write good emails that didn't sound like a Victorian butler having a stroke? That was hard.

Our early prompts were disasters. The AI would write things like:

> "Dearest Sir or Madam, I hope this electronic correspondence finds you in the most splendid of health and spirits on this fine Tuesday morning..."

Or it would hallucinate features our customers didn't have:

> "I was fascinated to learn about your company's revolutionary quantum blockchain solution for solving world hunger..."

We spent days teaching GPT to not be weird. Don't use "utilizing" when "using" works. Don't mention the weather. Don't pretend to have met them at a conference that doesn't exist. And for the love of all that is holy, stop signing emails with "Yours in perpetual servitude."

The breakthrough came when we stopped trying to make GPT write like a human and started making it write like a good SDR. We created a two-step process: first classify whether this lead is worth emailing (QUALIFIED, MAYBE, or what we eventually named HELL-NO after testing showed the model responded better to dramatic labels), then rewrite a rough template with genuine personalization.

We had to understand what a company actually did, which meant crawling their website and extracting meaningful context. The UX evolved into something clever: generate a first email template based on one example account and what you do, generate a second email from the first, then show 5 sample emails to let people see how personalization actually worked before they committed. Every time someone edited an email, we'd automatically add most recent changes to the few-shot learning examples - teaching the AI their voice through their corrections.

By late January, we had a barely functional MVP. You could connect your Gmail, find leads, and watch GPT write emails. It was buggy, slow, and crashed if you looked at it wrong, but it worked. We'd gone from Figma mockups to actual software in about three weeks, powered by caffeine, desperation, and the knowledge that hundreds of people had paid us $10 each for something we'd promised to deliver.

## The infrastructure nightmare

Here's what they don't tell you about building an AI SDR: the AI is the easy part. The email infrastructure will destroy your soul.

Want to send emails on behalf of customers? You need OAuth. Want those emails to not land in spam? You need domain authentication, DKIM, SPF, DMARC, IP warming, reputation monitoring, and probably a prayer circle. Want to track opens and clicks? Get ready for Apple Mail Privacy Protection to ruin your life. Want to handle bounces? Hope you enjoy parsing SMTP response codes.

We discovered that email providers really, really don't like it when you suddenly start sending personalized emails at scale. Google would randomly disable mailboxes. Our warming service would crash. Customers' emails would land in spam despite perfect technical setup. One customer's IT team flagged us as a "potential cyber attack" because we were sending "too many good emails too quickly" (yes, that was the actual ticket).

The solution was very manual. We'd buy separate domains for each customer (protecting their main domain), create multiple mailboxes on each domain, warm them for weeks using a service that basically sends fake emails to other fake inboxes to build reputation, then slowly ramp up sending while monitoring deliverability metrics across seventeen different parameters. Do things that don't scale.

Our AWS bill for all this infrastructure? About $100 per day just in GPT costs, plus another $50 for email warming, plus whatever we were burning on EC2 instances because I kept forgetting to turn off test servers. We were spending more on infrastructure than most people spend on rent, and we had exactly zero paying customers.

During this same period, the Pabio acquisition was falling apart. Our debt financing partner refused to negotiate, the German buyer walked away, and our lawyer was preparing bankruptcy filings for Koj AG. Some mornings Carlo would be on a call with our Swiss accountant discussing how to write off the furniture to zero, then immediately switch to a call about email warming best practices. The whiplash was disorienting.

## From zero to... still zero

By May 2023, we had real customers using the product. Actual companies sending actual emails to actual prospects. Our Slack channels were filling up with success stories. "5 meetings booked in the first week!" "20% response rate!" "This is magic!" (all real quotes).

There was just one tiny problem: nobody was paying us.

We'd been so focused on making the product work that we forgot to charge for it. Every customer was on a "free trial" that we kept extending because we were afraid they'd churn if we asked for money. We had the classic founder delusion: "Once we add this one more feature, then we'll start charging."

The feature list kept growing. Enriched fields that pulled real-time data from the web (a founder mentioned they were profitable in an obscure podcast? We'd find it). Smart scheduling that figured out the optimal time to send emails. Autopilot mode where the AI handled entire conversations. We were building the Rolls-Royce of sales tools while our bank account looked like we should be taking the bus.

## The call that changed everything

We scheduled a call with Michael Seibel from Y Combinator. We expected praise for our rapid product development. We'd pivoted from furniture to AI in record time, built a working product, gotten real users - surely he'd be impressed.

The call started normally enough. We showed him our dashboard, our user growth, our engagement metrics. Carlo was excited, talking about the tens of companies actively using the product, the testimonials we'd collected, the technical breakthroughs we'd made.

Michael listened. Then he asked one question: "What's your MRR?"

The call went silent.

"Well, we have 50 companies using the product actively..."

"That's not what I asked. What's your MRR?"

I could feel my face getting hot. Carlo jumped in to explain our freemium strategy, our conversion plans, how we were building trust before monetizing.

Michael cut him off. "What's your MRR?"

"..."

"Zero? Your MRR is zero?"

"Technically, yes, but we have a really solid—"

"There are no buts." Michael's voice wasn't angry, which somehow made it worse. It was the voice of a parent explaining something obvious to a child. "You have zero revenue. This is not a business. This is an expensive hobby. You're building features instead of building a company."

He paused. "How long has it been since you pivoted?"

"About five months."

"Five months and zero dollars. What were you doing at Pabio when you had zero revenue?"

"We were... losing money on every order." The irony of the situation hit me. We'd discovered Pabio was bleeding cash and immediately panicked. Now we had a new company that had never made a single dollar and we were celebrating.

"You're making the exact same mistake," Michael said. "You're substituting metrics that feel good for the only metric that matters. Users don't pay your bills. Revenue does. Until someone gives you money, you don't know if you have a product. You have a hypothesis."

The call lasted maybe 20 more minutes, but I don't remember any of it. I just remember Carlo and I sitting in silence afterward, staring at our beautiful dashboards full of users who hadn't given us a single cent.

## The managed service pivot

After that call, we did something desperate: we became the product ourselves. Instead of self-serve software, we offered a fully managed service. We'll set up your domains, create your mailboxes, write your campaigns, manage your outreach - just pay us $700/month and we'll get you 5 meetings.

It worked. Within weeks, we hit $5k MRR. Companies loved not having to think about email infrastructure or prompt engineering. They just wanted meetings on their calendar, and we delivered.

But it was unsustainable. We were basically running a human-powered service pretending to be software. Every customer required hours of manual setup. Every campaign needed hand-holding. Every technical hiccup meant frantic Slack messages at 2 AM. We'd escaped the furniture operations nightmare only to create a new operations nightmare, except instead of sofas getting stuck in elevators, it was emails getting stuck in spam folders.

While we were doing this, the Pabio liquidation was grinding on. Our accountant Monique was writing furniture down to zero while we were writing code. Customers were being told to redirect their subscription payments to our debt financing partner. The Swiss subsidiary was entering formal bankruptcy proceedings. It was surreal to have two companies simultaneously - one dying, one being born - both demanding our attention.

The breaking point came in September. We had a dozen managed customers, growing revenue, and exactly zero hours of sleep. Our queue system would crash, leaving hundreds of emails unsent. OpenAI would have outages during customer demos. Mailboxes would get disabled randomly. One customer's campaign started sending emails in German because GPT detected the lead was from Austria and decided to be helpful.

We looked at our burn rate, our revenue, our sanity levels, and made another pivot: we were done with cold outbound. The technology was better suited for warm outreach anyway - reengaging existing customers, following up with old leads, maintaining relationships. You know, the stuff where you actually have permission to email people.

## The CRM pivot

By October 2023, we were exhausted from playing human email servers. Our managed service model had us manually setting up domains at 3 AM, debugging why Klaus from Munich was receiving emails in German, and explaining to customers why their campaigns to info@genericcorp.com had a 0% response rate.

That's when we had our "aha" moment: why were we trying to email strangers when companies had thousands of warm leads sitting in their CRMs gathering dust?

The pivot wasn't elegant. While our lawyer was literally filing bankruptcy papers for Koj AG (yes, we were still cleaning up that mess), Carlo and I decided to completely refactor FirstQuadrant. Not just a feature update - a complete philosophical shift from "spray and pray" cold outbound to intelligent CRM automation.

Our Slack was a schizophrenic mix of bankruptcy proceedings ("alle Möbel von CHF 896'000 auf CHF 0 abschreiben") and product planning ("create strategy for combining new product in the current codebase"). The irony wasn't lost on us. While one company was being written down to zero, we were writing code for another that we hoped would be worth something someday.

## The second Bookface launch

By January 2024, we had something that barely worked but was 10x better than what existed. Instead of cold emails to strangers, FirstQuadrant would intelligently re-engage old leads, automate follow-ups with context from past conversations, and handle the tedious parts of sales that SDRs hate.

Remember that $10 waitlist from a year earlier? Those 200+ people who'd literally paid to wait? They became our secret weapon again.

On January 24, 2024, we launched on Bookface a second time. Within minutes of posting, we messaged every single person on our waitlist: "It's live on Bookface, would love your support!" They flooded the comments with genuine enthusiasm. Why? Because they'd been waiting a full year and had skin in the game.

The post exploded. Top 1% of all Bookface posts ever. Our waitlist went from 268 to 681 signups in a week. MRR jumped from $5,600 to $7,000. We were so overwhelmed that wait times for onboarding stretched to 6+ months.

But success, as we'd learn, comes with its own special flavors of disaster.

## Gmail's revenge

February 2024 started with Google deciding to enforce new anti-spam policies. Overnight, our customers' carefully warmed mailboxes started getting suspended. Not rate-limited. Not warned. Suspended. Dead. Kaput.

The first message came from Athina: "None of our emails are going out." Then another. Then another. Within 48 hours, we had a full-blown crisis. Gmail had essentially declared war on cold email, and we were caught in the crossfire.

Our Slack turned into a 24/7 war room. Carlo and I were writing appeals to Google at 2 AM, buying new domains at 3 AM, and teaching customers about SPF/DKIM/DMARC records at 4 AM. We became involuntary experts in email deliverability, learning obscure SMTP response codes and the difference between a 4.7.1 rate limit and a 5.5.1 hard bounce.

The solution was absurd in its complexity. For each customer, we'd:

1. Buy 2-4 separate domains (not subdomains - Google hates those)
2. Create 2 mailboxes per domain
3. Warm them for 6 weeks using services that send fake emails to other fake emails
4. Gradually ramp to 30 emails/day/mailbox
5. Monitor 17 different deliverability metrics
6. Pray to the email gods

One customer, frustrated by the complexity, asked, "Can't you just make it work?" I wanted to respond, "Sure, let me just call my friend Susan at Gmail and ask her to pretty please stop marking our emails as spam." Instead, I wrote a 2,000-word guide on email warming best practices.

## The growth paradox

Despite Gmail trying to murder our business, we kept growing. By March, we hit $13k MRR. By July, $20k. But the growth came with a paradox: the more successful we became, the more apparent our problems were.

Our "Brain" - the AI system that decided whether to follow up, how to respond to replies, and when to book meetings - would occasionally have seizures. It once sent a follow-up email two weeks late that started with "Sorry for the delay, I was traveling." The lead responded, "Two weeks of traveling? Must have been quite the trip!"

Another time, it classified a clear meeting request ("Let's hop on a call Tuesday at 2 PM") as "Out of Office" and sent an automated "Thanks for letting me know! I'll follow up when you're back!" The customer was not amused.

The technical debt was crushing us. Every customer success required three fires to be put out. Our standups became therapy sessions:

**Fucked up:**

- Too many bugs
- Demo broke again
- Mailboxes suspended
- Brain is hallucinating
- Apollo rate limits hit
- Customer is angry
- Everything is on fire

**Fucking amazing:**

- We're still in business!
- Someone paid us
- That bug from yesterday is fixed
- Coffee exists

## The infrastructure trap

By mid-2024, we were living a hard reality. Our product wasn't an AI that wrote emails - it was:

- A DNS management system
- An email warming service
- A deliverability monitoring platform
- A mailbox rotation scheduler
- A bounce handler
- A rate limit manager
- An IP reputation tracker
- A spam trap detector
- Oh, and also some AI that writes emails

We'd become the very thing we tried to avoid - an email infrastructure company. Except instead of building on solid ground, we'd built on quicksand. Gmail could change a policy and destroy our business overnight. Our entire $20k MRR hung by the thread of Google's spam detection algorithms.

The final straw came in June. After another weekend of manually reconnecting mailboxes and apologizing to customers, Carlo and I had a heart-to-heart. We could keep playing whack-a-mole with email deliverability, or we could admit defeat and pivot. Again.

On June 30, 2024, we made the announcement: "We're discontinuing our email deliverability tooling by December 31, 2024." No more warming. No more DNS management. No more fighting Gmail.

It felt like admitting defeat, but it was actually admitting reality. We weren't going to out-engineer Google's spam filters. We weren't going to solve cold email deliverability. We were two guys with a dream and a rapidly depleting bank account, not the email infrastructure messiahs.

We'd stripped FirstQuadrant down to its bones. No more domain buying. No more mailbox warming. No more deliverability monitoring. What was left?

That question would lead us to our biggest discovery yet - but it would also lead us to our biggest failure.

## Three takeaways

After building an AI SDR through multiple pivots, a bankruptcy, and Gmail declaring war on us, here are the three most important lessons that actually matter:

**Charge money immediately, even if it hurts.**  
The $10 waitlist fee was our best decision - it separated real customers from tourists, created psychological commitment, and gave us a payment relationship from day one. But more importantly: charging money forces you to confront reality. When people won't pay even $10, you don't have product-market fit, you have a hobby. Michael Seibel was right - five months with zero revenue meant we were building features, not a company. The money helps you realize that faster.

**Sell before you build.**  
We launched on Bookface with literally nothing - Figma mockups turned into static HTML with no backend. The screen recording looked real, but there was nothing behind it. That "fake" launch generated thousands in waitlist revenue and proved demand before we wrote a single line of actual code. If we'd built first and launched later, we might have spent months building something nobody wanted. Instead, we had hundreds of paying customers before we had a product.

**Infrastructure is a trap.**  
We thought we were building an AI email writer. We were actually building email infrastructure - DNS management, warming services, deliverability monitoring, bounce handling. The AI was maybe 10% of what we actually built. If you find yourself spending 90% of your time on something that isn't your core product, you're building the wrong thing. Sometimes you have to strip everything away to find what actually matters.

Next up, the final chapter: How we discovered what was actually valuable in the wreckage of our email infrastructure, why $20k-$30k MRR and early product-market fit signals still weren't enough, and how we made the hardest decision of all: [Finding the real product and running out of money](/blog/2025/finding-the-real-product-and-running-out-of-money).
