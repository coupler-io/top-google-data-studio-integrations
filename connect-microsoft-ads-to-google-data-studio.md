---
title: Connect Microsoft Ads to Google Data Studio with Coupler.io
slug: connect-microsoft-ads-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-microsoft-ads-to-google-data-studio.md
source: Microsoft Ads (Bing Ads)
destination: Google Data Studio
meta_title: Connect Microsoft Ads to Google Data Studio with Coupler.io
meta_description: Send Microsoft Ads campaign, keyword, search query, share of voice, and budget reports to Google Data Studio on a schedule. Bing dashboards that stay current.
---

![Microsoft Ads](https://static.coupler.io/importers/microsoft.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect Microsoft Ads to Google Data Studio (Looker Studio) with Coupler.io

Google ships no native connector from Microsoft Advertising into Google Data Studio, so Bing numbers usually reach a dashboard as a downloaded CSV that is stale before the meeting starts. The reports inside Microsoft Advertising itself are fine for one account at a time and awkward for anything else. Coupler.io pulls any of 44 Microsoft Ads report types straight into a Google Data Studio data source, across as many ad accounts as you like, and keeps it refreshed without anyone opening the Microsoft UI.

## How to export Microsoft Ads data to Google Data Studio

The wizard covers campaign, ad group, ad, and keyword performance, search queries, ad extensions, Dynamic Search Ads, shopping and hotel campaigns, audience targeting, budgets, change history, and fully custom reports. Here is each screen in order.

### Step 1. Basic settings

- **Ad accounts** — choose one Microsoft Advertising account or a whole list of them. Picking several produces a single combined data source, which is exactly what an agency rollup or a multi-brand view needs.
- **Report type** — decides what the rows in Google Data Studio represent: campaigns, keywords, search terms, products, locations, and so on. Every option is described further down this page. Pick **Custom report** when none of the prebuilt shapes fit.

### Step 2. Report period

- **Report period** — Microsoft's own preset windows such as *Today*, *Yesterday*, *Last 7 days* or *This week*. Choose **Custom** when you want to set the edges yourself.
- **Start date** — shown with **Custom**. Relative choices like *days ago*, *this month*, *last month*, *this year* or *last year* make the window slide forward by itself on every run.
- **End date** — the closing edge of a custom window. A date in the future is simply treated as today, so a relative end keeps the data source current.
- **Split data by period** — the time grain of each row: *Summary*, *Hourly*, *Daily*, *Weekly from Sunday*, *Weekly from Monday*, *Monthly* or *Yearly*. Daily is the safe pick for time-series charts. Not offered for the budget summary, change history, and negative keyword conflict reports.

### Step 3. Metrics and dimensions

Shown only for **Custom report**.

- **Metrics** — hand-pick the numbers: Impressions, Clicks, Spend, CTR, Average CPC, Conversions, Revenue, Return on ad spend, Impression share percent, and dozens more.
- **Dimensions** — the attributes every metric gets sliced by, from campaign and ad group to device, network, and tracking template.

### Step 4. Dimensions

- **Dimensions** — for every prebuilt report. You choose the descriptive columns (campaign status, campaign type, ad group name, device type, top vs other and the like) and Coupler.io brings along every metric that report supports automatically.

### Step 5. Advanced settings

- **Advanced filters** — a property and value pair that trims the result before it ships, for example a single campaign status or a specific network. Not available for the budget summary and product match count reports.

### Step 6. Blend and transform data

- **Column management** — drop columns the dashboard will never use, give API names like `AverageCpc` friendly labels, reorder fields, and fix types.
- **Join** — line up Microsoft Ads rows with another source on a shared key such as campaign name or date, so cost and CRM outcomes share one row.
- **Append** — put Google Ads, Facebook Ads, or LinkedIn Ads rows under your Bing data to get one paid search and social spend table.
- **Aggregate** — collapse daily keyword rows into monthly campaign totals when the dashboard needs the summary rather than the detail.
- **Custom SQL** — write a query against the prepared data for anything the other transformations do not cover.

### Step 7. Google Data Studio destination

- **Report / data source URL** — optional. Point the flow at a Microsoft Ads report you have already designed by pasting its `https://datastudio.google.com/reporting/...` address, whether that's the report or the data source behind it. Coupler.io then opens that exact report for you.

Select Google Data Studio as the destination and Coupler.io creates the data source through its own Google Data Studio connector. You sign in to Google Data Studio and to Coupler.io once, and it must be with the **same Google account**: two different accounts is the most frequent reason a setup stalls. Field types are read from the data itself, so the date column works with date range controls straight away and Spend, Clicks, and CTR land as numbers. Run the flow successfully once before you start building charts; that first run is also what unlocks scheduling.

### Step 8. Schedule

Choose how often the flow refreshes: every 15 minutes at the fastest, or hourly, daily, weekly, or monthly. Each run either replaces the previous data, which is what a performance dashboard normally wants, or appends to it so you build a running history. Bear in mind that Google Data Studio keeps its own cache and by default refreshes it every 12 hours; if you need this morning's spend now, open the report menu and click **Refresh data**.

### Bonus: or just ask the AI Agent to build it for you

Skip the form entirely if you prefer. Open the Coupler.io AI Agent in the right sidebar of the app and describe the result:

> *"Build a daily Microsoft Ads keyword performance report for the last 90 days with impressions, clicks, spend, conversions, and quality columns, for all my ad accounts, and send it to Google Data Studio so I can chart cost per conversion by keyword."*

The Agent chooses the report type, period, split, and dimensions, and asks only when your request leaves a real choice open. A few things remain yours:

1. **Connect Microsoft Ads** — the Microsoft sign-in is always done by you.
2. **Pick the ad accounts** — you control which accounts are included.
3. **Authorize Google Data Studio** — grant the connector access using the same Google account you use for Google Data Studio.
4. **Point it at a report** — paste a Google Data Studio report URL, or let Coupler.io create a new data source, so you know exactly where the data lands.

After the first run, open Google Data Studio and build the charts on top of the new data source.

## What data can you export from Microsoft Ads to Google Data Studio with Coupler.io?

There are 44 report types. Each flow carries one of them, so a dashboard that needs keyword detail plus budget pacing uses two flows. Coupler.io's **Join** and **Append** combine those reports before Google Data Studio ever sees them, giving you one tidy data source; you can still keep them separate and blend them inside the report if you prefer.

- **Campaign performance report** — spend, clicks, conversions, and ROAS per campaign, the backbone of most Bing dashboards.
- **Keyword performance report** — how each bid keyword performs, with match type and quality signals, so you can see which terms carry their cost.
- **Ad group performance report** — results one level below campaigns, useful when themes inside a campaign behave very differently.
- **Ad performance report** — individual ad results with titles and descriptions, ready for copy tests.
- **Ad extension by ad report** — which sitelinks, callouts, and other extensions show alongside each ad and what they earn.
- **Ad extension by keyword report** — the same extension results seen from the keyword side.
- **Ad extension detail report** — extension-level clicks and impressions, to tell useful extensions from decorative ones.
- **Call detail report** — calls generated by call extensions, with timing and status, for businesses where the phone is the conversion.
- **Budget summary report** — daily spend against each campaign's budget, the data behind any pacing chart.
- **Search campaign change history report** — who changed bids, budgets, or settings, and when.
- **DSA auto target performance report** — results for each Dynamic Search Ads auto target.
- **DSA category performance report** — Dynamic Search Ads performance grouped by website category.
- **DSA search query performance report** — the actual searches that triggered your Dynamic Search Ads.
- **Hotel dimension performance report** — hotel campaign results by property attributes.
- **Hotel dimension performance report with share performance statistics** — the same, plus impression share figures.
- **Hotel group performance report** — hotel results by hotel group.
- **Hotel group performance report with share performance statistics** — hotel group results with share of impressions.
- **Account performance report** — one line per account per period, perfect for an executive or client summary.
- **Account performance report with share performance statistics** — account totals with impression share lost to budget and rank.
- **Ad dynamic text performance report** — results for ads that use dynamic text parameters.
- **Ad group performance report with share performance statistics** — ad group results with competitive share figures.
- **Asset performance report** — individual headlines, descriptions, and images in responsive ads.
- **Asset group performance report** — Performance Max asset group results.
- **Audience performance report** — remarketing, in-market, and custom audience results.
- **Campaign performance report with share performance statistics** — campaign results with impression share, top impression share, and what was lost to budget or rank.
- **Conversion performance report** — conversions broken down by goal.
- **Destination URL performance report** — results by landing page URL.
- **Goals and funnels report** — conversion goal completions and the funnel steps leading to them.
- **Publisher usage performance report** — which sites and apps in the Microsoft network served your ads.
- **Search query performance report** — the real search terms that matched your keywords, the raw material for negatives.
- **Share of voice report** — how often you showed versus how often you could have, by campaign, ad group, or keyword.
- **Product dimension performance report** — shopping results by product attributes such as brand or category.
- **Product dimension performance report with share performance statistics** — product attribute results with impression share.
- **Product match count report** — how many products each product group matches in your catalog.
- **Product partition performance report** — results for each product partition you bid on.
- **Product partition performance report with share performance statistics** — partition results with competitive share.
- **Product partition unit performance report** — results at the lowest product partition level.
- **Product search query performance report** — the searches that triggered your shopping ads.
- **Age gender audience report** — performance by age bracket and gender.
- **Geographic performance report** — results by country, region, city, and other location levels.
- **Negative keyword conflict report** — negatives that block keywords you actually want to serve.
- **Professional demographics audience report** — LinkedIn-powered company, industry, and job function results, a Microsoft Ads specialty.
- **User location performance report** — where the people who saw your ads were physically located.
- **Custom report** — build your own combination of metrics and dimensions when no preset shape fits.

## Why export Microsoft Ads to Google Data Studio — real life cases

Bing traffic is usually a smaller line on the media plan, which is exactly why it gets neglected in reporting. These are the dashboards that fix that.

- **Weekly paid search review with Bing finally included**

  Most search reviews open a Google Ads dashboard and mention Microsoft only verbally. Feed the Campaign performance report into Google Data Studio and add a page with Spend, Conversions, and Return on ad spend scorecards plus a week-over-week line chart. The marketing lead runs the Monday review from one shared link instead of a screenshot pasted into slides.

- **Agency client reports that cover every engine**

  Clients who run both Google and Microsoft want one PDF. Append the two sources in Coupler.io, add an engine filter control, and schedule Google Data Studio's email delivery for every Monday at 8am. The account manager stops rebuilding the same deck each week and the client sees Bing results in the same layout as everything else.

- **Budget pacing board for finance**

  The Budget summary report gives daily spend against each campaign budget. A Google Data Studio bullet chart per campaign, plus a month-to-date scorecard, tells the finance team in seconds whether Bing will land on target. It replaces the end-of-month surprise and the spreadsheet someone used to update every Friday.

- **Search term mining dashboard for PPC specialists**

  Search query performance report data in a Google Data Studio table, sorted by Spend and filtered to rows with zero Conversions, is a ready-made list of negative keyword candidates. Add a Negative keyword conflict report page next to it so the specialist also sees which existing negatives are blocking good traffic. Weekly cleanup takes minutes instead of an afternoon in the Microsoft UI.

- **Competitive visibility tracker**

  Campaign performance report with share performance statistics carries Impression share percent and the share lost to budget and rank. Chart those three lines over time in Google Data Studio and the conversation with leadership changes from "Bing is small" to "we are losing 40% of eligible impressions to budget". That is a budget request with evidence attached.

- **Shopping campaign product dashboard for ecommerce**

  The Product dimension performance report shows revenue and cost by brand, category, and product attributes. A Google Data Studio treemap of Revenue by category and a table of Return on ad spend by brand let the merchandising team decide which lines to push. A date range control lets them compare the holiday season with an ordinary month in two clicks.

- **B2B audience report using professional demographics**

  Microsoft's LinkedIn-based targeting is a genuine advantage for B2B advertisers. Pull the Professional demographics audience report and build bar charts of Conversions and cost per conversion by industry and job function. Demand gen teams use it to justify bid modifiers and to show sales which company segments the ads are really reaching.

- **Change log alongside performance for account audits**

  When CPC jumps, the first question is what changed. Put the Search campaign change history report on a page next to daily Campaign performance report charts, with a shared campaign filter, and the cause is usually visible on the same date. Agencies use this during handovers and quarterly audits to show clients exactly what was adjusted and why.

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
- [Connect QuickBooks to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-quickbooks-to-google-data-studio.md)
- [Connect Shopify to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-shopify-to-google-data-studio.md)
- [Connect TikTok Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-ads-to-google-data-studio.md)
- [Connect TikTok Organic to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-organic-to-google-data-studio.md)
- [Connect WooCommerce to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-google-data-studio.md)
- [Connect Xero to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-google-data-studio.md)
- [Connect YouTube Analytics to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-google-data-studio.md)
