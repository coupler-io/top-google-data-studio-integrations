---
title: Connect TikTok Ads to Data Studio with Coupler.io
slug: connect-tiktok-ads-to-looker-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-ads-to-looker-studio.md
source: TikTok Ads
destination: Data Studio
meta_title: Connect TikTok Ads to Data Studio with Coupler.io
meta_description: Load TikTok Ads campaign, ad group, audience, GMV Max, Playable and DSA reports into Data Studio on autopilot. Live TikTok dashboards, no CSVs.
---

![TikTok Ads](https://static.coupler.io/importers/tiktok.svg) → ![Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect TikTok Ads to Data Studio with Coupler.io

TikTok Ads Manager is built for launching campaigns quickly, not for sharing results: custom reports live inside the platform, exports come out as one-off files, and there is no Google-built connector that brings TikTok into Data Studio (formerly Looker Studio). Coupler.io closes that gap. It pulls campaign, ad group, ad, audience, GMV Max, Playable, and Dynamic Showcase Ads reports from all your advertiser accounts into a Data Studio data source that refreshes itself.

## How to export TikTok Ads data to Data Studio

You can bring in performance reports at four levels (advertiser, campaign, ad group, ad), audience breakdowns, TikTok Shop GMV Max results, Playable Ad engagement, catalog-driven DSA reports, and plain lists of campaigns and ads. Here is what each wizard screen asks for.

### Step 1. Basic settings

- **Report type** — the shape of your data source. Choose the level and flavor of report you need; the screens that follow change to match it. All 18 options are explained further down.
- **Ad accounts** — select the TikTok advertiser accounts to include. Several accounts merge into one data source, which saves agencies from building a flow per client brand. If an account is missing, reconnecting TikTok in Coupler.io's Connections usually brings it back.
- **Stores** — appears for **GMV Max campaign report** only. Choose the TikTok Shop stores whose campaigns you want.

### Step 2. Report period

- **Start date** — where the data begins. Use a relative setting like *days ago*, *this month*, *last month*, *this year* or *last year* and the window moves forward with every refresh. Not used by the **Campaigns** and **Ads** lists, which export the current state.
- **End date** — where the data stops. *Today* keeps each run up to date.
- **Split data by period** — *Daily*, *Hourly*, or *Totals only* for basic and GMV Max reports; *Daily* or *Totals only* for audience and DSA reports. Daily is what you want for any trend chart.

### Step 3. Metrics and dimensions

- **Metrics** — the columns in your data source. Defaults cover Reach, Impressions, Clicks (destination), Conversions, and Cost; add CPM, CTR, Cost per result, Video views at 25%, 50%, 75% and 100%, Average play time per video view, Paid likes, Paid follows, app install and purchase value metrics, and many more.
- **Audience dimensions** — for audience reports. Break results down by Gender, Age, Country code, Province, DMA region, Language, Platform, Placement, Interest category, and other attributes.
- **DSA dimensions** — for Dynamic Showcase Ads reports. Group by Catalog id, Product set id, Product id, or Sku id.
- **Targeting dimension** — optional on basic reports. Split results by Country code or Ad type.
- **Asset dimension** — optional on basic reports. Group by assets such as Video material id, Image id, Post id, or Page id to see which creative pieces earned their spend.
- **Search dimension** — optional on basic reports. Add Search terms to see what people typed before they saw your search ads.

### Step 4. Advanced settings

- **Advanced filters** — narrow the result to a property and value, such as one campaign or one objective. Not available for the **Ads** list and the GMV Max report.

### Step 5. Blend and transform data

- **Column management** — keep the dozen columns your dashboard actually uses, rename TikTok's technical field names, and set the right types.
- **Join** — combine an ad-level performance report with the **Ads** list on Ad id, so every row carries the ad name and status.
- **Append** — stack Meta, Google Ads, Snapchat, or Pinterest rows under TikTok for one paid social table.
- **Aggregate** — turn hourly or daily rows into weekly campaign totals.
- **Custom SQL** — write your own query on the prepared data for calculations nothing else covers.

### Step 6. Data Studio destination

- **Report / data source URL** — optional. Running a TikTok spend report in Data Studio already? Paste its link, or the link of its data source (`https://datastudio.google.com/reporting/...`), and Coupler.io keeps the flow attached to that report so it's one click away. Leave it blank for a new data source.

Behind the scenes, picking Data Studio makes Coupler.io build a data source via the Coupler.io connector for Data Studio. Grant access in both apps using one and the **same Google account**; signing in with a personal account on one side and a work account on the other is what breaks most first attempts. Coupler.io infers types from the values, so dates are real dates that respond to date controls and Cost or CTR stay numeric. Let the flow finish one run first: only then can you build on the data source and turn on the schedule. You can also attach several TikTok flows, for example campaign and audience reports, to the same report as separate data sources.

### Step 7. Schedule

Set the refresh to every 15 minutes, hourly, daily, weekly, or monthly. Replace mode overwrites the data on each run and suits most dashboards; append mode adds rows and is useful when you want to keep a record TikTok will not keep for you. Data Studio caches what it reads and only rechecks every 12 hours by default, so after a fresh Coupler.io run, use **Refresh data** from the report menu to see it immediately.

### Bonus: or just ask the AI Agent to build it for you

Open the AI Agent from the right sidebar in Coupler.io and describe the TikTok dashboard in plain words:

> *"Get a daily TikTok Ads basic ad group report for the last 60 days with cost, impressions, clicks, conversions, CPM, and video views at 100% across all my advertisers, and connect it to Data Studio for a creative performance dashboard."*

The Agent picks the report type, dates, split, and metrics for you. Your part is short:

1. **Connect TikTok Ads** — signing in to TikTok for Business is always yours to do.
2. **Choose the advertiser accounts** (and stores, for GMV Max) — you decide what is in scope.
3. **Authorize the Data Studio connector** — with your Google account.
4. **Say where it goes** — paste an existing Data Studio report URL or let a new data source be created.

Then open Data Studio and design the charts on that data source.

## What data can you export from TikTok Ads to Data Studio with Coupler.io?

You can choose from 18 report types, one per flow. Most TikTok dashboards use two or three, typically a performance report, an audience report, and the Ads list. Coupler.io's **Join** and **Append** merge those into a single data source on the way in; blending them inside Data Studio remains an option if you would rather keep them apart.

- **Basic campaign report** — spend, reach, clicks, conversions, and cost per result per campaign, the default for a top-level TikTok dashboard.
- **Basic ad group report** — the same metrics by ad group, where targeting, bidding, and placement choices are made.
- **Basic ad report (Upgraded Smart+ by ad)** — performance per ad, with Upgraded Smart+ results kept at the ad (asset group) level.
- **Basic ad report (Upgraded Smart+ by creative)** — performance per ad, with Upgraded Smart+ results split down to individual creatives.
- **GMV Max campaign report** — TikTok Shop GMV Max campaigns with Gross revenue, Orders (SKU), Cost per order, Net cost, and ROI.
- **Campaigns** — a current list of campaigns with their settings, handy as a lookup table for names and budgets.
- **Ads** — a current list of ads with their attributes, the natural join partner for ad-level reports.
- **Basic advertiser report** — one line per advertiser account, ideal for a multi-account summary.
- **Audience campaign report** — campaign results broken down by audience dimensions such as age, gender, or region.
- **Audience advertiser report** — account-level results by audience.
- **Audience ad report** — ad-level results by audience, to see which creative works for which group.
- **Audience ad group report** — each ad group broken out by audience segment, closest to how targeting is set up.
- **Playable Ad report** — engagement with interactive Playable ads: scene views, CTA clicks, app installs.
- **Playable Ad report by country** — that interactive engagement, broken out market by market.
- **Dynamic Showcase Ads (DSA) campaign report** — catalog ad results per campaign, by product, SKU, or product set.
- **Dynamic Showcase Ads (DSA) report** — catalog ad results per ad.
- **Dynamic Showcase Ads (DSA) advertiser report** — catalog ad results per advertiser account.
- **Dynamic Showcase Ads (DSA) ad group report** — catalog ad results per ad group.

## Why export TikTok Ads to Data Studio — real life cases

TikTok moves fast, and reporting that waits for someone to export a file falls behind within days. Here is what teams put in front of their stakeholders instead.

- **Daily TikTok spend and results board**

  A single Data Studio page with scorecards for Cost, Conversions, and Cost per result, a daily line chart, and a campaign table sorted by spend. The paid social manager checks it each morning and the head of marketing has the same link, so nobody needs a login to Ads Manager to know how yesterday went.

- **Creative fatigue monitor**

  Use the Basic ad report with Video views at 25%, 50%, 75% and 100% and Average play time per video view, joined to the Ads list for names. A Data Studio line chart of CTR per ad over the last 30 days shows exactly when a video starts wearing out. Creative teams get a clear signal to brief the next round before CPA climbs.

- **Audience breakdown for media planning**

  The Audience ad group report split by Age, Gender, and Placement turns into Data Studio bar charts of Conversions and cost per conversion by segment. Planners use it to decide where to tighten targeting, and it replaces the manual pivot table that someone rebuilt every month from an export.

- **TikTok Shop revenue dashboard**

  For sellers running GMV Max, a dashboard built on the GMV Max campaign report shows Gross revenue, ROI, and Cost per order by store and campaign. Add a store filter and a date range control and the ecommerce lead can answer "is TikTok profitable this month?" without waiting for finance.

- **Agency client reporting across advertiser accounts**

  Select every client advertiser in one flow, add an advertiser filter control in Data Studio, and give each client a bookmarked view. Data Studio's scheduled email delivery sends the PDF every Monday, which takes the weekly TikTok screenshot round-up off the account team's plate.

- **Paid social mix review**

  Append TikTok with Meta and other ad platforms in Coupler.io so one Data Studio report compares Cost, Impressions, and Conversions by channel side by side. Leadership sees whether TikTok's cheaper CPM actually turns into cheaper conversions, which is the question that decides next quarter's budget split.

- **Mobile game and app install tracking**

  Combine the Playable Ad report by country with app install metrics from the basic reports. Data Studio geo maps of App install and Cost per app install show which markets respond to interactive ads. User acquisition teams use it to choose where to scale playables and where to stick to video.

- **Catalog ads performance by product**

  The Dynamic Showcase Ads (DSA) campaign report split by Product id and Sku id feeds a Data Studio table of the products TikTok promotes most and what they return. Merchandisers spot heroes and duds, and the team can exclude low performers from the product set instead of guessing.

## Other Data Studio integrations

Every other source you can land in Data Studio with the same no-code setup:

- [Connect Facebook Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-looker-studio.md)
- [Connect Facebook Page Insights to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-page-insights-to-looker-studio.md)
- [Connect Google Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-ads-to-looker-studio.md)
- [Connect Google Analytics to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-analytics-to-looker-studio.md)
- [Connect Google Search Console to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-search-console-to-looker-studio.md)
- [Connect Instagram Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-instagram-ads-to-looker-studio.md)
- [Connect Instagram Insights to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-instagram-insights-to-looker-studio.md)
- [Connect LinkedIn Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-linkedin-ads-to-looker-studio.md)
- [Connect LinkedIn Public Data to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-linkedin-public-data-to-looker-studio.md)
- [Connect Microsoft Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-microsoft-ads-to-looker-studio.md)
- [Connect QuickBooks to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-quickbooks-to-looker-studio.md)
- [Connect Shopify to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-shopify-to-looker-studio.md)
- [Connect TikTok Organic to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-organic-to-looker-studio.md)
- [Connect WooCommerce to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-looker-studio.md)
- [Connect Xero to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-looker-studio.md)
- [Connect YouTube Analytics to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-looker-studio.md)
