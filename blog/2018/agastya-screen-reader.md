# Introducing Universal Screen Reader on Agastya

Read aloud was one of Agastya’s signature features when it first launched, and our beta partners like [Nayee Disha](http://www.nayeedisha.in/about) — a collaboration between the UNDP and large corporates to skill and employ women in rural India — extensively made use of it. It was the easiest way to have a blind- and illiterate-friendly mode which automatically reads aloud the content of a webpage.

My co-founder Nishant even wrote an entire article about the different ways to detect relevant content on a webpage almost two years ago ([Reading the Right Way](https://blog.oswald.foundation/reading-the-right-way-f5555615ec60) on Oswald Labs Blog), because it’s not very easy to understand what’s important and what’s not.

Modern webpages are filled with hundreds of links, images, ads, etc., so it’s hard to algorithmically find the main content, because screen readers read everything. They start from the header, logo, navigation bar, etc., and continue until the footer — _everything_. This isn’t a problem for everyday users, but non-power users who aren’t familiar with navigation shortcuts need a better way to read the main content of a page (e.g., just the text of a news article instead of reading all the ads and images in between.)

Today, we’re proud to introduce **Read Aloud**, the universal screen reader part of Agastya. Starting today, all our customers using the new Agastya will see a “Read Aloud” button in the plugin which uses AI-powered speech synthesis for industry-leading text-to-speech.

## Semantic and backwards-compatible

Read Aloud automatically finds the most relevant content on a webpage. If you’re using HTML5 tags like `main` and `article`, it’s going to read content from there; if you’re not, it’s going to search for other characteristic sections. If it doesn’t find anything, it’s going to fallback to reading the entire content of the `body`, just like a screen reader would.

The original Read Aloud in Agastya required a `data-read-aloud` attribute in the element you want the plugin to read. This is no longer a requirement, but is supported.

![](https://blog.oswald.foundation/reading-the-right-way-f5555615ec60)

## Easy keyboard navigation

Visually impaired users can use the Left, Right, and Spacebar keys to navigate through parts of a webpage and pause or play speech. We already support opening and closing the plugin using a combination of `F + J`, the two keys which have ridges for identification.

## Works with all modern browsers

Read Aloud on Agastya works with all modern browsers and support goes all the way back to Internet Explorer 9. This is a breakthrough because the Web Speech Synthesis API is only available for a handful of browsers (which doesn’t even include IE, or Firefox or Opera on mobile), so we’re serving high-quality speech from our global CDN powered by our EU-based servers.

## Available today

Before today, we had to manually and individually enable read aloud for each website with Agastya with the selector for the right element to read from. This is no longer the case, and we’re globally releasing Read Aloud today for all our partners. Read Aloud is currently available in English, and will introduce support for 10+ additional languages in the coming weeks.
