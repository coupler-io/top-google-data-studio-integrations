---
title: Connect YouTube Analytics to Google Data Studio with Coupler.io
slug: connect-youtube-analytics-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-google-data-studio.md
source: YouTube
destination: Google Data Studio
meta_title: Connect YouTube Analytics to Google Data Studio with Coupler.io
meta_description: Send YouTube channel stats, video stats, subscribers, and traffic sources to Google Data Studio on a schedule and track every channel in one dashboard.
---

![YouTube Analytics](https://static.coupler.io/importers/youtube.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect YouTube Analytics to Google Data Studio (Looker Studio) with Coupler.io

YouTube Studio is built for one creator looking at one channel, one tab at a time. The moment you manage several channels, need watch time next to subscriber churn, or want a sponsor to see last month's numbers without logging in, you are back to screenshots and CSV downloads. Coupler.io pulls YouTube Analytics into Google Data Studio on a timer, across every channel you pick, so the reporting lives in a shareable dashboard instead of in someone's browser history.

## How to export YouTube Analytics data to Google Data Studio

The wizard covers channel and video performance, subscriber movement, content and subscriber-type splits, traffic sources, and a fully custom report built from YouTube's own metrics and dimensions. Below is each screen in the order Coupler.io shows it.

### Step 1. Basic settings

- **Channels** — sign in with the Google account that owns or manages the channels, then tick the ones to include. Selecting several gives you a single data source covering your whole network.
- **Report type** — decides the shape of the data. Start with a ready-made report such as *Video detailed statistics*, or pick *Custom* to assemble your own from scratch. The full list is further down.

### Step 2. Report period

- **Start date** — the first day of data. The relative picker keeps it moving with you: *days ago*, *this month*, *last month*, *this year*, *last year*. Out of the box the flow looks back 60 days.
- **End date** — the last day of data. Leaving it on *today* means each refresh includes yesterday's uploads without anyone editing the flow.
- **Split data by period** — choose *Day* or *Month*. Daily rows suit trend lines and date range controls; monthly rows are tidier for sponsor recaps. Applies to the channel, subscriber, and video reports, not to *Traffic sources* or *Custom*.

### Step 3. Metrics and dimensions

- **Metrics** — only for the *Custom* report. Choose from grouped YouTube metrics: performance (*Views*, *Watch time (minutes)*, *Average view duration*), interactions (*Likes*, *Comments*, *Shares*, *Subscribers gained*, *Subscribers lost*), cards, playlists, audience retention, annotations, and YouTube Premium.
- **Dimensions** — also *Custom* only. Slice by *Country*, *Age*, *Gender*, *Device type*, *Video*, *Playlist*, *Insight traffic source type*, *Day*, *Month*, and more.
- **Additional dimensions** — extra breakdowns for the content-type, subscriber, and traffic source reports, such as *Creator content type*, *Subscribed status*, *Video*, or *Live or on demand*, depending on the report you picked.

### Step 4. Sorting options

- **Sorting column** — the column rows are ordered by when they arrive. Handy if a table chart should open with the most-watched video at the top.

### Step 5. Advanced settings

- **Video ID** — needed for audience retention analysis, which YouTube only returns for one specific video. Paste the ID from the video's URL.
- **Insight traffic source type** — YouTube requires this filter whenever you use the *Insight traffic source detail* dimension. Pick a type such as *YT_SEARCH*, *RELATED_VIDEO*, or *EXT_URL* to see the exact search terms, videos, or sites behind it.

### Step 6. Blend and transform data

- **Column management** — drop columns your dashboard won't chart, rename metric keys into words a sponsor understands, reorder fields, and adjust types.
- **Join** — line up two YouTube reports on a shared key, for instance video statistics against traffic sources by *Video*, so each video row carries where its views came from.
- **Append** — stack YouTube with TikTok Organic, Instagram Insights, or Facebook Page Insights for a single cross-platform content table.
- **Aggregate** — total views and watch time per channel, per week, or per content type before anything reaches the report.
- **Custom SQL** — when you need a calculation the other tools don't cover, write a query and Coupler.io loads its output.

### Step 7. Google Data Studio destination

Select Google Data Studio as the destination and Coupler.io creates a data source for you through its Google Data Studio connector. Authorization happens once, and both Coupler.io and Google Data Studio must be signed in with the **same Google account**; using one account for each is the usual reason the connector refuses to load.

- **Report / data source URL** — optional. Got a channel report in Google Data Studio you want to keep using? Enter the report or data source address (`https://datastudio.google.com/reporting/...`) and Coupler.io links the two, with a shortcut to that report on the flow page. No URL means a new data source.

Field types are read from the YouTube data itself, so *Day* lands as a real date your date range control can filter, and views or watch time arrive as numbers ready for scorecards. Charts come after the first successful run, and that same run is what makes the schedule available. Got a separate flow for traffic sources? Add it to the same report as a second data source.

### Step 8. Schedule

YouTube Analytics typically settles a day or two after the fact, so a daily refresh is the natural fit, though hourly, weekly, and monthly intervals exist too, with 15 minutes as the floor. Pick **replace** to keep a clean rolling window for the dashboard, or **append** to build a permanent history beyond what you query each time. On the report side, Google Data Studio holds a cached copy and refreshes it about every 12 hours; open the report menu and choose **Refresh data** when you want the newest numbers right away.

### Bonus: or just ask the AI Agent to build it for you

There's an AI Agent built into Coupler.io, in the right-hand sidebar. Describe the channel dashboard you're after:

> *"Set up a flow with daily YouTube channel statistics for all my channels over the last 90 days — views, watch time, average view duration, subscribers gained and lost — and send it to Google Data Studio so I can build a channel performance dashboard."*

It chooses the report type, sets the period and split, and prepares the Google Data Studio destination. What remains for you:

1. **Connect YouTube** — the Google sign-in for your channels is yours to do.
2. **Choose the channels** — decide which ones belong in this report.
3. **Authorize the Google Data Studio connector** — with the same Google account you used in Coupler.io.
4. **Point the flow at a report** — paste an existing report or data source URL, or let Coupler.io create a fresh data source.

Once the first run completes, open Google Data Studio and lay out your charts.

## What data can you export from YouTube Analytics to Google Data Studio with Coupler.io?

There are seven report types, and each flow carries one of them. Need channel totals beside traffic sources? Coupler.io's **Join** and **Append** merge them inside the flow, so Google Data Studio gets a single combined data source. If you'd rather keep them apart, add each flow as its own data source and blend them in the report.

- **Channel detailed statistics** — the channel's vital signs per day or month: views, watch time, average view duration, likes, comments, shares, and subscriber gains and losses. The backbone of any channel overview.
- **Channel statistics by content and subscriber type** — the same channel numbers split by content type (videos, Shorts, live streams) and by whether the viewer is subscribed. Shows which format actually grows the audience.
- **Channel subscribers** — subscriber movement over time, with optional breakdowns by content type or video, so you can see which uploads earned followers and which lost them.
- **Video detailed statistics** — per-video performance for your selected period. The default report and the one most video leaderboards are built on.
- **Video statistics by content and subscriber type** — video-level numbers broken down by format and subscriber status, useful for comparing how loyal viewers and newcomers respond to each upload.
- **Traffic sources** — where views come from: YouTube search, suggested videos, external sites, playlists, channel pages, and ads. Add *Video* as a dimension to see the mix per upload.
- **Custom** — build a report from YouTube's metric and dimension catalog yourself, including audience retention, cards, playlists, demographics, devices, geography, and YouTube Premium watch time.

## Why export YouTube Analytics to Google Data Studio — real life cases

Here is what channel owners, agencies, and marketing teams put on their Google Data Studio reports once YouTube data refreshes itself.

- **Network overview for a multi-channel brand**

  Brands with regional or product channels rarely see them side by side in YouTube Studio. A single flow covering every channel feeds a Google Data Studio page with a channel filter, scorecards for *Views*, *Watch time (minutes)*, and net subscribers, and a time series for each. The monthly content review starts from one link instead of five logins.

- **Sponsor and brand-deal recaps**

  Creators owe sponsors proof that an integration delivered. Filter the *Video detailed statistics* data to the sponsored upload, show views, *Average view percentage*, likes, and comments in a clean one-page report, and share it as a view-only link. Google Data Studio's scheduled email delivery can send the recap a week and a month after publishing without you lifting a finger.

- **Shorts versus long-form decisions**

  *Channel statistics by content and subscriber type* separates Shorts, regular videos, and live streams. A stacked bar of views and *Subscribers gained* by *Creator content type* answers the question every content planning meeting circles around: is the Shorts effort building the channel or just inflating view counts?

- **Discovery report for SEO-minded teams**

  Using *Traffic sources* with *Insight traffic source type* set to *YT_SEARCH*, the *Insight traffic source detail* dimension lists the search terms that bring people to your videos. A table chart sorted by views shows which titles and keywords to double down on, and a date range control reveals how new uploads shift the mix.

- **Subscriber churn watch**

  A falling net subscriber line is easy to miss in YouTube Studio. Chart *Subscribers gained* against *Subscribers lost* per day from *Channel subscribers*, add the *Video* breakdown, and spikes in losses trace back to the exact upload that caused them. The community manager checks it every Monday.

- **Agency client reporting across many channels**

  Agencies running YouTube for several clients can append each client's flow into a templated Google Data Studio report with a client filter. Every client gets the same scorecards, trend lines, and top-video table, refreshed daily, and the account manager no longer spends the first week of the month exporting.

- **Audience demographics for media kits**

  A *Custom* report with *Age*, *Gender*, *Country*, and *Viewer percentage* produces the audience snapshot advertisers ask for. Keep it as a live page in Google Data Studio and the media kit is always current, rather than a PDF from last spring.

- **Content ROI next to the marketing calendar**

  Join video statistics to a Google Sheets content calendar inside Coupler.io so each row carries the campaign, topic, and production cost. In Google Data Studio, a scatter chart of cost against *Watch time (minutes)* tells the marketing lead which video formats earn their budget and which belong on the cut list.

## Other Google Data Studio integrations

Every other source you can land in Google Data Studio with the same no-code setup:

- [Connect Facebook Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-google-data-studio.md)
- [Connect Facebook Page Insights to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-page-insights-to-google-data-studio.md)
- [Connect Google Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-ads-to-google-data-studio.md)
- [Connect Google Analytics to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-analytics-to-google-data-studio.md)
- [Connect Google Search Console to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-search-console-to-google-data-studio.md)
- [Connect Instagram Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-instagram-ads-to-google-data-studio.md)
- [Connect Instagram Insights to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-instagram-insights-to-google-data-studio.md)
- [Connect LinkedIn Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-linkedin-ads-to-google-data-studio.md)
- [Connect LinkedIn Public Data to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-linkedin-public-data-to-google-data-studio.md)
- [Connect Microsoft Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-microsoft-ads-to-google-data-studio.md)
- [Connect QuickBooks to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-quickbooks-to-google-data-studio.md)
- [Connect Shopify to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-shopify-to-google-data-studio.md)
- [Connect TikTok Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-ads-to-google-data-studio.md)
- [Connect TikTok Organic to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-organic-to-google-data-studio.md)
- [Connect WooCommerce to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-google-data-studio.md)
- [Connect Xero to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-google-data-studio.md)
