---
date: 2025-11-10
draft: true
---

# Accidentally founding Koj

This article is the first in a chronological series of posts reflecting on our startup journey these last five years.

## A real meet-cute

Our Slack workspace was created by my cofounder [Carlo Badini](https://carlobadini.com) in October 2019. Carlo started Swiss explainer video agency Cleverclip in 2013 and after several years of running it, he was looking for his next challenge. Because he didn't have an idea yet, he visited many of his friends over several weeks to pick their brains. Although he didn't find something he'd like to work on, he observed that many of their apartments were, well, meh. When he asked them why they didn't invest in hiring an interior designer and get a nice place for themselves, they always had the same answer: "It's expensive, and I'm not going to stay here forever... IKEA works."

If you're renting in the city and want to be flexible, you're likely not going to invest in high-quality furniture - but what if you didn't have to? And when you're taking a vacation abroad, you always pick a gorgeous Airbnb with Scandinavian furniture and mood lighting, so why not your own home? The idea found Carlo - offering an interior design service personalized to your taste, paired with designer furniture, paid on a monthly subscription in Switzerland. Over the next few months, Carlo spent a few hours every week conducting market research and interviewing potential customers. He also explored brand names - dwely, shelly, doma, cactus, canary - and koj.

In March 2020, Carlo posted a job on WeWorkRemotely to hire a Tech Lead/CTO for Cleverclip. We were both previously in the Forbes 30 Under 30 list in 2018, Carlo for Cleverclip in Europe, and I for my previous startup Oswald Labs in Asia, so I applied using that as a hook. Carlo replied saying he was impressed by my background and vision, and proposed an alternative: instead of joining Cleverclip, we should co-found a new venture together in the design and furniture space. Over the next few months, we communicated daily on Zoom (sometimes several hours a day), carefully testing our compatibility as partners and discussing ideas before taking the plunge. After 3-4 months of these intensive discussions, we felt confident in our collaboration and officially embarked on building our company.

In parallel, Carlo onboarded an interior designer on a part-time contract to get started on the first concept for Rahel, his early employee at Cleverclip who later became the studio's CEO and our first customer. After 20 hours of design work and a budget of CHF 20,000 for all furniture, Kateryna prepared a list of all items and Carlo prepared a presentation to pitch Rahel. "They really love it!", he said. In April, Carlo coordinated the ordering and logistics of all furniture, and Kateryna sourced additional items like curtains and decor. She also suggested having a detailed questionnaire filled in by prospects so we can design the initial concept taking their preferences into account and save time spent in revisions.

![Early Koj living room render](/assets/accidentally-founding-koj/koj-render-preview-1.jpg)
![Iterating on the first concept](/assets/accidentally-founding-koj/koj-render-preview-2.jpg)

We celebrated every new visual. Renders like these were the first time the idea felt tangible and it reminded us that we could make rentals feel like intentional homes.

![Moodboard explorations for Rahel](/assets/accidentally-founding-koj/koj-bedroom-concept.jpg)
![Detailing the bedroom atmosphere](/assets/accidentally-founding-koj/koj-bedroom-moodboard.jpg)

In May, I joined the Slack workspace as Carlo's "late" cofounder, although we decided to drop the "late" prefix shortly after. I got started with what all technical founders do: creating a GitHub org, setting up a password manager, availing AWS credits, and so on. We also purchased our first domain, joinkoj.com, and started exploring the business model. I began competitive monitoring of furniture-rental players like Fernish and OliverSpace, and Carlo debated whether it was better to own our own furniture inventory or partner with retailers.

After speaking to founders of other rental companies, we summarized three business models for furniture financing: Asset heavy (we buy furniture with equity), Asset light (we use factoring), and Marketplace (customers directly buy from our partners). We decided to explore the marketplace model if we could get a few retailers onboard and keep asset-light as the fallback. Carlo already had a relationship with XXXLutz, one of the largest furniture retailers in Europe, so we started there. This was also the time we first talked about potentially applying to Y Combinator in the future.

## Day 1 and beyond

July 1, 2020, was officially my first day working at Koj full-time. Our first project was designing the website together after we purchased koj.co as our new domain. I got to do all the things I love: playing with a new stack, this time Svelte, and setting up localized URLs, lazy-loading blurred thumbnails from a dedicated CDN, Slack bots for signup notifications, and an ElasticSearch cluster for tracking analytics (I know, I know). We also made a detailed questionnaire to find our ideal customers and launched paid campaigns on Facebook and Google to gather early feedback.

![Our first Koj homepage](/assets/accidentally-founding-koj/koj-screenshot-home.png)
![Style quiz flow we shipped in week one](/assets/accidentally-founding-koj/koj-screenshot-style-quiz.png)

The campaigns went better than we expected, and we started collecting interest in a Firebase database - over 100 prospects in our first few weeks. At the same time, a major B2B opportunity emerged with Bernapark, a new housing development in Carlo's hometown of Bern. Kateryna curated moodboards and furniture, I evaluated SketchUp/V-Ray and Unreal/Twinmotion for rendering, and Carlo talked to customers and sourced freelance 3D artists to start preparing offers. We also set up Airtable for our internal furniture catalogue and task tracking for each project. To expand coverage, we launched a German-language version of our website; in a pre-LLM age I used the Google Translate API to pre-fill German strings for Carlo to edit and publish.

![Our first Airtable pipeline tracking every lead](/assets/accidentally-founding-koj/koj-airtable.png)
![One of my early render experiments](/assets/accidentally-founding-koj/koj-render-anand.png)

To market to both real estate professionals and consumers, we created dedicated landing pages focused on B2B and the environmental impact of "fast furniture" respectively. With this sudden surge of interest leading to more leads than we could manage, we migrated all leads from Firebase to Pipedrive to centralize pipeline management. We also realized that we probably needed to hire someone to help with sales sooner rather than later, and made several improvements to our onboarding funnel such as adding a date selector for gathering timelines, asking prospects to upload their floor plans, and a new component to visualize different interior design styles.

![Migrating leads into Pipedrive to stop losing follow-ups](/assets/accidentally-founding-koj/koj-pipedrive.png)

Now that we had more interior concepts to design than we could keep in our heads, we came up with a system: lead IDs with corresponding Slack channels (e.g., #concept-454). Our interior design operations scaled up too: Karina joined as our second interior designer, and we partnered with Mockup.Studio for 3D modeling of furniture assets, knowing that we need a long-term 3D model pipeline and internal catalogue of reusable assets. Our first furniture partner, Livique, gave us 30% off the base price and we set up meetings with Pfister to secure a similar deal. Logistics and delivery became another major constraint: our designers reported that many items we'd like to have had 6–15 week lead times, so we needed to decide whether to adjust promises made to customers or pursue direct-manufacturer relationships.

## Stacking incremental improvements

We formalized our process and worked on capacity planning: we now had a three-stage deadline per concept (plan/furniture selection → 3D render → final delivery) and prioritized concepts based on urgency and value. Weekends produced higher conversion volumes, so we increased our ad spend and continued refining onboarding images and styles to reduce drop-offs. Carlo also personally invested $100,000 to throw fuel on the fire. That confidence boost hit right when exhaustion was settling in.

Our conversion rate wasn't as high as we'd hoped, and one thing kept coming back over and over: render quality was the main sales blocker. To create a "wow" moment for customers, we needed photorealistic renders of the furniture in their own apartments, so we improved our proposals with more decor, better camera angles, higher-resolution exports, realistic textures, and detached shadows. While we curated our 3D model inventory, Carlo negotiated with Accarda for financing these furniture purchases. Because of that financial uncertainty, we paused taking new furniture projects until we had less operational risk. Meanwhile, we started raising a pre-seed round of $1 million - our first taste of the capital treadmill.

As we learned more, we improved our process again. We asked about built-in closets during onboarding, upgraded our tech infra, and created unique landing pages where customers could view their proposals with renders and inventory. We iterated heavily on the proposal/sales experience, adding decor sets in Airtable so designers could create reusable packages and paste them into apartments for faster concept reuse. We also added a fee of CHF 80 for proposals, refunded if customers accepted, and created an e-contract flow so customers could view, accept, and place the order in one sitting. A deal with CreditGate24/Advanon to become our financing partner was struck after Cleverclip provided a guarantee, and we restarted interior operations and scaled with contractors. October closed with operational confidence: new proposal and contract flows live, interior workflows codified, and an action plan to avoid repeating the budgeting mistakes from our first few orders.

![Production renders that finally sparked wow-moments](/assets/accidentally-founding-koj/koj-render-0.jpg)
![Dialing in lighting and textures to close sales](/assets/accidentally-founding-koj/koj-render-1.jpg)
![Render iterations from the same apartment to show optionality](/assets/accidentally-founding-koj/koj-render-2.jpg)
![The moment we realized we could deliver premium at scale](/assets/accidentally-founding-koj/koj-render-3.jpg)

## Wrestling with volume

Client projects dominated the last two months of the year and we realized that customers were too picky and requested many iterations. We experimented with ideas like limiting to one or two last edits per project to protect capacity and margins, but we knew the long-term solution would be to automate the rendering process. While we got to work on that project, we also set up concrete 3D guidance - better framing and proportions, ceiling-hung curtains, bigger plants, messy bed styling - everything we could do to make rendering more realistic. We finalized our deal with Pfister and set up a partnership with Baloise to add insurance to our furniture so customers wouldn't worry about dropping coffee on their couch.

We had a few different directions to improve rendering. I built a proof of concept: a furniture selector prototype to let customers mix pre-rendered furniture layers using transparent-background PNGs with separate shadow layers. But the real insight came from Carlo's good friend and 3D expert Ralph Wiedemeier, who suggested investing in a visual builder where interior designers could drag and drop furniture on a floor plan to automatically generate renders. Over the coming months, Ralph and I worked on a JSON schema output from the web-based tool that a Blender integration parses to render in EC2 spot instances. Koj ended its first full year with multiple homes furnished, signed contracts, paid proposals, and partnerships.

![](/assets/accidentally-founding-koj/koj-compare-and-save.png)

## Embrace the pain

Carlo and I set a blunt objective for the first quarter of 2021: "Embrace the pain". We developed a purpose-built ERP, Lounge, to replace Airtable and launched the rendering service. The designers standardized three styles - Scandinavian, Industrial, and Modern Chic - so customers could only choose from our standardized catalog, and we decided to hire an intern in Zurich. We also applied to YC and hired Neel as our first intern for operations and a new 3D modeler.

![Lounge, the internal ERP we hacked together to stay sane](/assets/accidentally-founding-koj/koj-lounge.gif)

We designed a new proposal experience where customers could click on individual furniture items to replace them in real time without needing new renders or quotes, and updated our backend to support presets for common rooms and addons like lamps. To scale up, we started working with a marketing agency, documented internal processes and tooling in Notion, and hired additional freelance designers. Our improved proposals also had a new pricing structure we developed called PPPP (price per product project... sigh... I'm great at names) wherein each item was assigned a fixed price for each minimum rental duration that added up to the monthly price, rather than a single price for the entire apartment. We also added a soft credit check to avoid risky defaults, improved the e-sign experience, and kept furnishing new apartments.

![Updating proposals without waiting on new renders felt like magic](/assets/accidentally-founding-koj/koj-change-gif.gif)
![Showing customers before-and-after changes unlocked faster approvals](/assets/accidentally-founding-koj/koj-change-gif-2.png)

Our last major project before YC was rebranding. Since Koj is pronounced like "koi", many customers didn't pronounce it right and discoverability was harder because we couldn't secure the .com domain. We made a mindmap of names, ran surveys with friends, and finalized Pabio - a name that sounded warm, traveled well, and had an available domain.

![Early compare-and-save calculator for prospects](/assets/accidentally-founding-koj/koj-compare-and-save.png)

By spring 2021 we were tired, proud, and very aware of how fragile the whole system still was. That's exactly why I wanted to write this series: the messy middle was where the magic (and the scars) came from.

**Start small, but act like it matters.**  
We didn't wait for permission or capital. A few Facebook ads, a designer, a spreadsheet, and a Slack channel turned into real customers. That early speed helped us understand what worked long before the product was "ready."

**Operations are the real product.**  
What looked like an interior design startup was really a logistics and coordination engine: design, sourcing, shipping, assembly, and financing. Most of our innovation came from reducing operational pain, not adding features.

**Every bottleneck hides a new layer of leverage.**  
The reason we built rendering automation, Airtable workflows, and an ERP wasn't aesthetic - it was survival. We learned that scaling manually reveals where automation truly matters.

**Customers teach you faster than any spreadsheet.**  
Our proposal fee, style standardization, and design revisions were all reactions to real customer behavior. Nothing in our early documents predicted that. It reminded me that data is what people do, not what they say.

**Founder pain compounds into founder clarity.**  
"Embrace the pain" became our internal mantra for a reason. Every hard, manual task helped us understand what needed to exist. Each design brief, delayed sofa, or picky customer made the next decision easier.

**The brand evolves slower than the product.**  
Koj's identity changed several times - marketplace vs. asset-light, B2C vs. B2B, and eventually Pabio. Each iteration wasn't a pivot, just a clearer articulation of the same intent: make beautiful homes accessible.

Next up in this series: how Koj became Pabio for real, what changed post-YC, and the messy decisions that followed. Continue to the next article: [The life of Pabio]
