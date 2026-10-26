---
title: Connect Google Ads to Google Data Studio with Coupler.io
slug: connect-google-ads-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-ads-to-google-data-studio.md
source: Google Ads
destination: Google Data Studio
meta_title: Connect Google Ads to Google Data Studio with Coupler.io
meta_description: Bring Google Ads campaign, keyword, search query, geo, and asset group reports into Google Data Studio, cleaned and combined, on a refresh schedule you control.
---

![Google Ads](https://static.coupler.io/importers/googleadv.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect Google Ads to Google Data Studio (Looker Studio) with Coupler.io

Google Data Studio does ship a built-in Google Ads connector, but it stops at a fixed field list per data source, it can't place other ad platforms or your CRM in the same table, and large accounts often make charts crawl while they query live. Coupler.io takes a different route: it pulls exactly the Google Ads report you choose, across as many accounts as you need, reshapes and combines it before delivery, and keeps a stored copy fresh on a schedule so the report opens quickly.

## How to export Google Ads data to Google Data Studio

The wizard covers performance reports at the account, campaign, ad group, ad, keyword, and asset group level; audience, demographic, and geographic cuts; search terms, landing pages, placements, and shopping; plus account structure, settings, and reference lists. When none of those fit, a Custom GAQL query is available too. It takes two short screens before the shared transformation, destination, and schedule steps.

### Step 1. Basic settings

- **Ad accounts** — pick one or more of the active accounts your Google login can see. Rows from every selected account land together, which is how an agency builds one MCC-wide report.
- **Report type** — the data category for this flow. Campaign performance is the default; the full catalogue sits further down, grouped the way the wizard groups it.
- **Custom GAQL** — appears only when the report type is **Custom GAQL**. Draft the query in Google's Query Builder, paste it here, and Coupler.io runs it as written.

### Step 2. Report period

This step applies to the performance reports. Account structure lists, settings, constants, and Custom GAQL skip it.

- **Start date** — where the data begins, 60 days back by default. Choose a relative value like *days ago*, *this month*, *last month*, *this year*, or *last year* so the range moves with the calendar. Seasonal comparisons that need a full year can use `{{365daysago}}`.
- **End date** — where the data stops, today by default, so each refresh adds the newest day.
- **Split data by periods** — one or several time columns: Date, Day of week, Week, Month, Quarter, or Year. Keywords performance offers every option except Day of week, and Click performance is available by Date only.

### Step 3. Blend and transform data

- **Column management** — drop columns the report won't chart, rename API-style keys into plain words, reorder, and fix data types.
- **Join** — connect the report to another dataset on a common key, for example campaign name against CRM opportunities or ad group ID against a list of ad groups.
- **Append** — place Microsoft Ads, Facebook Ads, or LinkedIn Ads rows under the Google Ads ones to get a single paid-media data source.
- **Aggregate** — total up daily keyword rows into weekly or monthly figures per campaign to keep the data source compact.
- **Custom SQL** — query the prepared data directly when you need logic the other tools can't express.

### Step 4. Google Data Studio destination

Select Google Data Studio and Coupler.io creates the data source through its Google Data Studio connector — nothing to configure field by field. Authorize Coupler.io and the connector once, and do it under the **same Google account**; it's tempting to reuse whichever login holds the Google Ads access, but if it differs from your Coupler.io login the connection fails.

- **Report / data source URL** — optional. Got an existing report or data source? Paste its address (`https://datastudio.google.com/reporting/...`) and the flow stays linked to it, opening it from Coupler.io in one click, rather than generating a new one.

Coupler.io works out column types from the incoming values, so Date is a date dimension, Cost and Clicks are numbers, and the date range control behaves as expected. You'll need one successful run before building the report and before the schedule can be switched on. Running several flows, say campaigns and search queries? Each becomes its own data source in the same report.

### Step 5. Schedule

The flow can refresh every 15 minutes at its fastest, or hourly, daily, weekly, or monthly. Choose replace if you want each run to deliver a clean current snapshot, which is what most performance dashboards need, or append if you want rows to build up as a history. Google Data Studio also caches what it reads and refreshes that cache roughly every 12 hours by default, so after a fresh run use **Refresh data** in the report's menu to see the update straight away.

### Bonus: or just ask the AI Agent to build it for you

The Coupler.io AI Agent sits in the right sidebar of the app. Tell it what the dashboard should show:

> *"Create a Google Ads to Google Data Studio flow with Keywords performance for all my client accounts, split by Week, covering this year, so I can build a keyword dashboard with a cost and conversions table per client."*

It selects the report type, the date settings, and the split, and gets the Google Data Studio destination ready. What's left for you:

1. **Connect Google Ads** — you sign in with your own Google login.
2. **Pick the ad accounts** — choose which accounts the flow covers.
3. **Authorize the Google Data Studio connector** — using the Google account tied to Coupler.io.
4. **Say where the data goes** — link an existing report or data source, or have a new one created.

Then build the charts in Google Data Studio.

## What data can you export from Google Ads to Google Data Studio with Coupler.io?

The Report type list holds 53 data categories in six groups. A flow carries one category at a time, and Coupler.io's **Join** and **Append** combine categories before anything reaches Google Data Studio — for instance, campaign performance with campaign budgets, or country, state, and region reports stacked together. You can still keep separate data sources and blend them inside the report if you prefer.

**Frequently Used**

- **Campaign performance** — daily cost, clicks, impressions, conversions, and conversion value per campaign; the base of most Google Ads dashboards.
- **Keywords performance** — clicks, cost, and conversions for each keyword in your search campaigns.
- **Ad group performance** — results per ad group, a step below campaigns.
- **Ad performance** — metrics per individual ad, for comparing copy and formats.
- **Asset group performance** — Performance Max asset group results.
- **Custom GAQL** — any query you write in Google Ads Query Language.

**Reports**

- **Account performance** — top-line totals per ad account.
- **Ad group audience performance** — how audience segments perform inside each ad group.
- **Ad group performance by country** — ad group results by country.
- **Ad group performance by state** — ad group results by state.
- **Ad group performance by region** — ad group results by region.
- **Ad group performance with install conversion** — ad group metrics including app install conversions.
- **Age range performance** — results by age bracket.
- **Campaign audience performance** — audience segment results at campaign level.
- **Campaign performance by ad network type** — Search, Search partners, Display, YouTube, and other networks side by side.
- **Campaign performance by country** — campaign results by country.
- **Campaign performance by state** — campaign results by state.
- **Campaign performance by region** — campaign results by region.
- **Campaign performance with conversion actions name** — conversions broken out by the named conversion action.
- **Campaign performance with unique user stats** — reach-style unique user figures per campaign.
- **Click performance** — click-level details by date.
- **Display keyword performance** — keyword targeting results in Display campaigns.
- **Display topics performance** — topic targeting results in Display campaigns.
- **Expanded landing page** — final URLs after redirects and tracking, with their metrics.
- **Gender performance** — results by gender.
- **Keywordless query** — queries matched by dynamic search ads.
- **Landing page** — performance per landing page URL.
- **Placement performance** — where Display and video ads appeared and how they did.
- **Responsive search ad performance** — results for responsive search ads.
- **Search query performance** — the actual search terms that triggered your ads.
- **Shopping performance** — product-level Shopping results.
- **User location performance** — results by where users physically were.
- **Video campaign performance with conversions** — video campaign views and conversions.

**Core Components**

- **Accounts** — account details such as name, currency, and time zone.
- **Ad groups** — the list of ad groups with their settings.
- **Ads** — every ad with its type and status.
- **Campaigns** — campaign names, types, statuses, and dates.

**Campaign Settings**

- **Campaign budgets** — budget amounts and delivery methods.
- **Campaign criterion** — targeting criteria set on campaigns.
- **Campaign labels** — labels applied to campaigns, useful as report filters.

**Strategies and Constants**

- **Accessible bidding strategies** — bidding strategies available to the account.
- **Bidding strategies** — portfolio bidding strategies and their settings.
- **Carrier constant** — reference list of mobile carriers.
- **Language constant** — reference list of languages.
- **Mobile app category constant** — reference list of app categories.
- **Mobile device constant** — reference list of mobile devices.
- **Operating system version constant** — reference list of operating system versions.
- **Topic constant** — reference list of topics for targeting.

**Miscellaneous**

- **Ad group criterion** — keywords, audiences, and other criteria on ad groups.
- **Call details** — call records from call ads and extensions.
- **Labels** — the account's labels.
- **User interest** — interest categories available for targeting.
- **User list** — your remarketing and customer lists.

## Why export Google Ads to Google Data Studio — real life cases

These are the Google Ads reports PPC managers, agencies, and growth teams build once the data refreshes without them.

- **Morning pacing dashboard**

  Campaign performance split by Date feeds a cost-versus-budget line chart and a scorecard row for Cost, Conversions, and cost per conversion, with a date range control set to this month. The PPC manager sees overspend before lunch rather than at month end.

- **Search term mining sheet**

  **Search query performance** for the last 30 days goes into a sortable table with a text filter control. Each week the team scans for terms with cost and zero conversions, adds negatives, and stops copying the search terms view out of the Google Ads interface.

- **Geo heat map for regional budgets**

  Coupler.io's Append stacks **Campaign performance by country** and **Campaign performance by state** into one data source. A Google Data Studio geo chart colored by conversion rate shows regional managers where to raise bids and where to pull back.

- **Agency client portfolio report**

  One flow covers every client account; an account filter control on a shared report lets each client see their own figures. Scheduled email delivery from Google Data Studio sends a PDF on the first of the month, replacing a half-day of slide-building.

- **Performance Max asset group review**

  **Asset group performance** split by Week lands in a table and a bar chart of conversion value per asset group. Growth teams use it in the biweekly creative review to decide which asset groups get fresh images and headlines.

- **Conversion action breakdown**

  **Campaign performance with conversion actions name** shows which conversion types each campaign actually drives, from purchases to sign-ups to calls. A stacked column chart makes it obvious when a campaign looks efficient only because of a soft micro-conversion.

- **Network-by-network split**

  **Campaign performance by ad network type**, aggregated in Coupler.io to monthly totals, powers a donut chart and a comparison table. It settles the recurring question of whether Search partners and Display are earning their share of spend.

- **Spend and revenue in one view**

  Join Campaign performance with CRM deals or Shopify orders by campaign name in Coupler.io, and the Google Data Studio report shows cost next to real closed revenue. Marketing and finance stop reconciling two spreadsheets before the monthly business review.

## Other Google Data Studio integrations

Every other source you can land in Google Data Studio with the same no-code setup:

- [Connect Facebook Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-google-data-studio.md)
- [Connect Facebook Page Insights to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-page-insights-to-google-data-studio.md)
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
