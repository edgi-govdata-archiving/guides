---
title: "Seeding the Internet Archive’s Web Crawler"
excerpt: "This guide provides instructions for seeding web pages to Internet Archive End of Term Archive using IA's Bookmarklet or EDGI's Chrome Nomination Extension."
author: "Technoscience Research Unit and EDGI"
creationDate: 2016-12-26
modifiedDate: 2017-02-14
---

This guide provides instructions for seeding web pages to Internet Archive [End of Term Archive](http://eotarchive.cdlib.org/) using IA's Bookmarklet or EDGI's [Chrome Nomination Extension](https://chrome.google.com/webstore/detail/nominationtool/abjpihafglmijnkkoppbookfkkanklok).

<!-- This will add a Table of Contents -->
{% include toc %}

## How the Web Crawler Works

Review how the [What the Internet Archive Web Crawler Does](/internet-archive-crawler/), in brief the Heritrix starts at a URL and saves anything within 3 clicks from that URL seed, Heritrix can’t:

- It **can’t click web form buttons like “Go!” or “Submit”**
- It **doesn’t have a browser environment**
- It **can’t follow links that don’t use the [Hypertext Transfer Protocol (HTTP)](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)** (FTP is handled in a separate crawl)

## Files the Web Crawler Cannot Get
{: #cannot-get}

Based on the limitations above, there are 4 categories of datasets that the Web Crawler can not crawl:

  - **Databases**: Lots of the data on the web is stored in [relational databases](https://en.wikipedia.org/wiki/Relational_database) that are almost never available directly on the web.
  - **Visualization/Interactive Applications**: Lots of the most user-friendly sites display data in a [web application](https://en.wikipedia.org/wiki/Web_application) embedded in a web page.
  - **Document Collections**:  Often, government sites will present documents in a _user-friendly_ frame of some kind. When this is the case, the PDF itself is not usually accessible to the web crawler.
  - **FTP**: Some agencies have a publicly-accessibly FTP site for bulk download of their datasets. While these are crawlable, it is done separately.

## Seeding the Web Crawler

Seeding the web crawler is quite easy and only requires familiarity with the browser and attention to detail. It is important to understand what the Internet Archive's web crawler program, Heritrix, [**can do and can’t do**](). <!-- LINK TO GUIDE -->

### As an individual or a small group of people

The End of Term Project has an excellent [nomination tool](http://digital2.library.unt.edu/nomination/eth2016/), which will also tell you if that URL has already been nominated. You can speed your work by installing their [bookmarklet](http://digital2.library.unt.edu/nomination/eth2016/about/).

To view web pages already in the Internet Archive you can also use their [Wayback Machine Chrome Extension](https://chrome.google.com/webstore/detail/wayback-machine/fpnmgdkabkmnadcjpehmlllkndpkmiak).

### As a large group and/or to record what URLS you are seeding

A large group can overwhelm the End of Term nomination tool, so it is better to use EDGI's [Chrome Browser Extension](https://chrome.google.com/webstore/detail/nominationtool/abjpihafglmijnkkoppbookfkkanklok), this will save URLs to a spreadsheet that EDGI manages and sends to the Internet Archive after your event.

If you would like to steward your own collectively produced spreadsheet, you can fork the Chrome Extension from the [EDGI GitHub repository](https://github.com/edgi-govdata-archiving/eot-nomination-tool), and issues should be reported there. We don't reccomend this option, as you must ensure the spreadsheet containing your results gets successfully forwarded to Internet Archive&mdash;otherwise the links won’t be seeded to the web crawler.

As a courtesy, please send a copy back to EDGI to update our [Agency Office Database](https://envirodatagov.org/archiving/) with your progress!

## Quick Reference "How to Seed"

1. Download EDGI's [Chrome Browser Extension](https://chrome.google.com/webstore/detail/nominationtool/abjpihafglmijnkkoppbookfkkanklok)

    People seeding may want to use these tools to see the work already done at the Internet Archive:

    - End of Term [Nomination Tool](http://digital2.library.unt.edu/nomination/eth2016/)
    - End of Term [Reports](http://digital2.library.unt.edu/nomination/eth2016/reports/)
    - Internet Archive's [Wayback Machine Chrome Extension](https://chrome.google.com/webstore/detail/wayback-machine/fpnmgdkabkmnadcjpehmlllkndpkmiak)

1. Visit a page you wish to nominate. Click the extension icon near the address bar (the icon looks like a black magnifying glass). A form will pop up beneath the icon. If you're working with an [EDGI Agency Primer](https://envirodatagov.org/agencyprimers/), fill in the corresponding Agency Office Code.

1. Identify if there are files that the [Web Crawler Cannot Get](#cannot-get).

1. Submit!
