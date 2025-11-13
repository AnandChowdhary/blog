---
date: 2025-11-11
draft: true
---

# The Life of Pabio

This is the second chapter in my five-year retrospective. After [accidentally founding Koj](/blog/2025/accidentally-founding-koj) and getting into Y Combinator, we rebranded to Pabio and embarked on what would become an intense journey of hypergrowth, operational complexity, and hard-earned lessons about unit economics and sustainable scaling.

## Our Y Combinator experience

We were on the fence about whether YC was a good fit for us - Koj wasn't "pure tech" and wasn't based in San Francisco. I remember discussing the idea of doing YC with Carlo within the first few months of starting Koj, and it was something I dreamed of in my high school computer club, so it was still very much on the bucket list.

We decided that if we got in and didn't have to move to California, we'd do it, because being close to our customers was crucial - Carlo and Neel were personally attending every delivery in those early days. Carlo's childhood friend Raphael Schaad did YC in Winter 2020 with the calendar app Cron (later acquired by Notion) and blessed us a recommendation and a mock interview. We spent several days perfecting every answer in the application and [recorded the video on Zoom](https://youtu.be/ZTq-O2BNhno).

Although Carlo and I had still not met in person, we had furnished 5 apartments at the time of recording that video ($50k in subscription value). We also shared that we have 150 leads waiting in the pipeline and partnerships with debt financing providers and furniture retailers set up, so we were ready to start scaling up.

Here are some of the most interesting answers from our application:

Please tell us something surprising or amusing that one of you has discovered:

> When selling Koj subscriptions to customers, it's fascinating to observe how little understanding people have for the present discounted value of subscription payments. While a user may say \$350/m with a duration of 3 years is way too much, they readily agree to \$300/m on a 4-year contract.

After a few weeks of patiently waiting, we got an email that we've been selected for an interview. We were really excited because our chance of getting in increased by over 10 times. Apparently YC interviews 4x the number of companies they would admit, so now we had about a 25% chance of getting in. We did 2 or 3 mock interviews, and then D-Day came.

The YC interview is extremely information-dense because you go through so much in only ten minutes. I don't even remember what we talked about; I just remember feeling like we're not going to make it when it was over. It was almost midnight for Carlo and I in Europe, and we got an email after a few hours - they were on the fence about whether they should let us in, so they would like to do a second interview in a few hours. The second time around, we had different group partners, we were less nervous, and had better answers. They told us they're going to call us if we get in, and email us if we don't.

The next morning, Michael Seibel called Carlo; it felt surreal. Suddenly, we were part of the Summer 2021 batch. The program kicked off while we were still firefighting daily operations - Lounge was crashing, customers were waiting on deliveries, and we were manually calculating prices in spreadsheets - now we were doing YC remotely and across time zones.

The first few weeks were chaos. I think those three months were the hardest I have ever worked. We'd join the virtual dinners at odd hours of the night, trying to absorb all we could while our Slack channels exploded with customer issues.

![Screenshot of the kickoff call](/assets/the-life-of-pabio/yc-batch-kickoff.png)

We'd also made the mistake of picking a non-standard KPI metric - MoKs (months of Koj) instead of MRR to incentivize our salespeople to sell longer-term contracts. I swear "How many MoKs did you sell this week?" sounded much better then than it does in hindsight. We thought we were being clever, but YC quickly taught us that standard KPIs exist for a reason. They create alignment, enable comparison, and prevent you from fooling yourself with vanity metrics. We switched to MRR halfway through the batch.

It was pretty funny that our batchmates were building tools for developers while we were figuring out how to ship a sofa from Pfister to an apartment in Zug without losing money. One founder asked us, "So you actually touch physical inventory?" as if we'd admitted to using a fax machine... but the YC partners got it - they'd seen Airbnb go through similar operational complexity in the early days.

![My notes from YC](/assets/the-life-of-pabio/yc-lessons.png)

The batch program forced brutal prioritization. We had to choose between fixing our broken onboarding flow (losing 75% of paid leads between signup and form completion) or expanding to Germany, a much larger market. Between automating our painful manual ordering process or adding the self-serve checkout, the answer was always "fix the thing that's killing you today."

By August, Demo Day prep consumed everything. We practiced our pitch several times, iterating between "We live in a subscription economy, so we're doing that for furniture" (too abstract) and "We're digitizing Europe's €50 billion furniture rental market" (too boring). We finally landed on a simple story: young Europeans move frequently, can't afford tens of thousands to furnish apartments, so we give them designer homes for €300/month.

In fact, your company blurb (short intro) is something YC helps you write on day one, and you keep refining it throughout the batch; our final version was:

> Pabio offers personalized interior design with high-quality furniture rental for Europe. With our asset-light rent-to-own business model, qualified customers can get $20k of new furniture with $0 upfront and monthly payments for up to 4 years.

Demo Day itself was anticlimactic - a pre-recorded video instead of the live performance you'd expect, but we were already over halfway done with our seed round by then (many investors reach out to you during the batch). We had grown from $10K MRR to around $30K MRR in those three months, so we wanted to raise $2M at a $20M cap. We ending up putting a hard stop at $2.2M at $25M, mostly over Zoom calls, bringing our total funding to almost $3.5M.

![Screenshot of the demo day pitch](/assets/the-life-of-pabio/yc-demo-day.png)

A lot of people ask me if what the value of doing YC is. I always say the same thing: It's more than the badge. It's the partners, it's everything you learn during the batch, and it's the incredible community that you are part of for life. That being said, the YC badge opened doors we didn't even know existed. Investors who'd passed on us at a $10M cap during out pre-seed were extremely keen on the $25M valuation. But it also set expectations sky-high.

Being in YC meant we had to "flip" our Swiss company to a Delaware C-corp structure to make it easy for American investors to participate in our seed round. But since we already had revenue in Switzerland, we kept Koj AG operational as a wholly-owned subsidiary. In hindsight, this was incredibly fortunate - when we pivoted, all the furniture liabilities stayed contained in the Swiss entity while the US parent company remained clean. Pure luck, but it saved us.

## Scaling chaos

Post-YC and post-funding, we thought we could finally build product. Instead, we every week brought new fires. Here's a highlight reel - one from each of the next few months:

**August 2021: Chargebee to Stripe:** We'd built our billing on Chargebee, but their developer SDK was riddled with bugs, and we ended up spending more time figuring out which API version to use than charging customers. We started migrating to Stripe while simultaneously trying to cache Chargebee responses. For three days, I warned everyone: "Do nothing and look at nothing related to payments until midnight" (literally quoted from my Slack).

The migration was a nightmare of edge cases. Some customers had been double-charged due to duplicate subscriptions. Others had contracts but no payment methods. We discovered over $40K in unpaid invoices that Chargebee simply hadn't been collecting. Monique, our (external) finance lead, was working overtime to reconcile accounts while I wrote scripts to sync data between three different systems.

![OKRs](/assets/the-life-of-pabio/okrs.png)

**September 2021: Render revolution:** As I shared in my previous post, customers often said "I like it, but can you change the sofa?" Each change meant 48 hours of 3D re-rendering, but I couldn't blame them for wanting to see what that specific sofa would look like in their apartment - after all, that was our value proposition. Ralph proposed something radical: a visual builder where designers could drag furniture onto floorplans and auto-generate renders via EC2 spot instances. We built it in six weeks. Suddenly, we could iterate proposals in minutes instead of days.

But the real breakthrough was the render pipeline itself. Raphael and Laura, our 3D artists, created a library of thousands of furniture models. We standardized everything: 1920x1300 resolution, consistent lighting angles, realistic material textures. When customers saw our renders, indistinguishable from photographs of their apartment, they were ready to sign.

![Floor plan uploading page](/assets/the-life-of-pabio/proposal-floor-plan.png)
![Add-ons page](/assets/the-life-of-pabio/pabio-proposal-addons.png)
![Furniture selection page](/assets/the-life-of-pabio/pabio-proposal-furniture.png)
![Product deatils page](/assets/the-life-of-pabio/pabio-proposal-product.png)

**October 2021: Supplies and Deutschland:** Expanding to Germany seemed logical - same time zone, similar market, bigger opportunity. We didn't anticipate the complexity: different VAT rules, new payment preferences ("Rechnung" culture meant everyone wanted invoices), alternative credit check systems (SCHUFA vs Swiss CRIF), and completely different supplier relationships. Our "copy Switzerland to Germany" plan became a three-month operational marathon, and we hired our new COO Claudia from "big furniture" to bring in a new adult in the room.

Our supplier relationships were complicated at best, catastrophic at worst. Pfister, the Swiss furniture giant, gave us a good discount but had 16-week lead times. Claudia set up collaborations with new retailers and brands such as Nuucon and Hannun - but it was always messy and chaotic. I always thought I would be brainstorming solutions to JavaScript bugs and not that the supplier forgot to ship legs with the dining table.

We onboarded several suppliers, but each had different systems: some required manual email orders, others had B2B portals that broke weekly, and a few we had to call to follow up. Our scrapers were checking product availability across all these sites every night, generating thousands of "product price updated" notifications that drove everyone insane - but we tried to automate what we could to scale faster.

**November 2021: Marketing addiction:** We ran A/B tests with different headlines, redesigned our home page for higher conversion, and invested in better rendering, but over time we became addicted to digital marketing, spending thousands every week on Facebook and Google. Our CAC was around CHF 2,000, which we thought we could easily afford because we sign long-term contracts (yep, we hadn't factored in churn yet).

![Homepage v1](/assets/the-life-of-pabio/pabio-homepage-1.png)
![Homepage v2](/assets/the-life-of-pabio/pabio-homepage-2.png)
![Homepage v3](/assets/the-life-of-pabio/pabio-homepage-3.png)
![Style quiz](/assets/the-life-of-pabio/pabio-homepage-style-quiz.png)

We tried everything else: word-of-mouth (people don't move often enough), B2B partnerships (real estate companies wanted kickbacks we couldn't afford), influencer marketing (nobody cared). We kept returning to the drug of paid acquisition, even though it was killing our unit economics.

![Digital marketing report](/assets/the-life-of-pabio/marketing-report.png)
![Financial dashboard spreadsheet](/assets/the-life-of-pabio/financial-dashboard.png)

The lesson was harsh but obvious: if you need to constantly buy customers, you don't have product-market fit. In hindsight, we were paying people to want our product rather than fixing why they didn't want it organically.

## Automation and Lounge

By early 2022, the sheer volume of manual work was overwhelming us. Each order demanded checking more than 15 supplier websites for product availability, calculating delivery windows across several warehouses, manually entering orders into different supplier systems, and tracking shipments through endless email threads. On top of that, we had to coordinate with our logistics partner for last-mile delivery and arrange for electricians to handle installation. The entire process was time-consuming and exhausting, and it became increasingly clear that our existing workflow was not sustainable.

We built scrapers for every supplier website, but they broke constantly. Our `#automation-errors` channel was a graveyard of failures. Some days, half our product prices would show as CHF 0 because a scraper failed silently and we'd wake up to customers asking about free sofas and have to manually update thousands of prices.

The breakthrough came from desperation: we implemented a "circuit breaker" rule - if a price changed by more than 50%, don't update it automatically, flag it for human review. Then we added Browserless (a headless Chrome service) but kept hitting concurrency limits. Then we tried Playwright but it consumed too much memory. Finally, we gave up on real-time accuracy and accepted that our prices would always be roughly correct, never exactly right, and we updated them overnight.

![Inventory management](/assets/the-life-of-pabio/lounge-furniture.png)
![ERP system](/assets/the-life-of-pabio/lounge-erp.png)

We also rebuilt our internal ERP system, Lounge, from the groud up because we didn't support multiple currencies or suppliers yet. We built an extremely complex piece of software where we manage the entire pipeline, from signing up and uploading your floor plan and photos, to designing and sending the proposal, to e-signing the contract, to placing the furniture order, to coordinating delivery, installation, and customer success - a combination of a CRM, ERP, and design tool, all in one.

![CRM pipeline view](/assets/the-life-of-pabio/lounge-pipeline.png)
![Audit trail](/assets/the-life-of-pabio/lounge-audit.png)

Although this was probably my favorite part of the product, in hindsight I can say that one of our biggest mistakes was building it in the first place. We thought we were "too custom" to use existing products. We needed something that combined asset management, service scheduling, subscription billing, and inventory tracking. Plus, honestly, the tech team needed something to do - just maintaining a website didn't feel like being a "tech company."

![Managing an apartment](/assets/the-life-of-pabio/lounge-apartment.png)
![Adding electricians](/assets/the-life-of-pabio/lounge-electrician.png)

This was classic premature optimization. We spent thousands of hours building features that we could have done manually in minutes. We built an Omocom insurance integration for German customers - then sold fewer than 10 apartments in Berlin total. We created a complex per-apartment pricing calculator, then switched to per-product pricing, requiring painful migrations.

The hours we spent building automated invoicing were more than it would have taken to manually create invoices for our first 100 customers. But my ego wanted to prove we were a tech company. I wanted to build something from scratch. And I was enjoying it a lot.

The lesson? Don't automate until the cumulative manual hours become a non-trivial part of your unit costs. Don't make ego-driven or FOMO-driven decisions. There's no reason to do tech for the sake of tech. If Pabio wasn't a good fit for me because it wasn't a pure tech product, I shouldn't have worked at Pabio - and if it was, I could have connected Retool with Salesforce and do away with a lot less engineering.

## From Istanbul to Zurich

It seems like every time we faced a growth challenge, we added complexity instead of removing friction. When customers said they wanted "something different", we added new styles: Boho, Art Deco, Penthouse, Nordic Farmhouse, Black & White. Each style meant more SKUs, more warehouse space, more supplier relationships. Turns out when people say they want something different, they often mean they just don't want what you're selling.

![New component](/assets/the-life-of-pabio/pabio-component.png)
![Pricing page](/assets/the-life-of-pabio/pabio-pricing.png)

We found ourselves offering bespoke deals to close clients. Some got special cancellation terms, some got net-60 payment. Each exception created operational debt. When one of our largest customers churned, we lost over $10K MRR overnight with no recourse because of their custom contract.

![Onboarding funnel](/assets/the-life-of-pabio/report-onboarding-funnel.png)

Customers weren't converting, so we added virtual consultations, room planning, style quizzes, referral programs. Each feature was a hypothesis that failed. Meanwhile, our core problem - furniture was too expensive and commitment was too long - went unaddressed. Our MRR was growing, but our profitability was tanking.

![Graph of contracts sold](/assets/the-life-of-pabio/report-mrr-sold.png)
![MRR graph](/assets/the-life-of-pabio/report-mrr.png)

In May 2022, with the team exhausted from months of firefighting, we decided to run our first company retreat in Istanbul. It was partly strategic planning, partly team building, mostly desperation to get everyone in one room and figure out what we were actually building.

Neel did an excellent job planning the whole week, and we our team flew in from Zurich, Berlin, New Delhi, and Groningen. When we arrived, everyone had different views on priorities: Sales wanted faster proposal creation, Operations wanted automated ordering, Engineering wanted to rebuild components. Carlo and I just wanted us to stop bleeding money. But by the end of the week, we had strong OKRs for the next three months and a renewed sense of purpose.

![Istanbul team photo](/assets/the-life-of-pabio/istanbul-1.png)
![Istanbul dinner](/assets/the-life-of-pabio/istanbul-2.png)

In September 2022, we pulled off something audacious: we built a pop-up bedroom in Zurich's main train station. Not a booth with brochures - an actual apartment without walls where commuters could test our furniture while waiting for trains - and Carlo actually lived there! This was several months in the making, with interior design, renders, furniture orders, and all the compliance.

![Top view render](/assets/the-life-of-pabio/train-station-render-1.png)
![Side view render](/assets/the-life-of-pabio/train-station-render-2.png)

All day, our team would hang out at that apartment and talk to potential customers about they can also have a really nice place to live in. And in the evening, we organized dinners every night - one with early customers, one with early investors, one with the team, and so on.

![Poster at the train station](/assets/the-life-of-pabio/zurich-poster.png)

I would bring sushi from the take-out place at the train station (sponsored by our friends at Uber Eats), Carlo would sleep in that bed every night, and I would do the dishes in the morning for the next dinner.

![Uber Eats](/assets/the-life-of-pabio/zurich-uber-eats.png)
![Carlo getting interviewed](/assets/the-life-of-pabio/zurich-carlo.png)

Set up a live stream so for all of those days, everyone could see exactly what's going on in real-time. Including seeing Carlo sleep all night (not creepy, I promise).

![Carlo sleeping](/assets/the-life-of-pabio/zurich-carlo-asleep.png)
![Live stream](/assets/the-life-of-pabio/zurich-streaming.png)

I think this was when we were at our peak. But the logistics were insane. We printed graphics, placed ads on TV, hauled in real furniture, and created sample proposals for every style.

![The boys](/assets/the-life-of-pabio/zurich-boys.png)
![Dining table](/assets/the-life-of-pabio/zurich-dining.png)

For five days, we turned the train station into our showroom. The results: thousands of visitors, hundreds of leads, and priceless brand awareness. More importantly, we learned that experiential marketing could crack the trust barrier that plagued online furniture rental.

## Three takeaways

Here are the three most important lessons I learned from scaling Pabio:

**If you need to constantly buy customers, you don't have product-market fit.**  
Our addiction to paid acquisition was a symptom, not a solution. We were paying people to want our product rather than fixing why they didn't want it organically. Real product-market fit doesn't require a marketing budget to sustain. If you don't have word of mouth, referrals, and organic growth on day 1, you likely won't have it on day 1,000 either.

**Don't reinvent the wheel for the sake of it.**  
When we picked MoKs instead of MRR, we thought we were being clever, but we were just being confusing. Standard metrics create alignment, enable comparison, and prevent self-deception. And Building Lounge before we knew what we actually needed was classic premature optimization when we could have used existing tools. Every time we ignored peer-reviewed, empirically-proven advice like YC's, they were right and we were wrong.

**Complexity is the enemy of growth.**  
Every time we faced a growth challenge, our instinct was to add something new - more furniture styles, custom payment terms, bespoke contracts, virtual consultations. But each addition created exponential operational overhead. What started as flexibility to win customers became the very thing that made us too slow and expensive to serve them. The irony is that simplicity - one style, one price, one process - would have forced us to nail the fundamentals instead of papering over problems with complexity.

What's next? We'd find out the hard way that we were bleeding cash on every order and transform from furniture rental to AI sales automation in 48 desperate hours. Continue to the next article: [Move fast and save things](/blog/2025/move-fast-and-save-things).
