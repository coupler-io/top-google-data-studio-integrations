---
title: Connect Facebook Page Insights to Google Data Studio with Coupler.io
slug: connect-facebook-page-insights-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-page-insights-to-google-data-studio.md
source: Facebook Page Insights
destination: Google Data Studio
meta_title: Connect Facebook Page Insights to Google Data Studio with Coupler.io
meta_description: Send Facebook Page performance, follower snapshots, post, reel, and video stats to Google Data Studio on a schedule. Organic social reports that update.
---

![Facebook Page Insights](https://static.coupler.io/importers/facebook.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect Facebook Page Insights to Google Data Studio (Looker Studio) with Coupler.io

Meta Business Suite shows a Page's numbers well enough for one person looking at one Page, but it was never meant to feed a shared report, and Google Data Studio has no native Facebook Page connector from Google. That leaves social teams copying figures by hand every month. Coupler.io pulls Page performance, follower snapshots, and post, reel, and video statistics for every Page you manage into a Google Data Studio data source that refreshes on its own.

## How to export Facebook Page Insights data to Google Data Studio

Coupler.io covers Page-level overview and performance data, daily follower breakdowns, and lifetime or daily statistics for posts, reels, and videos. These are the wizard screens, in order.

### Step 1. Basic settings

- **Pages** — tick the Facebook Pages to report on. Choose several and they share one data source, which makes a brand portfolio or multi-location view easy.
- **Report type** — picks what each row describes: the Page, a day of Page activity, a post, a reel, or a video. The six options are listed further down.

### Step 2. Report period

- **Start date** — for Page performance, follower snapshot, and video daily reports. Pick a relative value like *days ago*, *this month*, *last month*, *this year* or *last year* and the period rolls forward on every refresh.
- **End date** — the end of the window, *today* by default so the data stays current.
- **Created after** — for post and reel reports. Only content published after this date is included.
- **Created before** — for post and reel reports. Leave it empty to include everything up to now.
- **Split data by period** — for **Page: performance insights** only. *Daily* for trends, *Monthly* for a compact overview.

### Step 3. Metrics

- **Metrics** — the numbers to export, grouped by theme. Page reports offer Page views, New followers, Lifetime followers, Posts engagements, Content views - total, Unique content viewers, and video metrics. Post reports offer Post views - total, Unique post viewers, Clicks, Likes, Comments, Shares, and Reactions. Reel reports add Views, Average view time (ms), and Audience retention. Video reports cover Video views, Video view time, and Ad break earnings.

### Step 4. Metrics and dimensions

- **Metrics and dimensions** — for **Page: general overview**, pick Page attributes such as About, Website URL, Overall star rating, Rating count, Page likes, and Followers. For **Page: followers daily snapshot**, choose a single breakdown: Unique followers by city or Unique followers by country.

### Step 5. Advanced filters

- **Created after** — for **Post: video daily performance**. Only videos published after this date.
- **Created before** — for **Post: video daily performance**. Only videos published before this date.

### Step 6. Advanced settings

- **Post columns** — for **Post: posts lifetime performance**. Choose descriptive columns such as Message, Attachments, Created time, Posted by, and Permalink URL, or leave it empty to get them all.
- **Data behavior** — for the general overview, post, and reel reports. *Latest data* keeps current values only; *Track changes over time* saves a snapshot each day so you can chart how totals grow.

### Step 7. Blend and transform data

- **Column management** — hide unused fields, rename metrics into plain words for the report audience, and reorder or retype columns.
- **Join** — attach post statistics to Page data, or to ad data from Facebook Ads, on a shared key such as Page or post ID.
- **Append** — stack Instagram Insights or LinkedIn Company Pages rows under Facebook for one organic social data source.
- **Aggregate** — roll daily Page metrics up to weekly or monthly totals per Page.
- **Custom SQL** — a query of your own on the prepared data for anything more specialized.

### Step 8. Google Data Studio destination

- **Report / data source URL** — optional. Have a Page performance report you want to keep? Put its Google Data Studio address here (it starts `https://datastudio.google.com/reporting/...`, for a report or a data source) and the flow will point at it, reachable straight from Coupler.io.

Once you choose Google Data Studio, Coupler.io sets up a data source for you through its Google Data Studio connector. You give permission in Google Data Studio and Coupler.io a single time, using the **same Google account** in both; a mismatch there is behind most failed connections. Types come from the data, so the date field drives date range controls without tweaking and engagement counts arrive as numbers. The flow has to complete one run before the data source is ready for charts and before you can schedule it. Separate flows for Page metrics and post statistics can both feed one report.

### Step 9. Schedule

Refresh as often as every 15 minutes, or hourly, daily, weekly, or monthly. Replace swaps in a clean copy on every run, which suits nearly every Page dashboard; append keeps adding rows when you want a permanent log. Keep in mind that Google Data Studio holds a cached copy for up to 12 hours by default. Hit **Refresh data** in the report menu whenever you need the freshest numbers on screen.

### Bonus: or just ask the AI Agent to build it for you

Open the Coupler.io AI Agent from the right sidebar and describe what you need:

> *"Export lifetime performance for all posts published on my Facebook Pages this year, with post views, unique viewers, clicks, reactions, comments, and shares plus the message and permalink, and send it to Google Data Studio for a top posts dashboard."*

The Agent fills in the report type, dates, metrics, and post columns. You still do these yourself:

1. **Connect Facebook** — the Meta sign-in stays with you.
2. **Pick the Pages** — you decide which Pages are included.
3. **Authorize Google Data Studio** — approve the Coupler.io connector with your Google account.
4. **Choose the target** — paste the URL of an existing Google Data Studio report or let Coupler.io create a fresh data source.

With the first run complete, open Google Data Studio and build your charts.

## What data can you export from Facebook Page Insights to Google Data Studio with Coupler.io?

Six report types are available, and each flow exports one of them. Coupler.io's **Join** and **Append** can merge Page-level and post-level data into one data source before it reaches Google Data Studio; the alternative is to add each as its own data source and blend them in the report.

- **Page: general overview** — a profile card for each Page: about text, website, contact details, star rating, Page likes, and followers. Great for a portfolio summary across many Pages.
- **Page: performance insights** — daily or monthly Page activity: views, new followers, content views, engagements, reactions, and video views. The heart of any organic Facebook dashboard.
- **Page: followers daily snapshot** — unique followers by city or by country each day, so you can see where your audience lives and how that shifts.
- **Post: posts lifetime performance** — every post with its views, clicks, reactions, comments, and shares, plus message text and permalink for context.
- **Post: reels lifetime performance** — reels with views, unique views, view time, audience retention, follows, and reactions.
- **Post: video daily performance** — day-by-day views, view time, and ad break earnings for each video.

## Why export Facebook Page Insights to Google Data Studio — real life cases

Organic Facebook still matters to local businesses, publishers, and community brands, and it deserves a report people actually open. These are the ones worth building.

- **Monthly organic social report for leadership**

  A Google Data Studio page with scorecards for New followers, Posts engagements, and Content views - total, compared with the previous month, plus a trend line. It replaces the monthly slide someone assembled from Meta Business Suite screenshots, and with scheduled email delivery it arrives in the inbox on the first of the month.

- **Top posts leaderboard for the content team**

  Build a table from Post: posts lifetime performance sorted by Reactions or Shares, with Message and Permalink URL so anyone can click straight through to the post. Add a date range control on Created time and the weekly content meeting starts with what worked instead of who remembers what.

- **Multi-location or franchise Page comparison**

  Pull every location's Page into one flow and add a Page filter. Bar charts of Page views and New followers by location show which branches run an active Page and which need help. Regional managers each get a bookmarked view of their own stores.

- **Reels performance tracker**

  Post: reels lifetime performance gives Views, Average view time (ms), and Audience retention per reel. A scatter chart of views against retention in Google Data Studio separates reels that were seen from reels that were watched. Video producers use it to plan length and hook style for the next batch.

- **Audience geography dashboard**

  Page: followers daily snapshot with Unique followers by country drives a Google Data Studio geo chart and a country table. Marketing teams use it to decide posting times, languages, and which markets to target with paid boosts.

- **Publisher video monetization report**

  For Pages earning from in-stream ads, Post: video daily performance includes Ad break impressions, Ad break earnings, and Ad break CPM. A daily earnings chart with a video filter tells the editorial team which formats pay and lets finance forecast monthly revenue without exporting files.

- **Client reporting for social media agencies**

  Agencies that manage organic Pages for clients can connect each client's Pages, filter by Page, and share a view-only Google Data Studio link per client. With Track changes over time enabled on the overview report, the same dashboard shows Page likes and Followers growth month after month without any manual logging.

- **Organic and paid side by side**

  Join Page: performance insights with Facebook Ads data by date in Coupler.io and build one Google Data Studio report where organic reach and paid reach sit next to each other. It answers the familiar question of whether boosted posts are lifting organic engagement or simply replacing it.

## Other Google Data Studio integrations

Every other source you can land in Google Data Studio with the same no-code setup:

- [Connect Facebook Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-google-data-studio.md)
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
- [Connect YouTube Analytics to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-google-data-studio.md)
