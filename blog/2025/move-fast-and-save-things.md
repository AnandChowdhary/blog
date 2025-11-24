---
date: 2025-11-21
draft: true
---

# Move fast and save things

This is the third chapter in my five-year retrospective. After [the life of Pabio](/blog/2025/the-life-of-pabio), where we somehow convinced Y Combinator that sofas were SaaS and built an apartment in Zurich's main train station, we were about to discover that math doesn't care about your YC badge.

The culture was... unique? Carlo introduced the XX:59 meeting culture - every meeting started at 29 or 59 minutes past the hour. Miss the 7:59 AM standup by even 30 seconds? You're out, read the notes later. On Saturday, we were nice to let everyone sleep in and have the standup at 9:59 AM instead. So we were working very hard, but perhaps not on the right things.

In the second half of 2022, from the outside it looked like it was starting to work. We had over $700,000 ARR, 200+ subscriptions, and 15-20% monthly growth - a recipe for great investor updates. But behind the scenes, it was a mess.

Our accountability system was elegant to the point of absurdity: quarterly OKRs became weekly MITs (Most Important Tasks), which became daily MITs, which became hourly panic. Every morning's standup started with declaring if you were "On track" or "Fucked up". By month six, "Fucked up" had become our default state of being, and we'd only elaborate if we were actually on track.

For example, we accepted bank transfers because some Swiss customers didn't want to enter their credit card details, but what we got was a daily game of "guess which customer this random CHF 347.23 payment belongs to". Some customers would pay CHF 299 instead of CHF 300 because, I don't know, they liked round numbers? Our reporting became creative fiction and Monique had to moonlight as our part-time CFO.

The Frankenstein monster we called our financial stack - Lounge talking to Stripe talking to Bexio (a Swiss accounting tool) would randomly decide to take vacation days and I'd have to manually reconcile the accounts.

Then came the Tuesday that ruined everything. I was building yet another KPI dashboard (because if you can't fix your business, at least make pretty charts about it) when I created a graph titled "furniture purchase to credit received" because I was curious about the liability side of things. To my shock, the line went down. Like ski-slope-in-the-Alps down.

![Loan to TCV graph](/assets/the-life-of-pabio/loan-to-tcv.png)

Carlo and I had one of those Zoom calls where you just stare at each other in silence for a solid minute. Turns out our debt financing provider had been giving us less and less credit per order. We'd been losing money on every single apartment, for months, and we had no idea.

Carlo went into full forensic accountant mode and built a comprehensive P&L that included all the inconvenient realities we'd been ignoring. Turns out our "30-40% gross margins" assumed we lived in a fantasy world where customers kept paying forever instead of ghosting us after the first year and we were never spending more on buying furniture and organizing deliveries than we were receiving in factoring.

![The Stockholm pivot: Where furniture dreams went to die and software dreams were born](/assets/the-life-of-pabio/pivot-costs.png)

We redid the unit economics to calculate updated pricing for each apartment. A customer who'd been discussing his proposal for weeks, watched his monthly payment go from CHF 450 to CHF 760 while we were on the phone with him, which clearly was not going to work. Since the interest rates were going up and we couldn't significantly raise prices, we were already losing money on every apartment.

The truth hit like a freight train carrying all our damaged furniture: subscription furniture in Europe was fundamentally a zero interest rate phenomenon.

## Wartime CEO

The moment we discovered we were basically a charity for Swiss people who wanted nice furniture, Carlo went full "wartime CEO." I'd never seen someone cut so fast and so deep. Within days of our realization, we killed all marketing spend, stopped taking new orders, and only spent money on things that were absolutely necessary.

Shutting down a furniture subscription business is like canceling Netflix, except Netflix doesn't have 180 angry sofas sitting in your warehouse demanding justice. Within 72 hours, we launched an outlet store to get rid of all our existing inventory at a high discount so we don't have to pay another month of warehouse rent.

![Outlet website showing our digital yard sale](/assets/the-life-of-pabio/outlet-list.png)
![Product page with the world's most honest furniture descriptions](/assets/the-life-of-pabio/outlet-product-page.png)

We had high churn and high customer debt, but good luck collecting that from someone who'd already blocked our number and possibly fled the country. As a last resort, I called every furniture rental company in Switzerland and Germany and tried to get acquired by them, but to no success.

We had some cash left, so we had two options: we could either return the money to our investors, or we could pivot. No investor would want a 0.1x return, so we decided the latter. As part of this, we had to let everyone go, because we didn't even know what we would work on, except that it wouldn't be furniture. So we scheduled hour-long calls with each team member individually, and over the course of a single very long day, we told everyone that we had to let them go. This was one of the worst days of my life. It was really hard to say goodbye to everyone, but it had to be done.

![The last Pabio homepage, forever frozen in time](/assets/the-life-of-pabio/pabio-homepage-outlet-message.png)

The Zurich warehouse stands empty now, probably being used for something sensible like storing things that people actually want. But here's the thing: for two and a half glorious, chaotic years, we helped hundreds of people create homes they loved. We made beautiful spaces accessible. Yes, we learned lessons that are priceless, but after burning through millions.

Sometimes we still hear from old customers. "I still have my Pabio sofa," they'll write. "It's the best furniture I've ever owned." I don't tell them it's probably the only piece of furniture they've ever owned that came with its own bankruptcy story.

## Pivoting to AI

## Three takeaways

Here are the three most important lessons I learned from the last year of Pabio:

**Financial reality doesn't care about your mission.**  
We discovered we were losing money on every order after months of bleeding cash, all because we didn't have proper financial controls. Not having a CFO when you're managing debt financing, inventory, and multi-currency operations isn't lean, it's silly. Every startup thinks they can defer financial rigor until Series A. Plot twist: Series A doesn't come if you're secretly bankrupt.

**Operational debt is worse than technical debt.**  
Every "yes" to a custom deal, every special payment term, every "we'll figure it out later" created compounding complexity that eventually crushed us. Technical debt Claude can refactor on a weekend, but operational debt requires unwinding actual contracts with actual humans who have actual lawyers. We learned that saying no to revenue today saves you from bankruptcy tomorrow.

**The best time to pivot away from something that doesn't work six months ago; the second best time is now.**  
We saw the writing on the wall in June when we redid the unit economics, but we didn't pull the trigger until November when we didn't have another option; we kept trying to make it work somehow. Every month we waited had an opportunity cost. Pivots delayed are pivots denied.

Next up: [Building the first AI SDR].
