# Introducing the new Agastya

Since we launched Agastya in late 2016, we’ve come a long way. Today, we’re announcing the biggest update to our end-to-end web accessibility platform. This update is currently available only to our Pro 1M customers, and will be available to everyone this summer.

## Privacy-first

With the EU’s General Data Protection Regulation last month, people are familiar with getting tens of emails with updated privacy policies. We’ve been GDPR-compliant from the start, but we’ve radically changed our approach towards users’ data in this release.

### Export and Delete

Since the first time we introduced analytics as part of our suite, we made sure you remain in charge of your data with the option to export all collected data from your websites in JSON format. Now, your users can enjoy the same benefit — with just the click of a button, users can download or permanently delete all their data from our servers.

### Anonymization

We no longer collect and share the IP address of users. Our tracking still works the same way, you get access to insights like countries, cities, browsers, modes, and more, but every IP address goes through a one-way cryptographic hash function before getting stored in our records. No personally identifiable information is ever being stored.

![](https://miro.medium.com/max/1000/1*tyELu4HS_EPtw02POfNFGw.png)

### Cookies

Another thing we’ve seen companies having trouble with is compliance with the EU’s cookie law. With this update, we have a built-in compliance tool which proactively takes consent for strictly necessary cookies and allows users to change their preferences to analytics or other forms of cookies.

### EU Detection

We only show the cookie compliance message to users from within the EU, and share consent information (like what they gave consent to and when) with you, so you can have the same set of customizations in your website. You can also find out if the user is from the EU using our API.

## Universal

We’ve listened to our users and have included a variety of plugin customizations in this update.

### Better SPA Support

Built-in support for tracking actions in single-page apps which no longer listens to hash changes. This makes sure that Agastya works out-of-the-box with modern PWAs and not-so-modern WordPress blogs alike.

### Language Detection

We now also automatically detect the language of the webpage and user to show the plugin in their language. So, if a user from the Netherlands opens Agastya on your Dutch website, it will automatically open in Dutch. Of course, we also offer built-in translation to 100+ languages.

![](https://miro.medium.com/max/1000/1*n9gD1L2kaCTzkMGRlNdKlQ.png)

### Colors & Headings

You can not only customize what modes users can use and get access to analytics, but you can also decide the theme for both the button and the plugin window. You can also change the heading and subheading text to give your users a nice introductory message.

### Faster, Smaller, More Secure

The new Agastya has a (much) smaller footprint and is delivered from our next-generation global content delivery network with over 150 data centers around the globe with services hosted in the EU.
The more efficient loader is just 1.3 KB in size and makes sure you’re always running the latest and most secure version of Agastya. The new plugin interface is written from scratch in Vue.js with dynamic loading, so only the parts your user interacts with are loaded.

### Ready? Upgrade Now

Upgrading to the new Agastya is super simple. Change your loader code to the following line (replace `KEY` with your API key).

```html
<script src="https://agastya-loader.oswaldlabs.com/KEY.js"></script>
```
