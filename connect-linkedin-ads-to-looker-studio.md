---
title: Connect LinkedIn Ads to Data Studio with Coupler.io
slug: connect-linkedin-ads-to-looker-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-linkedin-ads-to-looker-studio.md
source: LinkedIn Ads
destination: Data Studio
meta_title: Connect LinkedIn Ads to Data Studio with Coupler.io
meta_description: Get LinkedIn Ads analytics by member company, job title, and seniority, plus sponsored leads and creatives, into Data Studio with scheduled refreshes.
---

![LinkedIn Ads](https://static.coupler.io/importers/linkedin.svg) → ![Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect LinkedIn Ads to Data Studio with Coupler.io

LinkedIn's Campaign Manager is good at showing one account's results in its own charts, and that's where it ends: there's no Google-built LinkedIn Ads connector for Data Studio (formerly Looker Studio), and exporting demographic reports by hand gets old quickly. Coupler.io pulls LinkedIn Ads analytics, leads, and account structure on a schedule, lets you shape it before delivery, and serves it to Data Studio as a data source that stays up to date without anyone touching it.

## How to export LinkedIn Ads data to Data Studio

You can export ad analytics grouped by one or several dimensions, campaign results by professional audience attributes, sponsored lead form submissions, and lists of account users, campaign groups, campaigns, creatives, video ads, sponsored content shares, and conversions. Sign in to LinkedIn, then go through these screens.

### Step 1. Basic settings

- **Ad accounts** — choose one or several LinkedIn ad accounts. Selecting more than one merges them in a single data source, so a portfolio view needs only one flow.
- **Report type** — the data category to load. Ad analytics by single dimension is the default, and the options are described further down.

### Step 2. Report period

- **Start date** — where the period begins, 60 days back by default. Set a relative value such as *days ago*, *this month*, *last month*, *this year*, or *last year* and each refresh moves the window forward. For sponsored leads it's the earliest capture date to include. Not shown for **Shares (creative sponsored content)** or **Conversions**.
- **End date** — where the period ends, today by default. Used by the three analytics reports and **Sponsored leads**.
- **Split data by period** — for the analytics reports, choose Daily, Monthly, Yearly, or Totals only.

### Step 3. Metrics and dimensions

These fields apply to the three analytics reports.

- **Metrics** — up to 18 per flow. Impressions, Reach, Clicks, Amount spend in USD, Conversions, and Reactions are preselected; you can add Leads, Lead form opens, Landing page clicks, Video completions, Document completions, Engagements, Average Dwell time, Conversion value in local currency, viral metrics, and many more. Need more than 18? Run a second flow and join the two in Coupler.io.
- **Dimension** — for **Ad analytics by single dimension** and **Campaign performance by member dimension**, the one attribute rows are grouped by: Campaign, Creative, Placement, Member company, Member job title, Member seniority, Member industry, Member country, and others.
- **Dimensions** — for **Ad analytics by multiple dimensions**, several attributes at once, such as Campaign group, Campaign, Creative, Campaign objective type, Impression device type, and Placement name.

### Step 4. Advanced settings

- **Advanced filters** — for the analytics reports, set a property and a value to fetch only matching rows, for example one campaign group.
- **Lead generation forms** — for **Sponsored leads**, pick specific forms or leave the field empty to collect submissions from all of them.

### Step 5. Blend and transform data

- **Column management** — hide unneeded fields, turn technical names into readable labels, reorder them, and set types.
- **Join** — link analytics rows to the **Campaigns** or **Creatives** list on their IDs, or to CRM opportunities, so names and pipeline sit beside the metrics.
- **Append** — combine LinkedIn Ads with Google Ads, Microsoft Ads, or Facebook Ads data for a B2B paid media overview.
- **Aggregate** — group daily analytics into monthly totals per campaign group or per member company.
- **Custom SQL** — query the prepared dataset for anything more specialized, like cost per qualified lead.

### Step 6. Data Studio destination

Once you select Data Studio, Coupler.io sets up a data source through its Data Studio connector, so there are no field definitions to write. A one-time authorization covers Coupler.io and the connector, and it has to be done with the **same Google account** for both. LinkedIn access is separate, but on the Google side, two different accounts is the classic reason the connection won't complete.

- **Report / data source URL** — optional. Already working in a Data Studio report or data source? Paste its URL (it starts with `https://datastudio.google.com/reporting/...`) so the flow is linked to it and Coupler.io can open it for you. Otherwise a new one is started.

Coupler.io infers each column's type from the data: dates come through as dates, so the report's date range controls work, and Amount spend in USD or Impressions come through as numbers. The first successful run has to happen before you design the report and before scheduling becomes available. If you run several LinkedIn flows, for example analytics and sponsored leads, add each one to the same report as a separate data source.

### Step 7. Schedule

Pick a cadence — every 15 minutes, hourly, daily, weekly, or monthly — and decide what each run does. Replace swaps in a fresh, current copy, which fits most campaign dashboards; append adds new rows on top of old ones, useful for a lead log. Data Studio keeps its own cache and by default updates it every 12 hours, so when someone needs today's numbers in a meeting, **Refresh data** in the report menu pulls them in right away.

### Bonus: or just ask the AI Agent to build it for you

Open the Coupler.io AI Agent from the right sidebar of the Coupler.io app and say what you're after:

> *"Build a LinkedIn Ads to Data Studio flow using Campaign performance by member dimension, grouped by Member seniority, for this year, split Monthly, so I can chart spend and conversions by seniority for our ABM dashboard."*

The Agent sets the report type, the date range, the period split, and the Data Studio destination. LinkedIn's setup keeps a few choices in the wizard for you:

1. **Connect LinkedIn Ads** — the LinkedIn sign-in is yours.
2. **Choose the ad accounts** — define whose data is included.
3. **Select metrics and dimensions, and any advanced filters** — these are picked in the wizard.
4. **Authorize the Data Studio connector** — with the Google account linked to Coupler.io.
5. **Point to the destination** — an existing report or data source URL, or a new data source.

When the first run completes, build the charts in Data Studio.

## What data can you export from LinkedIn Ads to Data Studio with Coupler.io?

The Report type list has 11 data categories, and each flow loads one. Coupler.io's **Join** and **Append** merge categories before Data Studio sees them — analytics with campaign names, say, or leads with creative details — leaving you one data source to build on. Blending several data sources inside the report remains an option if you'd rather keep them separate.

- **Ad analytics by single dimension** — metrics grouped by one dimension of your choice, from Campaign or Creative to Member company or Member job function.
- **Ad analytics by multiple dimensions** — the same metrics grouped by several dimensions together, such as Campaign group, Campaign, and Creative in one table.
- **Campaign performance by member dimension** — campaign results broken down by a professional attribute like Member seniority, Member industry, Member company size, or Member region.
- **Sponsored leads** — submissions from your LinkedIn lead generation forms, filtered by capture date.
- **Ad account users** — who can access each ad account, and with which role.
- **Campaign groups** — campaign group names, statuses, and budgets.
- **Campaigns** — campaign settings, objectives, and statuses.
- **Creatives** — the creatives in your account with their status and type.
- **Video ads** — the video ads in your account.
- **Shares (creative sponsored content)** — the posts used as sponsored content.
- **Conversions** — the conversion definitions set up in the ad account.

## Why export LinkedIn Ads to Data Studio — real life cases

B2B marketers, demand generation teams, and agencies lean on these reports most.

- **ABM account coverage report**

  **Campaign performance by member dimension** grouped by Member company shows Impressions, Clicks, and Amount spend in USD per target company in a sortable table. The ABM lead reviews it with sales every two weeks to see which named accounts are being reached and which need more budget.

- **Seniority and job function split**

  Member seniority and Member job function, charted as stacked bars of spend and Conversions, reveal whether budget reaches decision-makers or interns. Demand gen managers use the view to tighten targeting before a new quarter.

- **Lead form pipeline board**

  **Sponsored leads** refreshed every 15 minutes populate a table and a daily lead count chart filtered by form. SDRs follow up the same morning, and marketing combines it with spend in Coupler.io to report cost per lead per form.

- **Campaign group budget tracker**

  Ad analytics grouped by Campaign group, aggregated monthly in Coupler.io, feeds a gauge-style scorecard against each group's budget. The paid social manager catches underdelivery mid-month instead of at the end-of-quarter recap.

- **Document and video engagement report**

  Document completions and Video completions at each quartile, alongside Average Dwell time, go into a bar chart per Creative. Content marketers see which gated asset or video format holds attention and plan the next round of production around it.

- **Client reporting for B2B agencies**

  One flow across all client ad accounts and an account filter control produce one shared report per client. Data Studio's scheduled email delivery sends it every Monday, which replaces copying Campaign Manager charts into slides.

- **Cross-network B2B spend view**

  Coupler.io's Append places LinkedIn Ads next to Google Ads and Microsoft Ads under shared column names. A single Data Studio time series and a pie chart show how spend is split across B2B channels and where cost per conversion is lowest, which feeds the quarterly budget plan.

- **Industry targeting review**

  Member industry as the dimension, with Clicks, Leads, and Amount spend in USD, gives a ranked table of industries by cost per lead. Product marketing uses it to decide which verticals get dedicated campaigns next quarter.

## Other Data Studio integrations

Every other source you can land in Data Studio with the same no-code setup:

- [Connect Facebook Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-looker-studio.md)
- [Connect Facebook Page Insights to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-page-insights-to-looker-studio.md)
- [Connect Google Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-ads-to-looker-studio.md)
- [Connect Google Analytics to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-analytics-to-looker-studio.md)
- [Connect Google Search Console to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-search-console-to-looker-studio.md)
- [Connect Instagram Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-instagram-ads-to-looker-studio.md)
- [Connect Instagram Insights to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-instagram-insights-to-looker-studio.md)
- [Connect LinkedIn Public Data to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-linkedin-public-data-to-looker-studio.md)
- [Connect Microsoft Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-microsoft-ads-to-looker-studio.md)
- [Connect QuickBooks to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-quickbooks-to-looker-studio.md)
- [Connect Shopify to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-shopify-to-looker-studio.md)
- [Connect TikTok Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-ads-to-looker-studio.md)
- [Connect TikTok Organic to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-organic-to-looker-studio.md)
- [Connect WooCommerce to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-looker-studio.md)
- [Connect Xero to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-looker-studio.md)
- [Connect YouTube Analytics to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-looker-studio.md)
