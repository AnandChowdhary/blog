---
date: 2025-11-24
draft: true
---

# Building the first AI SDR

This is the fourth chapter in my five-year retrospective. We decided to [move fast and save things](/blog/2025/move-fast-and-save-things), after discovering we were losing money on every sofa and had to liquidate our furniture inventory in 72 hours, we ended up inventing the first sales tool in the post-ChatGPT era.

## From sofas to software in 48 hours

In December 2022, while our furniture business was literally being dismantled and sold piece by piece, Carlo and I were secretly playing with GPT-3 like kids who'd discovered fire. We'd type prompts, watch the AI respond, and text each other "this is insane" at 2 AM. Carlo even had GPT-3 write our investor update about Pabio's collapse, and when investors complimented the clarity of our communication, we just smiled and nodded.

The pivot wasn't some grand strategic move. It was two founders in denial about their failed startup, desperately looking for something - anything - that could work. We spent weeks brainstorming ideas, scoring them on spreadsheets, and arguing about everything from naming conventions to whether we should just raise $10M for a fake app and go to the Bahamas (we were joking... mostly).

But one problem kept haunting us from Pabio: outbound sales sucked. I mean, it really sucked. At Carlo's previous company Cleverclip, he'd built an 8-person SDR team that generated millions in revenue. But the reality of an SDR's life is soul-crushing: endless LinkedIn stalking, crafting "personalized" messages that were really just templates with {FirstName} variables, and praying for a 2% response rate. We'd spent months at Pabio doing this manually, and it was about as fun as assembling IKEA furniture with missing screws.

That's when it clicked: what if GPT could write actually personalized sales emails? Not just "Hi {FirstName}, I see you work at {Company}" but real, researched, contextual outreach that didn't sound like it was written by a robot pretending to be human?

## The art of launching without a product

Here's where things get wonderfully stupid. Instead of building anything, we decided to test demand first. Over a weekend in January 2023, Carlo created gorgeous mockups in Figma while I turned them into static HTML. No backend, no AI, no actual functionality - just pretty screenshots and smooth animations that looked like a real product.

![The fake idea evaluator we used to test demand](/assets/building-the-first-as-sdr/idea-evaluator.png)

We recorded our screens clicking through the fake interface, stitched together some GIFs, and wrote a Bookface post (YC's internal forum) announcing FirstQuadrant: "a GPT-based outbound sales tool that (actually!) fully automates your B2B outbound activities."

The response was immediate and overwhelming. Hundreds of upvotes, dozens of comments, and people asking how to sign up. We were onto something, but we needed stronger validation than just internet points.

So we did something unorthodox: we added a $10 paywall to join the waitlist.

Yes, you read that right. We charged people money to maybe, potentially, possibly get access to a product that didn't exist yet. We figured if people wouldn't pay $10, they definitely wouldn't pay $700/month for the actual product. Plus, it would filter out the tire-kickers and leave us with people who actually felt the pain we were solving.

Carlo was nervous. "What if people get angry about paying for a waitlist?" I was nervous too, but for a different reason: "What if nobody pays and we realize this idea sucks?"

## The $10 validation hack

Within hours of adding the payment gate, the first $10 hit our Stripe account. Then another. And another. By the end of the first day, we had dozens of paid signups. By the end of the week, hundreds. We made more money from our non-existent product's waiting list than we'd made from actual furniture rentals in some months.

The $10 fee turned out to be genius for unexpected reasons. First, it gave us incredibly high-quality feedback. People who pay even a small amount feel invested and give thoughtful input. Second, it created urgency - people don't want to "waste" their $10, so they actively engaged when we reached out. Third, and most importantly, it gave us their email and payment info, making it trivial to convert them to paying customers later.

But the real validation came from the messages. CTOs of YC companies were DMing us their outbound horror stories. One founder wrote, "I spent 6 hours yesterday writing 20 personalized emails and got 1 response saying 'unsubscribe.' Please build this faster." Another said, "I would pay $10,000/month if this actually works."

We looked at each other over Zoom (we were always on Zoom) and realized: we actually had to build this thing now.

## The race to MVP

The next few weeks were a blur of 18-hour coding days and endless GPT-3 prompt engineering. We discovered that getting GPT to write emails was easy. Getting it to write good emails that didn't sound like a Victorian butler having a stroke? That was hard.

Our early prompts were disasters. The AI would write things like:

> "Dearest Sir or Madam, I hope this electronic correspondence finds you in the most splendid of health and spirits on this fine Tuesday morning..."

Or it would hallucinate features our customers didn't have:

> "I was fascinated to learn about your company's revolutionary quantum blockchain solution for solving world hunger..."

We spent days teaching GPT to not be weird. Don't use "utilizing" when "using" works. Don't mention the weather. Don't pretend to have met them at a conference that doesn't exist. And for the love of all that is holy, stop signing emails with "Yours in perpetual servitude."

The breakthrough came when we stopped trying to make GPT write like a human and started making it write like a good SDR. We created a two-step process: first classify whether this lead is worth emailing (QUALIFIED, MAYBE, or what we eventually named HELL-NO after testing showed the model responded better to dramatic labels), then rewrite a rough template with genuine personalization.

## The Bookface launch playbook

By late January, we had a barely functional MVP. You could connect your Gmail, import leads, and watch GPT write emails. It was buggy, slow, and crashed if you looked at it wrong, but it worked.

Time to launch properly on Bookface.

We'd learned from the first launch that Bookface posts have about a 4-hour window to gain traction before they're buried. So we prepared like it was D-Day. Carlo designed new screenshots showcasing the actual product. I set up demo accounts with pre-loaded data. We drafted personalized messages to every single person who'd engaged with our first post.

But the secret weapon was our existing waitlist. Within minutes of posting, we messaged all 200+ people who'd paid $10: "It's live on Bookface, would love your support!" They flooded the comments with genuine enthusiasm because they were actually invested in our success.

The post exploded. Top 1% of all Bookface posts ever. VCs started sliding into our DMs. Other YC companies wanted demos immediately. We went from 200 to 400 signups in 48 hours.

## The infrastructure nightmare

Here's what they don't tell you about building an AI SDR: the AI is the easy part. The email infrastructure will destroy your soul.

Want to send emails on behalf of customers? You need OAuth. Want those emails to not land in spam? You need domain authentication, DKIM, SPF, DMARC, IP warming, reputation monitoring, and probably a prayer circle. Want to track opens and clicks? Get ready for Apple Mail Privacy Protection to ruin your life. Want to handle bounces? Hope you enjoy parsing SMTP response codes.

We discovered that email providers really, really don't like it when you suddenly start sending personalized emails at scale. Google would randomly disable mailboxes. Our warming service would crash. Customers' emails would land in spam despite perfect technical setup. One customer's IT team flagged us as a "potential cyber attack" because we were sending "too many good emails too quickly" (yes, that was the actual ticket).

The solution was hilariously over-engineered. We'd buy separate domains for each customer (protecting their main domain), create multiple mailboxes on each domain, warm them for weeks using a service that basically sends fake emails to other fake inboxes to build reputation, then slowly ramp up sending while monitoring deliverability metrics across seventeen different parameters.

Our AWS bill for all this infrastructure? About $100 per day just in GPT costs, plus another $50 for email warming, plus whatever we were burning on EC2 instances because I kept forgetting to turn off test servers. We were spending more on infrastructure than most people spend on rent, and we had exactly zero paying customers.

## From zero to... still zero

By May 2023, we had real customers using the product. CoCEO, SimpleHash, Centercode - actual companies sending actual emails to actual prospects. Our Slack channels were filling up with success stories. "5 meetings booked in the first week!" "20% response rate!" "This is magic!"

There was just one tiny problem: nobody was paying us.

We'd been so focused on making the product work that we forgot to charge for it. Every customer was on a "free trial" that we kept extending because we were afraid they'd churn if we asked for money. We had the classic founder delusion: "Once we add this one more feature, then we'll start charging."

The feature list kept growing. Enriched fields that pulled real-time data from the web (a founder mentioned they were profitable in an obscure podcast? We'd find it). Smart scheduling that figured out the optimal time to send emails. Autopilot mode where the AI handled entire conversations. We were building the Rolls Royce of sales tools while our bank account looked like we should be taking the bus.

Michael Seibel from Y Combinator scheduled a call with us. We expected praise for our rapid product development. Instead, he asked one question: "What's your MRR?"

"Well, we have 50 companies using the product actively..."

"That's not what I asked. What's your MRR?"

"..."

"Zero? Your MRR is zero?"

"Technically, yes, but—"

"There are no buts. You have zero revenue. This is not a business. This is an expensive hobby."

## The managed service pivot

After that call, we did something desperate: we became the product ourselves. Instead of self-serve software, we offered a fully managed service. We'll set up your domains, create your mailboxes, write your campaigns, manage your outreach - just pay us $700/month and we'll get you 5 meetings.

It worked. Within weeks, we hit $5k MRR. Companies loved not having to think about email infrastructure or prompt engineering. They just wanted meetings on their calendar, and we delivered.

But it was unsustainable. We were basically running a human-powered service pretending to be software. Every customer required hours of manual setup. Every campaign needed hand-holding. Every technical hiccup meant frantic Slack messages at 2 AM. We'd escaped the furniture operations nightmare only to create a new operations nightmare, except instead of sofas getting stuck in elevators, it was emails getting stuck in spam folders.

The breaking point came in September. We had a dozen managed customers, growing revenue, and exactly zero hours of sleep. Our queue system would crash, leaving hundreds of emails unsent. OpenAI would have outages during customer demos. Mailboxes would get disabled randomly. One customer's campaign started sending emails in German because GPT detected the lead was from Austria and decided to be helpful.

We looked at our burn rate, our revenue, our sanity levels, and made another pivot: we were done with cold outbound. The technology was better suited for warm outreach anyway - reengaging existing customers, following up with old leads, maintaining relationships. You know, the stuff where you actually have permission to email people.

## Three takeaways

Here are the three most important lessons I learned from building the first AI SDR:

**Charge for validation, not just feedback.**  
The $10 waitlist fee was accidentally brilliant. It separated real customers from curious browsers, created psychological commitment, and gave us a payment relationship from day one. Free feedback is worth what you pay for it. Even a tiny payment changes the entire dynamic. If we'd done a free waitlist, we'd probably still be building features nobody wanted.

**Infrastructure is the product in B2B SaaS.**  
We thought we were building an AI email writer. We were actually building an email delivery infrastructure company that happened to use AI. The prompt engineering took weeks; the email infrastructure took months and never really worked reliably. When you're building B2B SaaS, the boring stuff - authentication, permissions, integrations, reliability - IS the product. The cool AI part is just marketing.

**Managed services are a great way to learn, terrible way to scale.**  
Doing everything manually first taught us what customers actually needed versus what we thought they needed. But it also trapped us in a high-touch, low-margin business model that looked like SaaS to investors but felt like a services company to us. The middle ground - productized services - might have been better, but we were too burned out to find it.
