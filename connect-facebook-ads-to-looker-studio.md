---
title: Connect Facebook Ads to Data Studio with Coupler.io
slug: connect-facebook-ads-to-looker-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-looker-studio.md
source: Facebook Ads (Meta Ads)
destination: Data Studio
meta_title: Connect Facebook Ads to Data Studio with Coupler.io
meta_description: Send Facebook Ads insights, ad creatives, sponsored leads, activities, and Business invoices to Data Studio on autopilot for dashboards that stay current.
---

![Facebook Ads](https://static.coupler.io/importers/facebook.svg) → ![Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect Facebook Ads to Data Studio with Coupler.io

Google never shipped a native Meta connector for Data Studio (formerly Looker Studio), so most teams end up downloading Ads Manager exports, pasting them into a sheet, and hoping nobody opens the dashboard before Monday's refresh. Coupler.io removes that loop. It pulls Facebook Ads data straight from Meta, tidies it up on the way, and hands Data Studio a ready-made data source that refreshes itself — performance, structure, leads, change history, and invoices included.

## How to export Facebook Ads data to Data Studio

The wizard below covers ad performance insights, the campaign, ad set, ad, and creative structure behind it, lead form submissions, the account's activity log, and Meta billing. Sign in with your Meta profile, then work through the screens in order — fields that don't apply to the category you picked simply stay hidden.

### Step 1. Basic settings

- **Report type** — decides what the flow brings back. Choose one of the nine data categories described further down; every later screen reshapes itself to match.
- **Ad accounts** — select one or many. When you pick several, rows from each account land in the same data source, so one Data Studio report can cover a whole portfolio. Not used for invoices or leads.
- **Pages** — shown for **List of Sponsored Leads** only. Choose the Facebook Pages whose lead forms you want to read.
- **Businesses** — shown for **List of Business invoices** only. Pick the Business Manager accounts that receive the bills.

### Step 2. Report period

- **Start date** — where the window opens. Relative choices such as *days ago*, *this month*, *last month*, *this year*, or *last year* keep the window rolling forward without edits. For a full trailing year of history, `{{365daysago}}` does the job. Applies to insights, leads, and activities.
- **End date** — where the window closes. Set to *today*, every refresh picks up the newest spend Meta has reported.
- **Split data by period** — the time grain for insights: daily, weekly, monthly, or totals only. Daily is the default and the right choice for time-series charts.

### Step 3. Date filters

These four fields appear only for **List of Business invoices**.

- **Billing start date** — the earliest invoiced month to include. Left blank, Coupler.io reaches back six months.
- **Billing end date** — the latest invoiced month. Blank means up to the current one.
- **Issue start date** — filter by the date Meta issued each invoice instead. Once set, it overrides the billing-period filter.
- **Issue end date** — the latest issue date to keep.

### Step 4. Metrics and dimensions

- **Metrics and dimensions** — for **Reports and Insights**, pick the columns your charts need. Account and campaign names, Amount spend, Reach, Frequency, Impressions, Clicks, CPC, CPM, and CTR come preselected; add ROAS, video plays, or any of the conversion events, including custom conversions from your pixel.
- **Breakdowns** — slice the numbers by Age, Gender, Country, Region, Publisher platform, Platform position, Impression device, and dozens of other combinations. One breakdown set per flow.

### Step 5. Advanced settings

- **Attribution settings** — keep your ad account's attribution, switch to the ad group's, or set it manually so every account in a client report counts conversions the same way.
- **Action attribution windows** — available when attribution is set manually. Choose click, view, or engaged-view windows, from 1 day to 28 days.
- **Filters** — a Graph API filter expression for insights, handy for dropping paused campaigns or isolating one objective before the data ever reaches your report.
- **Lead generation forms** — for sponsored leads, narrow the pull to particular forms or leave it empty to capture every form on the selected Pages.
- **Ad creative columns** — for **List of Ads with ad creatives**, choose which creative fields come along: creative name, body, title, call to action type, image and thumbnail URLs, link URL, URL tags, and more. Leave it blank to get them all; core ad properties are always included.
- **Updated since** — also for ads with creatives, fetch only the ads modified after a given date.

### Step 6. Blend and transform data

- **Column management** — hide fields the report won't use, rename API-style names into labels your viewers recognize, reorder them, and adjust data types.
- **Join** — match Facebook Ads rows with another dataset on a shared key, such as campaign name against CRM deals or ad ID against creative details.
- **Append** — stack Meta data with Google Ads, TikTok Ads, or LinkedIn Ads rows so one data source holds every paid channel.
- **Aggregate** — collapse daily rows into weekly or monthly totals per campaign before they hit the dashboard.
- **Custom SQL** — write a query over the prepared data for anything the other options don't cover.

### Step 7. Data Studio destination

Pick Data Studio on the destination screen; Coupler.io then builds the data source for you using its own Data Studio connector. You authorize two things, Coupler.io and the Data Studio connector, and both must use the **same Google account** — a personal Gmail for one and a work login for the other is the most common reason a setup stalls.

- **Report / data source URL** — optional. If you already have a Data Studio report or data source (a link starting with `https://datastudio.google.com/reporting/...`), paste it here so the flow is tied to it and opens it straight from Coupler.io. Leave it empty to start fresh.

Coupler.io works out field types by looking at the values: Amount spend arrives as a number and the date column as a real date, so the report's date range control filters correctly from the first chart. Run the flow once successfully before you start building in Data Studio — the Schedule step stays locked until that run succeeds.

### Step 8. Schedule

Set the refresh to every 15 minutes, hourly, daily, weekly, or monthly. On every run Coupler.io can swap in a fresh snapshot, which suits most performance dashboards, or add the new rows beneath the old ones to keep a running history. Bear in mind Data Studio holds its own cache and refreshes it about every 12 hours by default; when a client is on the call and you need this morning's spend, hit **Refresh data** in the report menu.

### Bonus: or just ask the AI Agent to build it for you

Prefer to describe the report instead of clicking through it? Open the Coupler.io AI Agent in the right sidebar of the app and type something like:

> *"Set up a flow from Facebook Ads to Data Studio with daily Amount spend, Impressions, Clicks, CTR, CPC, and Purchase ROAS for the last 90 days, broken down by Publisher platform, so I can build a weekly client dashboard."*

The Agent chooses the report type, the columns, the breakdown, and the date window, then prepares the Data Studio destination. A few steps stay in your hands:

1. **Connect Facebook Ads** — the Meta sign-in is yours to do.
2. **Choose the ad accounts** — or, for leads, the Pages and lead generation forms, which you pick in the wizard.
3. **Authorize the Data Studio connector** — signed in to Google exactly as you are in Coupler.io.
4. **Decide where the data lands** — link a report or data source you already use, or have a new data source generated.

With the first run done, head to Data Studio and arrange the charts.

## What data can you export from Facebook Ads to Data Studio with Coupler.io?

There are nine data categories, and each flow carries one of them. That's rarely a limitation: Coupler.io's **Join** and **Append** can merge categories inside the flow, for example ads with their creatives or insights with campaign budgets, so a single merged data source is what reaches Data Studio. Prefer them separate? Connect every flow to the report on its own and use Data Studio blending as the fallback.

- **Reports and Insights** — the performance layer: spend, reach, impressions, clicks, CPC, CPM, CTR, ROAS, video completion, and every conversion event you track, split by day, week, or month and by any breakdown. Most Facebook dashboards start here.
- **List of Sponsored Leads** — submissions from your Meta lead forms with the answers people gave, the time they submitted, and the ad and campaign behind each one.
- **List of Ad creatives** — every creative stored in the ad account, used or not, with its format, copy, links, and media.
- **List of Ad sets** — status, optimization goal, and remaining budget for each ad set, useful for explaining why delivery shifted.
- **List of Campaigns** — objective, status, budget, and stop time per campaign, the labels that make a spend chart readable.
- **List of Ads** — one row per ad with its status, bid amount, and any issues Meta has flagged.
- **List of Ads with ad creatives** — only creatives that actually ran, already attached to their ads, so a creative scorecard needs no extra matching.
- **List of Activities** — the account's audit trail: who changed a budget, paused an ad, or edited an audience, and when.
- **List of Business invoices** — monthly invoices for each bill-to entity on your Business, with billed amounts and the campaigns included.

## Why export Facebook Ads to Data Studio — real life cases

Here's how marketing, agency, and finance teams put these Meta data sources to work once they live in a shared report.

- **Weekly paid social scorecard for the marketing lead**

  A single page of scorecards — Amount spend, Reach, CTR, CPC, and Purchase ROAS — sits above a daily line chart, with a date range control preset to the last seven days. The marketing lead checks it before the Monday stand-up instead of asking someone to screenshot Ads Manager.

- **White-labeled client reports for agencies**

  Agencies select every client ad account in one flow, then add an account-name filter control so each client sees only their own figures through a shared view link. Data Studio's scheduled email delivery sends a PDF every Monday, which retires the manual Friday export routine.

- **Placement and device breakdown for budget shifts**

  With Publisher platform and Impression device as breakdowns, a stacked bar chart shows where spend actually goes across Facebook, Instagram, Audience Network, and Messenger. Paired with CPM and CTR per placement, it tells the media buyer which placements to trim before the next budget review.

- **Creative leaderboard for the design team**

  A flow based on **List of Ads with ad creatives**, joined to insights in Coupler.io, feeds a table with thumbnail URLs, titles, call to action types, spend, and CTR. Designers sort it to find the best performers and spot fatigue, instead of waiting for a monthly creative recap deck.

- **Lead form intake dashboard for sales**

  **List of Sponsored Leads** refreshed every 15 minutes powers a table and a time-series chart of submissions by form and campaign. Sales managers filter by form to see today's volume and follow up quickly, and marketing gets a cost-per-lead view by appending spend from insights.

- **Change log next to performance**

  Plot **List of Activities** as a table beside the daily CPA chart for the same date range. When a cost spike lines up with a budget edit or an audience change on the same day, the team can see who made it, which makes the weekly performance review about facts rather than guesses.

- **Meta billing report for finance**

  **List of Business invoices** fills a monthly bar chart of billed amounts by entity and a table of campaigns per invoice. Finance filters by month during close and checks Meta's invoices against the budget sheet without logging into Business Manager.

- **Cross-channel spend overview for leadership**

  Coupler.io's Append combines Facebook Ads insights with Google Ads and LinkedIn Ads rows under matching column names, so one Data Studio pie chart and one trend line cover total paid spend. Leadership compares channels side by side, and quarterly budget talks start from the same numbers.

## Other Data Studio integrations

Every other source you can land in Data Studio with the same no-code setup:

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
- [Connect TikTok Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-ads-to-looker-studio.md)
- [Connect TikTok Organic to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-organic-to-looker-studio.md)
- [Connect WooCommerce to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-looker-studio.md)
- [Connect Xero to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-looker-studio.md)
- [Connect YouTube Analytics to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-looker-studio.md)
