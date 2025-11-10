---
date: 2025-11-10
draft: true
---

# Accidentally founding Koj

This is the first chapter in a five-year retrospective I'm writing for myself as much as for anyone else.

## A real meet-cute

My cofounder [Carlo Badini](https://carlobadini.com) created a new Slack workspace in October 2019. Carlo started Swiss explainer video agency Cleverclip in 2013 and after several years of running it, he was looking for his next challenge. Because he didn't have an idea yet, he visited many of his friends over several weeks to pick their brains. Although he didn't find something he'd like to work on, he observed that many of their apartments were, well, meh. When he asked them why they didn't invest in hiring an interior designer and get a nice place for themselves, they always had the same answer: "It's expensive, and I'm not going to stay here forever... IKEA works."

Carlo couldn't shake that shrug. He figured if people splurge on photogenic Airbnbs for a weekend, why not on the place where they actually live? Over the next few months, he wrote down every brand name he could think of for this idea - Dwely, Shelly, Doma, Cactus, Canary - and circled Koj. The idea was still fuzzy, but there was a clear promise: subscription interior design tailor-made for renters who crave personality without permanent commitments.

Fast forward to March 2020, Carlo posted a job on WeWorkRemotely to hire a Tech Lead/CTO for Cleverclip. We were both previously in the Forbes 30 Under 30 list in 2018, Carlo for Cleverclip in Europe, and I for my previous startup Oswald Labs in Asia, so I applied using that as a hook. Carlo replied in under a day, saying he was impressed by my background and vision, and proposed an alternative: instead of joining Cleverclip, we should co-found a new venture together in the design and furniture space.

![One of the many Zoom meetings we had](/assets/accidentally-founding-koj/koj-zoom-meeting.png)

Over the next few months, we communicated daily on Zoom (sometimes several hours a day), carefully testing our compatibility as partners and discussing ideas before taking the plunge. After 3-4 months of sometimes just swapping furniture links, sometimes discussing ideas, and sometimes stress-testing whether we could disagree without walking away, we were ready to start building.

In parallel, Carlo onboarded an interior designer part time to get started on the first concept for Rahel, his early employee at Cleverclip who later became the studio's CEO and our first customer. After 20 hours of design work and a budget of CHF 20,000 for all furniture, Kateryna prepared a list of all items and Carlo prepared a presentation to pitch Rahel. "They really love it!", he said. In April, Carlo coordinated the ordering and logistics of this first Koj-furnished home, and Kateryna sourced additional items like curtains and decor. She also suggested having a detailed questionnaire filled in by prospects so we can design the initial concept taking their preferences into account and save time spent in revisions.

![Early Koj living room render](/assets/accidentally-founding-koj/koj-render-preview-1.jpg)
![Iterating on the first concept](/assets/accidentally-founding-koj/koj-render-preview-2.jpg)

We celebrated every new visual. Renders like these were the first time the idea felt tangible and it reminded us that we could make rentals feel like intentional homes.

![Moodboard explorations for Rahel](/assets/accidentally-founding-koj/koj-bedroom-concept.jpg)
![Detailing the bedroom atmosphere](/assets/accidentally-founding-koj/koj-bedroom-moodboard.jpg)

In May, I joined the Slack workspace as Carlo's "late" cofounder, although we decided to drop the "late" prefix shortly after. I got started with what all technical founders do: creating a GitHub org, setting up a password manager, availing AWS credits, and so on. We also purchased our first domain, joinkoj.com, and started exploring the business model. I began competitive monitoring of furniture-rental players like Fernish and OliverSpace, and Carlo debated whether it was better to own our own furniture inventory or partner with retailers.

After speaking to founders of other rental companies, we summarized three business models for furniture financing: asset-heavy (equity buys sofas), asset-light (someone else fronts the cash), and marketplace (we connect customers with partner inventories). Carlo already knew the team at XXXLutz, one of the largest furniture retailers in Europe, so that became our opening move. It was also the first time we discussed Y Combinator as a potential funding option.

## Day 1 and beyond

July 1, 2020, was officially my first day working at Koj full-time. Our first project was designing the website together after we purchased koj.co as our new domain. I got to do all the things I love: playing with a new stack, this time Svelte, and setting up localized URLs, lazy-loading blurred thumbnails from a dedicated CDN, Slack bots for signup notifications, and an ElasticSearch cluster for tracking analytics (I know, I know, over-engineering fun-size problems or whatever). We also made a detailed questionnaire to find our ideal customers and launched paid campaigns on Facebook and Google to gather early feedback.

![Our first Koj homepage](/assets/accidentally-founding-koj/koj-screenshot-home.png)
![Style quiz flow we shipped in week one](/assets/accidentally-founding-koj/koj-screenshot-style-quiz.png)

The campaigns went better than we expected, and we started collecting interest in a Firebase database - over 100 prospects in our first few weeks. At the same time, Bernapark, a new development in Carlo's hometown, became our first B2B opportunity to furnish entire buildings. Kateryna curated moodboards and furniture, I evaluated SketchUp/V-Ray and Unreal/Twinmotion for rendering, and Carlo talked to customers and sourced freelance 3D artists to start preparing offers. We also set up Airtable for our internal furniture catalogue and task tracking for each project. To expand coverage, we launched a German-language version of our website; in a pre-LLM age I used the Google Translate API to pre-fill German strings and Carlo corrected every "Stuhl" vs "Sessel" mistake manually.

![Our first Airtable pipeline tracking every lead](/assets/accidentally-founding-koj/koj-airtable.png)
![One of my early render experiments](/assets/accidentally-founding-koj/koj-render-anand.png)

To market to both real estate professionals and consumers, we created dedicated landing pages focused on B2B and the environmental impact of "fast furniture" respectively. With this sudden surge of interest leading to more leads than we could manage, we migrated all leads from Firebase to Pipedrive to centralize pipeline management. We also realized that we probably needed to hire someone to help with sales sooner rather than later, and made several improvements to our onboarding funnel such as adding a date selector for gathering timelines, asking prospects to upload their floor plans, and a new component to visualize different interior design styles.

Leads snowballed. We spun up dedicated landing pages, one for real estate partners, and about the environmental impact of "fast furniture". When we couldn't keep track anymore, we migrated everything from Firebase to Pipedrive and invented a Slack naming scheme: every lead got a `#concept-###` channel. It made the workspace look like a NASA control room.

![Migrating leads into Pipedrive to stop losing follow-ups](/assets/accidentally-founding-koj/koj-pipedrive.png)

Now that we had more interior concepts to design than we could keep in our heads, we came up with a system: lead IDs with corresponding Slack channels (e.g., #concept-454). Our interior design operations scaled up too: Karina joined as our second interior designer, and we partnered with Mockup.Studio for 3D modeling of furniture assets, knowing that we need a long-term 3D model pipeline and internal catalogue of reusable assets. Our first furniture partner, Livique, gave us 30% off the base price and we set up meetings with Pfister to secure a similar deal. Logistics and delivery became another major constraint: our designers reported that many items we'd like to have had 6–15 week lead times, so we needed to decide whether to adjust promises made to customers or pursue direct-manufacturer relationships.

## Stacking incremental improvements

We formalized our process and worked on capacity planning: we now had a three-stage deadline per concept (plan/furniture selection → 3D render → final delivery) and prioritized concepts based on urgency and value. Weekends weirdly converted better, so we cranked up ad spend on Fridays and pretended that was strategic rather than desperate. Carlo invested $100,000 of his own money so we could turn it into renders that made people gasp.

![Miro process overview](/assets/accidentally-founding-koj/koj-miro-2.png)
![Miro optimized process](/assets/accidentally-founding-koj/koj-miro-1.png)

The renders were the bottleneck. Customers kept saying, "I like the idea, but can you make it look more real?" So we obsessed. We added plants, adjusted camera angles, replaced flat lighting with golden-hour warmth, and reworked textures. Carlo negotiated with Accarda for financing because buying furniture outright was going to kill us. We paused new projects for a few weeks to fix processes, and yes, that was as scary as it sounds. Meanwhile, we started raising a pre-seed round of $1 million.

We tightened onboarding questions ("Any built-in closets we should know about?"), built proposal landing pages where customers could click through renders, and introduced decor sets in Airtable so designers could drag-and-drop looks instead of starting from scratch. We charged CHF 80 for proposals - not to make money, but to make sure customers were serious - and refunded it if they signed. Cleverclip backed our line of credit, CreditGate24/Advanon came onboard to finance the furniture, and we re-opened the floodgates with a calmer heart rate.

![Production renders that finally sparked wow-moments](/assets/accidentally-founding-koj/koj-render-0.jpg)
![Dialing in lighting and textures to close sales](/assets/accidentally-founding-koj/koj-render-1.jpg)
![Render iterations from the same apartment to show optionality](/assets/accidentally-founding-koj/koj-render-2.jpg)
![The moment we realized we could deliver premium at scale](/assets/accidentally-founding-koj/koj-render-3.jpg)

## Wrestling with volume

November and December were chaos disguised as traction. Customers loved the concepts but requested "just one more tiny change" five times in a row. We tried imposing a two-revision rule and immediately broke it. The real fix had to be automation.

While Carlo negotiated with Pfister for better pricing and set up a deal with Baloise for including insurance (so "my dog chewed the couch" wouldn't ruin our gross margins), I went deep on rendering workflows. I built a proof-of-concept where customers could mix and match furniture layers from transparent PNGs, which was clunky, but showed the path. But the real insight came from Carlo's good friend and 3D expert Ralph Wiedemeier, who suggested investing in a visual builder where interior designers could drag and drop furniture on a floor plan to automatically generate renders. Over the coming months, Ralph and I worked on a JSON schema output from the web-based tool that a Blender integration parses to render in EC2 spot instances.

![Early compare-and-save calculator for prospects](/assets/accidentally-founding-koj/koj-compare-and-save.png)

## Embrace the pain

Carlo and I set a blunt objective for the first quarter of 2021: "Embrace the pain". We knew we couldn't duct-tape Airtable forever, so we built Lounge, our internal ERP that let designers assign styles, track deliveries, and vent about lead times in one place. Lounge was gloriously janky and gloriously ours.

![Lounge, the internal ERP we hacked together to stay sane](/assets/accidentally-founding-koj/koj-lounge.gif)

The designers standardized three styles - Scandinavian, Industrial, and Modern Chic - so customers could only choose from our standardized catalog. We also hired Neel, our first intern, who joined the same week we submitted our YC application. He ended up knowing more about Zurich furniture warehouses than any reasonable new grad should.

To scale up, we started working with a marketing agency, documented internal processes and tooling in Notion, and hired additional freelance designers. Our favorite product unlock was more interactive proposals. Customers could click a sofa, swap it, and instantly see the price change without waiting for a new render. It felt like magic, even though it required sleepless nights wiring presets, add-ons, and soft credit checks into the backend.

![Updating proposals without waiting on new renders felt like magic](/assets/accidentally-founding-koj/koj-change-gif.gif)
![Showing customers before-and-after changes unlocked faster approvals](/assets/accidentally-founding-koj/koj-change-gif-2.png)

We also worked on PPPP (Price Per Product Project, because naming things is hard), wherein each item was assigned a fixed price for each minimum rental duration that added up to the monthly price, rather than a single price for the entire apartment. It worked: customers stopped asking "Why does my living room cost X?" and started asking "Can I add the lamp?"

Then came the rebrand. We loved Koj, but the world kept pronouncing it "codge" instead of "koi". We couldn't buy the .com and every intro call started with pronunciation lessons. So we threw a naming sprint, explored hundreds of options, and landed on Pabio - warm, memorable, and available. It felt like naming a band right before the big tour.

![Name brainstorming](/assets/accidentally-founding-koj/koj-name-1.png)
![Name brainstorming](/assets/accidentally-founding-koj/koj-name-2.png)
![Koj to Pabio logo change](/assets/accidentally-founding-koj/koj-name-3.png)

By spring 2021 we were tired, proud, and very aware of how fragile the whole system still was. That's exactly why I wanted to write this series: the messy middle was where the magic (and the scars) came from. Here are some of the earliest lessons we learned:

**Start small, but act like it matters.**  
We didn't wait for permission or capital. A few Facebook ads, a designer, a spreadsheet, and a Slack channel turned into real customers. That early speed helped us understand what worked long before the product was "ready."

**Operations are the real product.**  
What looked like an interior design startup was really a logistics and coordination engine: design, sourcing, shipping, assembly, and financing. Most of our innovation came from reducing operational pain, not adding features.

**Every bottleneck hides a new layer of leverage.**  
The reason we built rendering automation, Airtable workflows, and an ERP wasn't aesthetic - it was survival. We learned that scaling manually reveals where automation truly matters.

**Customers teach you faster than any spreadsheet.**  
Our proposal fee, style standardization, and design revisions were all reactions to real customer behavior. Nothing in our early documents predicted that. It reminded me that data is what people do, not what they say.

Next up in this series: how Koj grew into Pabio, the Y Combinator experience, and the messy decisions that followed. Continue to the next article: [The life of Pabio]
