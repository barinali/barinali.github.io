---
author: barinali
comments: true
date: 2016-11-06 20:00:00+02:00
layout: post
link: http://blog.alibarin.com.tr/crawlers-and-spas
permalink: /crawlers-and-spas
title: Crawlers and SPAs
meta_description:
categories:
- Angular.js
tags:
- angularjs
- prerender
- crawler
- spa
excerpt: We build our websites as single page applications. So search engine's crawlers can't fetch the content of our websites. Therefore we must make our websites readable by crawlers.
---

Nowadays, we build our websites as single page applications. So search engine's crawlers can't fetch the content of our websites. Therefore we must make our websites readable by crawlers.

Actually, there is not so much things to do for that. There is just a thing to be done. We need to add a layer to our infrastructure such as <a rel="nofollow" href="http://prerender.io">prerender</a>. Then we can manage SE's crawlers and show our content them. I don't want to make this post long. Just I want to make a point on this requirement. Because SEO (Search Engine Optimization) is absolutely required in our day. Naturally, fetching by crawlers is the first rule of this.

Besides this, I want to mention one last thing. There is a thing that can make you happy if you build your single page application by EmberJS. It's <a rel="nofollow" href="https://github.com/ember-fastboot/ember-cli-fastboot">Ember FastBoot</a>. You can render your single page application on server-side. Thus you don't have to add prerender to your infrastructure.
