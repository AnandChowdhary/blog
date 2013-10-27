# Internet.org Redesign

I recently participated in an event where I was required to redesign Internet.org’s homepage and logo. The content had to remain the same, but the design was to be completely new. The website was required to be responsive, and good in code-quality and aesthetics, without the use of any external code. The logo was marked for creativity and execution. Here’s what I co-designed with Akshat Srivastava in five hours. And why.

> The relationship between form and purpose—How and Why— is symbiotic. But despite this link, Why is usually neglected, because How is more easily framed. It is easier to recognize failures of technique than those of strategy or purpose, and simpler to ask “How do I paint this tree?” than to answer “Why does this painting need a tree in it?”

While working on redesigning the corporate identity for Internet.org, I had only one thing in mind — the initiative. I believe that before thinking about what to make, I should realize why to make it. They define Internet.org as a global partnership between technology leaders, nonprofits, local communities and experts who are working together to bring the internet to the two thirds of the world’s population that doesn’t have it.

## The Logo

Taking this approach, I started brainstorming about what the logo should look like. When you think about the Internet and connectivity, you see a globe. That’s obvious. But we wanted to go beyond that, and design something simple, yet beautiful for the eye. So, just the two-dimensional shape of the globe—the circle—was selected.

Then, I had to look for a color. To be honest, we were already sure. We didn’t even try any other color out. The color is optimistic and uplifting, rejuvenating our spirit. With its enthusiasm for life, the color also highlights connectivity, and is also visually appealing. So, it was decided that we would go with a flat color, a beautiful shade of orange, tomato.

Another concept I really loved was Jabong.com’s logo. I can’t see a dot in their logo. But when I read the text, I read it as “jabong-dot-com,” simply because the ‘com’ is highlighted, much to my delight. So, I decided to merge our concept of usage of circles with this unique idea. Thus, our logo was the text “internet” in Helvetica lowercase followed by a negative circle with the text “org” in it. A sideline reason was that we wanted to highlight the ‘org,’ since it’s a non-profit organization. Metaphorically, the circle also did a great job since it looks like an enlarged dot, avoiding any confusion. The following was the end-product. Later, we designing similar favicons and Apple-touch-icons.

![Logo](https://svbtleusercontent.com/jysyu4plfooaq_retina.png)

## The Website

Now that we had a logo ready, we had to design a matching website. I jumped back to the ‘Why,’ and realized that the first impression I’d want to give my visitors would be a global one. People from all over the planet—connected—in a way users relate to. So, I took some pictures from Greg Peverill-Conti’s 1,000 faces project and designed a large banner in a way that the pictures looked a lot like profile pictures on leading social media websites, to give them a “connected” feel.

![Website](https://svbtleusercontent.com/l0rl4tf1v3qfgg_retina.png)

To leave an impression of “all the people in the world,” I designed the header in such a way that the background image (on repeat) was the banner I just perfected. Then, I added a few lines of JavaScript animation which imitated an infinite loop of those pictures, going right to left, so it appeared like there were a few more people involved in the initiative every second. The JS for the header, after giving it a repeating background-image set at size cover, was as follows:

```js
window.onload = function () {
  var loopSize = 0,
    loopInterval = setInterval(function () {
      document.querySelector("header").style.backgroundPosition =
        "-" + loopSize-- + " 0";
    }, 100);
};
```

The logic of the above code was simple: When loading of the page was complete, I created an interval for every tenth of a second in which the horizontal position of the background image was one pixel lesser than the previous. So, it looked as if the background was moving towards left, and every time it did so, a new column of faces was born.

Immediately after the header, there was a navbar positioned at the bottom of the visible page. We used a clever algorithm to ensure that the header and the navigation exactly filled the page using window.InnerHeight. On scrolling, the navbar got fixed on the top for providing easy navigation to all parts of the website.

Similar to the original site, we divided the site into sections, ‘Mission,’ ‘About,’ ‘Partners,’ and ‘Contact.’ Alternate sections had a tomato background with white text, while others were white. All sections faded in when the users scrolled to them, giving them a feel of context. We used ‘Source Sans Pro’ in light for typography across the entire website. The site was responsive and used a powerful self-developed grid system.

In conclusion, we designed a simple and flat logo and a responsive and aesthetically-pleasing website for Internet.org in just five hours. The project was an interesting one as I learnt many new things. For the first time, I took more time in researching about the project rather than designing for it.

## Footnotes

1. Chimero, Frank [“The Shape of Design”](http://read.shapeofdesignbook.com/chapter01.html) — Chapter 1 — Quote
2. [Internet.org](http://internet.org/) — Section 3 — Definition of the initative
3. Empower Yourself with Color Psychology — “The Color [Orange](http://www.empower-yourself-with-color-psychology.com/color-orange.html“
4. Photos are copyrighted by [Greg Peverill-Conti](http://www.flickr.com/photos/gregpc/) under a Creative Commons BY-NC-SA 2.0 license
