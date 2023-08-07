---
title: "How to add custom syntax highlighting in Hugo"
date: 2023-08-07T21:25:07Z
draft: false
author: "Helgi Arnarson"
tags: ["Hugo"]
# author: ["Me", "You"] # multiple authors
TocOpen: false
hidemeta: false
comments: false
description: "When none of the default Chroma themes quite fit what you're going for, this post will explain how you can do custom highlighting."
canonicalURL: "https://canonical.url/to/page"
hideSummary: false
searchHidden: true
ShowReadingTime: true
ShowBreadCrumbs: true
ShowWordCount: false
ShowRssButtonInSectionTermList: true
UseHugoToc: true
cover:
    image: "<image path/url>" # image path/url
    alt: "<alt text>" # alt text
    caption: "<text>" # display caption under cover
    relative: false # when using page bundles set this to true
    hidden: true # only hide on current single page
---
---

## Getting started

The easiest way to get started is using Hugo to export the settings from a Chroma style and use it for a baseline. Do so with the following command:
```
hugo gen chromastyles --style=dracula > SyntaxHighlight.css
```

This will generate a css file with the settings for the dracula style and save it as SyntaxHighlight.css. You can pick any style you like, reference can be found [here](https://xyproto.github.io/splash/docs/).

---

## Importing the style

First you have to load the new css you exported using the previous hugo command. There are multiple ways to do this, but here's the method I used.
* Copy SyntaxHighlight.css to `/static/css/` in your project.
* If it doesn't already exist, create `/layouts/_default/baseof.html`
* Depending on your theme, you might need to copy the content of baseof.html from the theme folder. 
* In the following screenshot, I'm copying the content of PaperMod theme baseof.html and adding it to baseof.html created in previous step. More information can be found [here](https://gohugobrasil.netlify.app/themes/customizing/#override-template-files).
* Add the link to the `head` section: 
```
<link rel="stylesheet" type="text/css" href="/css/SyntaxHighlight.css">
```
![Info](baseof.png)

Once completed, modify or add the following to the root of your config.yml:
```yml
pygmentsUseClasses: true
pygmentsCodefences: true
```

---

## In closing
Now your site should be respecting the custom css file configuration. You can start experimenting with the color values you want to see in your code snippets, using the text editor of your choice.

Here's a link to a [custom scheme](https://example.com) I setup using this method.