<!-- Please use the template below when creating a guide. All fields should be in YAML frontmatter -->

---
title: "<Guide Name>"
permalink: <Guide Name>/
excerpt: "One sentence description of guide"
date: 2016-11-03
<!-- Author Name is optional-->
author: "<Author Name>"
<!-- modifiedDate is optional, should only be added if there is an update to the guide  -->
modifiedDate: 2016-12-04
layout: single
---

<!-- Do not need a title because it is added in the frontmatter -->

<!--Include brief, optional intro for the guide here.-->

<!-- This will add a Table of Contents -->
{% include toc %}


## Guide Section Header
<!-- Include section content here -->

## Guide Section Header 2
<!-- Include section content here -->

## Guide Section Header 3
<!-- Include section content here -->


------------------------------------------------------------


<!--Below is a example guide -->

---
title: "Understanding the Internet Archive Web Crawler"
permalink: guide/internet-archive-crawler/
excerpt: "In this document we explain what Heritrix can do, why it needs our help, and also how to identify documents and datasets that Heritrix can’t reach."
author: Matt Price
date: 2016-12-20
modifiedDate: 2017-02-14
layout: single
---

The Internet Archive's [End of Term nomination tool](http://digital2.library.unt.edu/nomination/eth2016/) asks the IA web crawler, [Heritrix](http://crawler.archive.org/), to start crawling from URLs and go 2-3 clicks down in a website’s link hierarchy.

This guide explains what Heritrix can do, why it needs our help, and how to identify documents and datasets that Heritrix **can’t** reach.

{% include toc %}

## How a Web Crawler Works
A webcrawler like Heritrix visits...
