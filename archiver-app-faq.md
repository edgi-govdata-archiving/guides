# Archiver App FAQ

### 1) I’m seeing that some URLs may have already been archived by Ann Arbor.
"0" is the *default* priority; it means that no-one has reviewed it.
*UNLESS* it says "MAY HAVE BEEN HARVESTED AT ANN ARBOR" . If it says
that, Assign the priority to 1, so it drops down in the queue, and then
*SKIP IT*.

### 2) What does it mean if it says “Crawled by archive.org”?
“Crawled by archive.org" means the *page itself* was crawled; it may
or may not mean the *dataset* was crawled; you need to judge whether
the data is the sort of thing the archive could crawl and use your best
judgement, IIUC.

### 3) I have a process improvement that would make this go better!
Great! Open an issue in your event-specific GitHub repo, or report it in the
appropriate channel in your Slack team.

### 4) How should I handle overly broad sites with just a search form,e.g.  [**http://www.noaa.gov/ **](http://www.noaa.gov/) ?
In some cases like this, you just have to play around and try to find
the data source it’s referencing. Maybe there’s some way to query that
data. In most cases, it might be difficult/impossible, depending on the
kind of database.

### 5) For stuff that is updated regularly, do we have a scripting system set up?
Not yet; that's a going-forward plan. What you do with those is you
indicate in the notes section for both the Research and Harvest sections
that it is updated regularly, and then mark it complete anyway (per
Matt).

### 6) What if I have a site and want to know if it’s been crawled already
(FTP data or something)?
Internet archive has a plugin you can use to check if something has been
archived:

[*https://chrome.google.com/webstore/detail/wayback-machine/fpnmgdkabkmnadcjpehmlllkndpkmiak?hl=en-US*](https://chrome.google.com/webstore/detail/wayback-machine/fpnmgdkabkmnadcjpehmlllkndpkmiak?hl=en-US)

Or you can check on the internet archive site directly at
[*http://archive.org/web/*](http://archive.org/web/)

### 7) What if the site has in fact been crawled well by the internet
archive?
If the site includes only crawlable data, then there is no need to
harvest it. If the site includes one or more uncrawlable datasets
(including things like a set of PDFs that could probably be crawled),
then harvest the datasets.

### 8) What does it mean when it says "checking out this url will unlock url: xxx"
That means you had another URL checked out and you can only check out
one at a time so it’ll unlock the other.

### 9) What do I do with stuff that’s already in the Link URL section?
If there are a bunch of sub-sites listed that are **not** links, then
you are on the master entry; the child entries are therefore just
advisory and you should try to make sure that your scraping includes all
of them, but otherwise keep going.

If that section has a single thing listed and it’s a link, you are on a
child item, which is the wrong place. Click the link and work there.

### 10) How do I partition the Large Parent URLs (to reduce the size of the download > 5G)?
On the right side of app, click “add URL” for each child. Add
description that these new URLs are children to the Parent URL. Then go
back to Research, check out the parent URL, and link it to all of its
children. Make sure the priory of each child is the same as the parent.
Start harvesting each child.

### 11) Wifi is kind of slow. Anybody have any workarounds for a faster connection?
1. Tether your phone :) Don’t forget to plug in power if you do that.

2. Do as much of the work as possible remotely; spin up an instance at
AWS or something, ssh there, and do the actual downloading/scraping from
there. The fewer people that are using the bandwidth here for big
things, the more there will be for everyone.

### 12) I'm looking at a URL, but I can't edit aything!

Make sure you have checked out the URL (big blue button near the top). None of the felds can be edited until the URL is checked out.

### 13) Why can't I edit the harvesting section?
The app expects users to work their way through the stages ofthe workflow. In order to edit the "Harvesting" section, you will first need to mark "Research" as complete. Look for the "done" checkbox on the right-hand side of the page, on the same line as the **Research** headline.

### 14) When I'm harvesting, clicking on the `Download Zipstarter` button doesn't work
Yeah, that happens a lot. Try reloading, or switching browsers. In general, don't use Safari with the app. 

### 15) In the Research section, what are all the checkboxes for? 
Please read the Workflow documentation for more info!

