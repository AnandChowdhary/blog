# Introducing Agastya 4 + Augmenta11y

11 months ago, [we launched Agastya 3](https://blog.oswald.foundation/introducing-the-new-agastya-privacy-first-and-universal-9a67ef66cb19), with the promise of a privacy-first accessibility widget. Today, we bring the next major version of Agastya with a focus on user customization, along with an entirely new app. Like the last update, Agastya 4 is currently available to our Pro 1M customers, and will be available to everyone this summer.

## The Road to Agastya 4

The first version of Agastya was launched in 2016 when Nishant, Mahendra, and I founded Oswald Labs (we called it Oswald Foundation back then).

I found old some screenshots to tell the story.

Since I was working with Justice Adda in back in 2016, they were our first partner for adding a beta of Agastya on their website. It looked simple, with the option of choosing any one of five modes.

![Agastya on Justice Adda, August 2016](https://miro.medium.com/max/1000/1*B_DZGmDKK1NJZsIfQA44kA.png)

Interestingly, our most popular (and exclusive!) accessibility mode, dyslexia-friendly mode, was still at the top of our list when we first invented Agastya. It didn’t have all the customization abilities we have today, but it was still ahead of its time and clearly showcased our vision to build the best reading experience for people with dyslexia.

![Agastya in October 2016 (left) and November 2016 (right)](https://miro.medium.com/max/1400/1*QOwv0KkBKvht_d6e_5mw4g.png)

In late 2016, we launched Agastya 1.0. It featured our signature “4-circle” switcher (inspired from Valmiki, our browser extension) so that users could quickly change the color scheme of a website. It also showcased Reading Mode for the first time, which shows the main content of a webpage in a more legible format. We also had webpage translation and a blue light filter.

![Agastya in January 2017 (left) and Agastya 2 in May 2017 (right)](https://miro.medium.com/max/1400/1*-01_rSTOsQs_cqzLeZ_k8w.png)

Learning from our smartphone, Shravan, we quickly realized that higher-contrast buttons with large icons was the way to go in an accessibility application. This was our first major redesign and we launched Agastya 2.0 in May 2017 on our shiny new domain, a11y.co. We also got our first paying client for Agastya during this version.

In June 2018, we launched Agastya 3, our “privacy-first and universal” release.

![](https://miro.medium.com/max/1000/1*BU0jRezMpxJ2VtOvJeYYcQ.png)

This was our largest release to-date, because it was a complete rewrite with an entirely new architecture. Instead of running the plugin interface directly on a webpage, Agastya 3 had a single-page webapp built in Vue.js which controlled the plugin running on the website through an iframe. This allowed us to easily update the interface and add new modes in the future, all while rendering a consistent plugin across websites.

Customers could also customize the header and button colors and text to match their brand.

It also featured new compliancy features like an EU cookie law banner, GDPR data export and download tools, and automate language detection. Our [Intercom](https://www.intercom.com/)-inspired look was a result of our integration with third-party live chat services. Agastya 3.0 also featured an API for controlling the widget programatically.

## Agastya 4

After over 100 betas over three months, we’re proud to launch Agastya 4 with (another) re-write from the group up. Agastya 4 is built around one idea — complete customization. We don’t want to impose any restrictions on what users or developers can do with our plugin.

### User customization

Put simply, users can customize everything. For example, instead of being restricted to our template for dyslexia-friendly mode, users can now build on top of it by changing things like letter spacing and typeface. This is incredibly powerful because dyslexia is not a “one size fits all” problem, and allowing using to customize every aspect of reading means they can decide what works best for them.

![](https://miro.medium.com/max/882/1*hb_vRPf5jE6kn-vDW0dKZQ.png)

Users can adjust the color scheme, typeface, font size, letter spacing, word spacing, and line height in real time to see what works best for them.

Agastya remembers these preferences, so whenever they come back to the website, they’ll always have a great reading experience. Furthermore, for the first time, Agastya remembers preferences across websites. This means that if you turn on dyslexia-friendly mode on our website, when you go to any of our partner websites, Agastya will automatically turn on dyslexia-friendly mode.

Internally, Agastya 4 is written in TypeScript and uses the same architecture as Agastya 3 — a powerful new API for programatic access, combined with a beautiful Vue.js webapp framed interface. We’ve completely automated our deployment process and now use CloudFront to deliver Agastya to users. This gives us access to 169 points of presence in 68 cities across 29 countries.

### Agastya App Store

For developers, we have even more customization.

![](https://miro.medium.com/max/874/1*BB4wunvM4g6nCdOAKnDiCA.png)

You can now completely customize which modes you want to display on your website (and in which order). You can also easily add custom modes using CSS and JavaScript.

We’re also launching the Agastya App Store in beta, where developers can create and share their own plugins, modes, and services which run within the Agastya widget.

For example, we’ve made a share card and an Uptime Robot integration which shows your website’s status in the plugin. We also have integrations for tools like Google Analytics and Oswald Labs Platform services like AutoALT™ (available soon). From Agastya Admin, developers can enable these integrations and customize their widget.

For developers, the Agastya App Store is an easy way to integrate their favorite apps and services using a single TypeScript file (we call these _Agastya Single-file Components_). More information about our developer program will be available soon. We can’t wait to see what you build.

## Powered by Oswald Labs Platform

Agastya 4 is powered by the all-new Oswald Labs Platform. We have a new [API documentation](https://help.oswaldlabs.com/) which allows developers to do everything from enabled modes to tracking custom events. We already track more than 20 events per second and support several API methods.

## Agastya Admin 1.0

We’re finally bring our admin panel outside beta. We now also support multiple API keys and configurations. You can also view analytics, individual user timelines, and aggregations like referrers and countries.

![Events view in Agastya Admin](https://miro.medium.com/max/1400/1*Vd1IJFuQJDqyy0jw-0yCnw.png)

## Say hello to Augmenta11y

Powered by Agastya 4, Augmenta11y is a new smarphone app available for free for Android and iOS devices. It uses Augmented Reality (AR) to show text from the real world in a dyslexia-friendly reading format. In a research on students with dyslexia, the Augmenta11y team found an average reduction in reading time of over 20%. [**Download Augmenta11y**](https://oswaldlabs.com/platform/augmenta11y/)

## Ready? Upgrade Now

Upgrading to Agastya 4 is super simple. Just replace your Agastya loader with the following snippet (replace API_KEY with the API key):

```js
<script async src="https://platform.oswaldlabs.com/_/API_KEY.js"></script>
```

If you’re not already a customer, [**get started for free**](https://oswaldlabs.com/platform/agastya/?utm_source=medium&utm_medium=article&utm_campaign=agastya-4).
