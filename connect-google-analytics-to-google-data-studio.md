---
title: Connect Google Analytics to Google Data Studio with Coupler.io
slug: connect-google-analytics-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-analytics-to-google-data-studio.md
source: Google Analytics 4 (GA4)
destination: Google Data Studio
meta_title: Connect Google Analytics to Google Data Studio with Coupler.io
meta_description: Bring GA4 sessions, channels, landing pages, key events, ecommerce and ad metrics into Google Data Studio from many properties. Faster, steadier dashboards.
---

![Google Analytics](https://static.coupler.io/importers/google-analytics.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect Google Analytics to Google Data Studio (Looker Studio) with Coupler.io

Google's own GA4 connector for Google Data Studio queries Analytics live every time someone opens or filters a chart. On a busy report that burns through the property's API quota, charts stall with quota errors, and combining several properties means juggling one data source per property. Coupler.io takes a different route: it pulls the GA4 metrics and dimensions you pick, across as many properties as you need, on a schedule, and gives Google Data Studio a ready data source to read from, so the dashboard is no longer at the mercy of live quota.

## How to export Google Analytics data to Google Data Studio

GA4 has no report-type menu in Coupler.io: you build each flow from metrics and dimensions. Typical builds cover traffic and engagement, acquisition channels, pages and landing pages, key events, ecommerce, advertising, and audience or device breakdowns. Three setup steps get you there.

### Step 1. Basic settings

- **Properties** — the GA4 properties to read from, listed from every account your Google login can see. Select several, or a whole account group at once, and one flow reads from every property you ticked.

### Step 2. Report period

- **Start date** — the first day of data. Go relative, whether that is *this year*, *last year*, *this month*, *last month* or some number of *days ago*, and the period rolls on by itself with every run. It starts at 60 days ago unless you change it. For a full trailing year behind a year-over-year view, `{{365daysago}}` does the job.
- **End date** — the final day included; it defaults to today so each run brings the latest numbers.

### Step 3. Metrics and dimensions

- **Metrics** — what you are counting, up to 10 per flow. Views, Total users, New users, Event count and Key events are preselected, and the list loads from your chosen properties. Need more than ten? Split them across two flows and join them back together in the next step.
- **Dimensions** — how the numbers are broken down, up to 9 per flow. Date is preselected; add things like Session default channel group, Landing page, Device category or Country.

### Step 4. Blend and transform data

- **Column management** — hide GA4 fields the dashboard ignores, give API-style names a readable label, reorder and set types.
- **Join** — merge two GA4 flows on Date and shared dimensions to get past the ten-metric cap, or join GA4 landing pages to Google Search Console pages.
- **Append** — combine flows from separate properties or from older exports into one continuous set of rows.
- **Aggregate** — roll daily rows into weekly or monthly figures per property or channel.
- **Custom SQL** — calculate anything the GA4 interface does not offer, such as revenue per engaged session, with a query on the combined data.

### Step 5. Google Data Studio destination

Here the destination is Google Data Studio, and the flow becomes a data source by way of Coupler.io's Google Data Studio connector. Access is granted once, to Google Data Studio and to Coupler.io, and the Google account has to match on both sides. Mixing a personal and a work account is where most GA4 setups go wrong.

- **Report / data source URL** — optional. Moving an existing GA4 dashboard over? Paste the address of that report or of its data source (the `https://datastudio.google.com/reporting/...` kind). The flow is tied to it, and Coupler.io opens it for you instead of starting from scratch.

Coupler.io reads the types straight from the GA4 rows: Date arrives as a date, so a date range control filters it properly, and metrics like Sessions or Purchase revenue arrive as numbers. Building the report and turning on the schedule both wait until the flow has completed one run. You can feed one report from several flows; each shows up as a separate data source.

### Step 6. Schedule

Refresh as frequently as every 15 minutes, or go hourly, daily, weekly or monthly; daily is plenty for most GA4 reporting. Each run can either replace the data, giving a clean picture of the current period, or append to it, building a running record. Google Data Studio refreshes its own cache on a cycle, every 12 hours by default, so choose **Refresh data** from the report menu if you want the newest run to show immediately.

### Bonus: or just ask the AI Agent to build it for you

Describing the dashboard is often quicker than picking ten metrics from a list of a hundred. The Coupler.io AI Agent, docked in the app's right-hand sidebar, takes a request like this:

> *"Create a GA4 flow for all our properties with Sessions, Engaged sessions, Engagement rate, Key events and Purchase revenue by Date, Session default channel group and Landing page for the last 90 days, and send it to Google Data Studio for a weekly marketing dashboard."*

The Agent picks the metrics and dimensions, sets the date window and prepares the destination. You still do these yourself:

1. **Connect Google Analytics** — you sign in with your own Google account.
2. **Choose the properties** — only you know which ones belong in the report.
3. **Let the Google Data Studio connector in** — signing in on that very Google login.
4. **Tell it where the data goes** — the link of a GA4 report you already run, or nothing at all, in which case a new data source appears.

When the first run finishes, the chart building happens in Google Data Studio.

## What data can you export from Google Analytics to Google Data Studio with Coupler.io?

GA4 in Coupler.io has no report-type parameter; every flow is a free combination of up to 10 metrics and 9 dimensions. The nine categories below are an editorial grouping we made to help you find things. They are not options in the wizard, but every name in them is a real metric or dimension label from the connector. Any one flow can mix labels from several groups. To bring more groups together than one flow allows, Coupler.io's Join and Append merge flows before they reach Google Data Studio; leaving them apart and blending them later inside the Google Data Studio report also works.

- **Users and engagement** — the size and quality of your traffic: Total users, New users, Active users, 7-day active users, Sessions, Engaged sessions, Engagement rate, Average session duration, User engagement, Bounce rate and DAU / MAU. The top row of almost every GA4 dashboard.
- **Traffic acquisition** — where visitors came from: Session default channel group, Session source / medium, Session campaign, First user source / medium and First user default channel group. Answers which channels bring people in and which bring them back.
- **Pages and content** — what people looked at: Page path, Page title, Landing page, Landing page + query string, Content group, Views, Views per session, Percent scrolled and Scrolled users.
- **Events and key events** — what people did: Event name, Event count, Event value, Key events, Is key event, Session key event rate and User key event rate. This is where conversion reporting lives.
- **Ecommerce and items** — the store side: Item name, Item category, Item brand, Transaction ID, Order coupon, Ecommerce purchases, Add-to-carts, Checkouts, Item revenue, Purchase revenue, Refund amount and Cart-to-view rate.
- **Advertising and ad platforms** — paid media as GA4 sees it: Google Ads campaign, Google Ads keyword text, Ads cost, Ads clicks, Ads cost per click, Cost per key event and Return on ad spend, plus CM360, DV360 and SA360 dimensions and publisher fields like Total ad revenue.
- **Organic Google Search** — search figures from a linked Search Console property: Organic google search clicks, Organic google search impressions, Organic google search click through rate and Organic google search average position.
- **Audience, location and technology** — who and on what: Country, Region, City, Language, Age, Gender, Interests, Device category, Browser, Operating system and Platform.
- **Time and cohorts** — how to slice the calendar: Date, Date + hour (YYYYMMDDHH), Day of week name, Week, Year month, ISO week of ISO year, First session date, Cohort and Weekly cohort.

## Why export Google Analytics to Google Data Studio — real life cases

The dashboards below are the ones GA4 users build most often once the data stops fighting them.

- **Channel performance dashboard for the marketing lead**

  A time series of Sessions and Key events split by Session default channel group, with an Engagement rate table underneath, tells the marketing lead which channels are carrying the month. A date range control set to compare with the previous period makes Monday's "what changed?" question a two-second read, and it replaces the weekly GA4 export that someone used to paste into slides.

- **Landing page audit for SEO and content**

  Landing page with Sessions, Engagement rate, Bounce rate and Key events, shown as a Google Data Studio table with heatmap coloring, highlights pages that attract traffic but lose it. The content team works down the list each sprint. Join in Google Search Console data in Coupler.io and the same table shows which of those pages rank for queries that convert poorly.

- **Merchandising report for the ecommerce team**

  Item name and Item category against Items viewed, Add-to-carts, Cart-to-view rate and Item revenue show which products get looked at but not bought. Category managers filter by Item brand, spot the weak product pages, and bring the list to the weekly trading meeting instead of guessing from total sales.

- **Paid traffic measured on-site, not just in the ad platform**

  GA4's Ads cost, Return on ad spend and Cost per key event by Google Ads campaign give one view of Google Ads. For the other networks, Coupler.io joins Facebook Ads or LinkedIn Ads spend to GA4 Session campaign rows, so a single Google Data Studio table puts every campaign's cost next to the sessions and key events it actually produced on the site.

- **One client report per property for agencies**

  Agencies select every client property under **Properties** in one flow, then give each client a Google Data Studio report filtered to their property that they can open but not edit. A monthly email schedule in Google Data Studio mails it out without anyone remembering to, and because charts read the data Coupler.io already loaded, a client clicking around does not trigger quota errors.

- **Organic search next to on-site behavior**

  Organic google search clicks and Organic google search average position sit beside Landing page and Engaged sessions in one chart, so the SEO team sees not just how a page ranks but whether searchers stay. Pages with strong positions and weak engagement go on the rewrite list.

- **Product and retention health for app and SaaS teams**

  DAU / MAU, 7-day active users, New / returning and Weekly cohort feed a retention view the product team checks every sprint review. Line charts show whether stickiness is improving after a release, and a filter on Platform separates web from app without rebuilding anything.

- **Year-over-year executive summary**

  Start date set to `{{365daysago}}` and Year month as the dimension give a twelve-month view of Total users, Transactions and Total revenue. Leadership opens a single page of scorecards with comparison to the same period last year, and the quarterly business review no longer starts with an analyst rebuilding the numbers.

## Other Google Data Studio integrations

Every other source you can land in Google Data Studio with the same no-code setup:

- [Connect Facebook Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-google-data-studio.md)
- [Connect Facebook Page Insights to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-page-insights-to-google-data-studio.md)
- [Connect Google Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-ads-to-google-data-studio.md)
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
