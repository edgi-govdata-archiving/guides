---
title: "Understanding the Internet Archive Web Crawler"
permalink: internet-archive-crawler/
excerpt: "In this document we explain what Heritrix can do, why it needs our help, and also how to identify documents and datasets that Heritrix can’t reach."
author: Matt Price
date: 2016-12-20
modifiedDate: 2017-02-14
layout: single
---

The Internet Archive's [End of Term nomination tool](http://digital2.library.unt.edu/nomination/eth2016/) asks the IA web crawler, [Heritrix](http://crawler.archive.org/), to start crawling from URLs and go 2-3 clicks down in a website’s link hierarchy.

This guide explains what Heritrix can do, why it needs our help, and how to identify documents and datasets that Heritrix **can’t** reach.

<!-- This will add a Table of Contents -->
{% include toc %}

## How a Web Crawler Works

A [webcrawler](https://en.wikipedia.org/wiki/Web_crawler) like Heritrix visits web pages and searches for links. When it identifies a link, it follows it to a new page, where it once again identifies links, then follows those, and so on, and so on... As you can imagine, this rapidly leads to a very large number of links!

Internet Archive therefore imposes limits: after **3 “hops”**, Heretrix will stop collecting links and move on to the next “**seed**” on the list. This allows a lot of “territory” to be covered&mdash;moving relatively rapidly through the huge .gov domain&mdash;but it means that there are “hidden depths” which it doesn’t see.

When we nominate seeds, we draw Heritrix’s attention to some of this “deep web,” identifying it as especially important and worth crawling.

## What Heritrix Can and Can’t Get

Heritrix is a clever program, but is fully-automated and runs in a “command-line” environment. That means that there are certain things it can’t do. On the other hand, what it can do, it does very well.

Heritrix can:

- Browse to any `http://` or `https://` link that it finds. This includes datasets in `.zip`, `.csv`, `.xls`, `.xlsx`, `.pdf`, etc.&mdash;as long as the link is really a link to the file, and not an “obfuscated” link that instead points to a page that includes a complex environment (see below).
- Browse to any `ftp://` or [FTP](https://en.wikipedia.org/wiki/File_Transfer_Protocol) links.

Heritrix can’t:

- It **can’t click web form buttons like “Go!” or “Submit”**. Search forms often stop it dead in its tracks, unless there’s a “browse” link on the page to the full list of searchable resources
- It **doesn’t have a browser environment** that can do computing work for it. Many sophisticated webpages ask the browser to do a lot of computational work. Heritrix can’t do that very well.
- It **can’t follow links that don’t use the [Hypertext Transfer Protocol (HTTP)](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)**. This mostly affects resources that aren’t designed for direct web browsing, including:

  - **Databases**: Lots of the data on the web is stored in [relational databases](https://en.wikipedia.org/wiki/Relational_database) that are almost never available directly on the web. Instead, databases serve particular bits of information in response to a request from a webserver, or from the user or browser. Those requests travel over paths that Heritrix can’t follow.
  - **Web Applications**: Lots of the most user-friendly sites display data in a [web application](https://en.wikipedia.org/wiki/Web_application) embedded in a web page. Often these applications use maps or other fancy interfaces to display data in a user-friendly form. Since these applications load “dynamically”&mdash;running in the browser and written in JavaScript, [Java](https://en.wikipedia.org/wiki/Java_(programming_language)), or [Flash](https://en.wikipedia.org/wiki/Adobe_Flash)&mdash;Heritrix won’t see them. If the application goes off line,  Internet Archive will have a copy of the web page, but it will just display an empty box in the middle where the application is supposed to be.
  - **Document Collections**:  Often, government sites will present documents in a _user-friendly_ frame of some kind. When this is the case, the PDF itself is not usually accessible to the web crawler.

## Identifying Uncrawlable Data

Let’s look at one example of a difficult-to-crawl site.

The [EPA’s publication search form](https://www.epa.gov/nscep) ([epa.gov/nscep](https://www.epa.gov/nscep))
leads to a [results pages](https://nepis.epa.gov/Exe/ZyNET.exe?User=ANONYMOUS&Back=ZyActionL&BackDesc=Contents+page&Client=EPA&DefSeekPage=x&Display=hpfr&Docs=&ExtQFieldOp=0&File=&FuzzyDegree=0&ImageQuality=r85g16%2Fr85g16%2Fx150y150g16%2Fi500&Index=1976+Thru+1980%7C1981+Thru+1985%7C2000+Thru+2005%7CHardcopy+Publications%7C2011+Thru+2015%7CPrior+to+1976%7C1991+Thru+1994%7C1995+Thru+1999%7C2006+Thru+2010%7C1986+Thru+1990&IndexPresets=entry&IntQFieldOp=0&MaximumDocuments=15&MaximumPages=1&Password=anonymous&QField=&QFieldDay=&QFieldMonth=&QFieldYear=&Query=climate%20&SearchBack=ZyActionL&SearchMethod=2&SeekPage=&SortMethod=-&SortMethod=h&Time=&Toc=&TocEntry=&TocRestrict=n&UseQField=&ZyAction=ZyActionS&ZyEntry=0). If you open one of the [search results](https://nepis.epa.gov/Exe/ZyNET.exe/P100OW3T.txt?ZyActionD=ZyDocument&Client=EPA&Index=1976%20Thru%201980%7C1981%20Thru%201985%7C2000%20Thru%202005%7CHardcopy%20Publications%7C2011%20Thru%202015%7CPrior%20to%201976%7C1991%20Thru%201994%7C1995%20Thru%201999%7C2006%20Thru%202010%7C1986%20Thru%201990&Docs=&Query=climate%20&Time=&EndTime=&SearchMethod=2&TocRestrict=n&Toc=&TocEntry=&QField=&QFieldYear=&QFieldMonth=&QFieldDay=&UseQField=&IntQFieldOp=0&ExtQFieldOp=0&XmlQuery=&File=D%3A/ZYFILES/INDEX%20DATA/11THRU15/TXT/00000020/P100OW3T.txt&User=ANONYMOUS&Password=anonymous&SortMethod=-%7Ch&MaximumDocuments=15&FuzzyDegree=0&ImageQuality=r85g16/r85g16/x150y150g16/i500&Display=hpfr&DefSeekPage=x&SearchBack=ZyActionL&Back=ZyActionS&BackDesc=Results%20page&MaximumPages=1&ZyEntry=1&SeekPage=x) in a new tab, you’ll be able to follow along with this section.

There are **two red flags** that suggest that important data won’t be preserved by an IA webcrawl.

1. The picture in the center of the page is not an actual PDF, but just an image with your search terms highlighted in yellow. If you right-click to **View Page Source** the page, the HTML source looks like this:

    ```
    <img src="/Exe/tiff2png.cgi/P100OW3T.PNG?-i+-r+85+-g+15+-h+5,0,7,7,31,7,10,0,7,13,3,7,14,28,7,20,20,7,21,45,7,25,36,7,28,
    0,7,32,28,7,34,43,7,37,78,7,42,45,7,42,62,7,43,64,7,45,68,7,51,81,
    7,54,55,7,56,74,7,59,70,7+D%3A%5CZYFILES%5CINDEX
    %20DATA%5C11THRU15%5CTIFF%5C00001231%5CP100OW3T.TIF" style="max-width:none;margin-bottom:5px">
    ```

    Capturing the page content will only archive a single page of the document rather than the document itself!

1. While there is a “link” to the PDF and text documents, they aren’t “real” links. Instead, they are JavaScript commands which dynamically generate the URLs for the requested documents in a new browser window. You can verify this in two ways.

    First, right-click and **Inspect Element** on the PDF link, you’ll see that it looks like this:

    ```
    <a href="#" title="Download this document as a PDF" alt="Download this document as a PDF" onclick="ZyShowPDF('PDF',event)">PDF</a>
    ```

    Heritrix can’t capture links of this kind.

    Second, when clicking on the link, instead of loading right away, the page first gives you a fancy loading screen. This means that some kind of communication between your browser and the server while you wait. Heritrix can’t talk to the server like your browser can!

Based on the above, any crawl will fail to capture the actual document&mdash;the actual resource!

## How You Can Help -- Nominating Seeds

An important task is to identify these uncrawlable datasets and interfaces with the EDGI [Chrome Nomination Extension](https://chrome.google.com/webstore/detail/nominationtool/abjpihafglmijnkkoppbookfkkanklok) and alert data archivers to their location. Many of these datasets may be available for you to download elsewhere, such as [data.gov](https://catalog.data.gov/dataset), a centralized repository of government datasets, or in another part of an agency’s website. Once we know about them, we can try to reverse engineer the interface&mdash;look for clues that identify the underlying data and develop a strategy to preserve it, either through scraping or some other preservation avenue (such as an FOIA request or a manual download at a government library).

For more information on these avenues, see James Jacobs’ [2016 End of Term (EOT) crawl and how you can help](http://freegovinfo.info/node/11477).
