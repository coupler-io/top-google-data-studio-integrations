---
title: Connect Google Search Console to Google Data Studio with Coupler.io
slug: connect-google-search-console-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-search-console-to-google-data-studio.md
source: Google Search Console
destination: Google Data Studio
meta_title: Connect Google Search Console to Google Data Studio with Coupler.io
meta_description: Get Search Console search, appearance, Discover, Google News and URL index data into Google Data Studio for many sites at once. SEO reports that stay current.
---

![Google Search Console](https://static.coupler.io/importers/google-search-console.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect Google Search Console to Google Data Studio (Looker Studio) with Coupler.io

Search Console's interface caps exports at a thousand rows, and the connector Google ships for Google Data Studio handles one property per data source. Discover, Google News and index status stay behind in the Search Console tabs. Coupler.io pulls all of those from any number of your sites on a schedule and passes them to Google Data Studio as data sources, so the full SEO picture lives in one report.

## How to export Google Search Console data to Google Data Studio

You can bring over classic search performance, performance by search appearance, Discover and Google News traffic, and the index status of specific URLs. Sign in with the Google account that has access to your Search Console properties, then fill in four short screens.

### Step 1. Basic settings

- **Sites** — the Search Console properties to pull from. Pick as many as you like; an agency can cover a whole client roster in one flow. Not used by the URL index report, which works from the list below instead.
- **Report type** — the dataset this flow returns, one of five. Later screens show only the fields that matter for your pick.
- **Inspection URLs** — appears only for **URLs index performance**. List the URLs whose index status you want checked, one per line.

### Step 2. Report period

- **Start date** — where the analysis period begins, 60 days back by default. Relative choices such as *last month*, *this year*, *days ago*, *this month* or *last year* move along with the calendar, so nobody edits the flow each week. For a full year of search trend data, enter `{{365daysago}}`.
- **End date** — where it ends, today by default.

Both dates apply to the four performance reports; the URL index report reflects current status, so it has no period.

### Step 3. Dimensions

- **Dimensions** — the breakdown for each row. Search results performance offers Date, Country, Device, Page and Query; Discover performance offers Date, Country and Page; Google News performance offers Date, Country, Device and Page. Date is selected to begin with, which is what makes a trend line possible.
- **Filters by dimensions** — narrow the data with a rule such as Query contains your brand name, or Page excluding a regex for staging paths. You can filter on Country, Device, Page, Query or Search appearance, even if that dimension is not among the ones you selected above. Operators include Contains, Equals, Does not contain, Does not equal, Including Regex and Excluding Regex.

This step applies to search results, Discover and Google News performance.

### Step 4. Advanced settings

- **Search results type** — which Google surface the search numbers come from: Web, News, Image or Video, with Discover and Google News added for the by-appearance report. Web is the default.
- **Aggregate data by** — how Google rolls up the numbers. Auto lets Search Console decide; Page groups by canonical URL; Property merges everything for the same property. Discover and Google News reports also offer News showcase panel, which needs a matching filter of Search appearance equals NEWS_SHOWCASE.
- **Data state** — Final returns only settled figures, a few days behind but no longer changing. All includes the freshest data, up to about a day old, which may still be revised.

### Step 5. Blend and transform data

- **Column management** — keep the Search Console columns your report needs, rename them for non-SEO readers and confirm their types.
- **Join** — link Search Console pages to Google Analytics landing pages, so rankings and on-site engagement share one row.
- **Append** — stack branded and non-branded flows, or several sites pulled separately, into one data source.
- **Aggregate** — total clicks and impressions by page or by month before the data leaves Coupler.io.
- **Custom SQL** — compute your own measures, like a weighted average position across a group of pages.

### Step 6. Google Data Studio destination

Google Data Studio is the destination here. Behind the scenes, Coupler.io's connector for Google Data Studio turns the flow into a data source. The first setup asks you to authorize Google Data Studio and Coupler.io; use one Google account for both, ideally the one with Search Console access. Using two different accounts is the usual reason setups fail.

- **Report / data source URL** — optional. Already running an SEO report in Google Data Studio? Paste the report or data source link (`https://datastudio.google.com/reporting/...`) to connect this flow to it; Coupler.io will open that report rather than making a separate one.

Types are taken from the Search Console data, so Date behaves as a date for range controls and clicks or impressions behave as numbers. The flow has to run successfully once before you build anything in Google Data Studio, and the schedule becomes available after that run too. Need search, Discover and index data in one report? Each flow plugs in as a data source of its own.

### Step 7. Schedule

Choose a refresh interval anywhere from every 15 minutes to hourly, daily, weekly or monthly. Search Console data settles over a few days, so daily is a sensible default. Each run either overwrites the previous data, keeping the report a current snapshot, or appends new rows to build a longer history than Search Console's own 16 months. Google Data Studio caches what it reads and renews it about every 12 hours unless you click **Refresh data** in the report's menu.

### Bonus: or just ask the AI Agent to build it for you

If you would rather skip the form, the AI Agent can configure the flow from a sentence. It lives in Coupler.io's right sidebar:

> *"Pull Search Console search results performance for all my sites by Date, Page and Query for the last three months, using final data only, and send it to Google Data Studio for a weekly SEO dashboard."*

It picks the report type, dimensions, period and advanced settings. Some parts stay manual:

1. **Connect Google Search Console** — sign-in is yours.
2. **Choose the sites** — you decide which properties are included.
3. **Set any dimension filters** — rules like branded-query exclusions you add yourself on the Dimensions screen.
4. **Sign the Google Data Studio connector in** — on your Google account.
5. **Say where the data should go** — the SEO report you already maintain, or a data source created from scratch.

Charts follow in Google Data Studio as soon as the first run has landed.

## What data can you export from Google Search Console to Google Data Studio with Coupler.io?

Five report types are available, and each flow returns one of them. Combine them in Coupler.io first: Join and Append can put search and Discover performance in the same data source before it reaches Google Data Studio. Keeping them apart and blending in the report is the other option.

- **Search results performance** — clicks, impressions, CTR and position from Google Search, broken down by Date, Country, Device, Page and Query. The foundation of any SEO dashboard.
- **Search results performance by appearance** — the same performance figures split by how your result appeared, such as rich results or video, to show whether structured data is paying off.
- **Discover performance** — traffic from the Google Discover feed by Date, Country and Page, for publishers and content sites that live on recommendations rather than queries.
- **Google News performance** — visibility and clicks inside Google News by Date, Country, Device and Page, so newsrooms can see which stories got picked up.
- **URLs index performance** — the index status of the URLs you list, a watchlist for the pages that must stay in Google.

## Why export Google Search Console to Google Data Studio — real life cases

These are the Search Console reports SEO teams, publishers and agencies run in Google Data Studio.

- **Weekly organic search dashboard for the whole team**

  Search results performance by Date drives a line chart of clicks and impressions with scorecards for CTR and average position above it. A date range control compares this week with the last, and the head of marketing gets an answer to "is organic up?" without opening Search Console.

- **Finding queries that are one push from page one**

  A flow with Query and Page feeds a Google Data Studio table filtered to high impressions and positions between about 5 and 15. These are the queries where a content refresh pays off fastest. The content team picks the next articles to update from this list every sprint instead of guessing.

- **Mobile versus desktop, market by market**

  Device and Country dimensions, shown as a stacked bar chart and a geo map, reveal where mobile search behaves differently from desktop. When CTR on mobile drops in one market, that is the cue to check how your results display on small screens there.

- **Proving the value of structured data**

  **Search results performance by appearance**, with Search results type set to Web or Video, shows clicks earned by each type of rich result. After the developers ship new markup, the SEO lead points to the chart in the next stakeholder meeting rather than arguing from theory.

- **A publisher dashboard for Discover and Google News**

  Editorial teams get two data sources in one report: **Discover performance** and **Google News performance**, both by Page and Date. Editors see which stories took off in each feed, and a filter control for section lets each desk follow its own coverage.

- **Index watchlist for revenue-critical pages**

  List your key product, pricing and landing pages under **Inspection URLs** and the **URLs index performance** report brings back their status on every run. A Google Data Studio table with conditional formatting marks anything that has dropped out of the index, so the problem is spotted the same day rather than after traffic falls.

- **Branded and non-branded traffic, tracked separately**

  Two flows use **Filters by dimensions**: one with Query Including Regex for brand terms, one with Excluding Regex. Coupler.io's Append stacks them into one data source, and Google Data Studio charts both lines on one time series. Growth in non-branded clicks is the number that shows SEO work is reaching new people.

- **Client SEO reports for agencies, sent automatically**

  Select every client site under **Sites** in a single flow, then copy one report template per client and restrict it to that client's site. Each client receives a PDF of their copy on the 1st through an email schedule configured in Google Data Studio, replacing the export-and-format routine account managers used to do by hand.

## Other Google Data Studio integrations

Every other source you can land in Google Data Studio with the same no-code setup:

- [Connect Facebook Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-google-data-studio.md)
- [Connect Facebook Page Insights to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-page-insights-to-google-data-studio.md)
- [Connect Google Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-ads-to-google-data-studio.md)
- [Connect Google Analytics to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-analytics-to-google-data-studio.md)
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
