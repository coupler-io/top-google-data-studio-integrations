---
title: Connect LinkedIn Public Data to Google Data Studio with Coupler.io
slug: connect-linkedin-public-data-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-linkedin-public-data-to-google-data-studio.md
source: LinkedIn Company Pages
destination: Google Data Studio
meta_title: Connect LinkedIn Public Data to Google Data Studio with Coupler.io
meta_description: Send LinkedIn Company Page follower gains, demographics, post and video performance to Google Data Studio on a schedule. Social reports that update themselves.
---

![LinkedIn Public Data](https://static.coupler.io/importers/linkedin.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect LinkedIn Public Data to Google Data Studio (Looker Studio) with Coupler.io

LinkedIn's Page analytics tab shows one Company Page at a time, and its downloads are spreadsheets you have to reopen, reformat and paste into a deck every month. Google offers no built-in LinkedIn connector for Google Data Studio either, so most social teams end up with a report that is out of date the day after it was built. Coupler.io fixes the plumbing: it pulls your Company Page reports straight from LinkedIn, keeps them refreshed, and hands them to Google Data Studio as a data source your charts can read.

## How to export LinkedIn Public Data data to Google Data Studio

Coupler.io covers three kinds of LinkedIn data here: page-level reach and follower growth, the demographics of who follows and visits the page, and post-by-post results including video. You sign in with the LinkedIn account that administers the pages, then work through the wizard below.

### Step 1. Basic settings

- **Pages** — tick the Company Pages you manage and want in the report. Choosing several is how an agency or a group with regional pages gets one data source per report type instead of one per page.
- **Report type** — decides what the flow returns. There are nine current options, grouped under Page, Audience and Post; each one is described further down. The fields in the next steps change depending on what you pick here.

### Step 2. Report period

- **Start date** — the first day the report covers. Relative values keep it current: *last month*, *this month*, *last year*, *this year* or a count of *days ago*, and each run nudges the window forward. Out of the box it starts 60 days back.
- **End date** — the last day included, *today* unless you want the window to close earlier.
- **Split data by period** — how rows are bucketed in time: Daily, Weekly, Monthly or Totals only. It appears for page performance, cumulative posts performance, follower gains and video reports, and the choices narrow a little per report (follower gains has no totals option, video stops at weekly).

The two date fields show up only for report types that are tied to a period. Lifetime overviews, follower demographics, individual post lifetime figures and reaction counts are snapshots, so they skip this step's dates.

### Step 3. Dimensions

- **Dimension** — the attribute your demographic rows are cut by. For audience demographics pick from Seniority, Country, Industry, Company size, Job function or Geo (market area). Follower demographics adds Association type to that list. One dimension per flow, so run a second flow if you want both industry and seniority side by side.

### Step 4. Metrics

- **Metrics** — used by **Post: video performance** only. Choose any of Views, Viewers, Time viewed (ms) and Time viewed for views (ms).

### Step 5. Blend and transform data

- **Column management** — drop LinkedIn columns your report never charts, give the rest names your audience will recognize, and change types where needed, for example turning milliseconds of watch time into a number you can divide.
- **Join** — line up two LinkedIn reports on page and date, so follower gains and page performance share one row per day.
- **Append** — put LinkedIn rows under Facebook Page Insights, Instagram Insights or TikTok Organic rows for one social overview.
- **Aggregate** — collapse daily rows into monthly totals per page before they arrive.
- **Custom SQL** — write your own query over the combined data when the visual tools are not enough, such as computing average seconds watched per viewer.

### Step 6. Google Data Studio destination

Choose Google Data Studio as where this flow ends up, and Coupler.io's Google Data Studio connector generates the data source on your behalf. You will be asked to authorize Google Data Studio and Coupler.io once. Use a single Google account for both steps; a second login sneaking in is the slip that derails most first setups.

- **Report / data source URL** — optional. LinkedIn report already live in Google Data Studio? Drop in its link (the `https://datastudio.google.com/reporting/...` address of the report or its data source). The flow attaches to that report, and Coupler.io opens it for you rather than creating a fresh one.

Column types come from the LinkedIn data itself, so dates land as real dates that respond to a date range control and follower counts land as numbers that scorecards can total. Charts come after a first successful run, and so does the schedule. Several LinkedIn flows can share a single report, each appearing there as its own data source.

### Step 7. Schedule

LinkedIn pages rarely change by the minute, so daily or weekly refreshes are usually enough, though Coupler.io can go as fast as every 15 minutes, or run hourly or monthly. Each run either swaps out the old rows for a clean, current snapshot (what most dashboards want) or appends the new rows below the old ones, which is how a follower history keeps growing. On its side, Google Data Studio caches the data and renews it roughly every 12 hours by default; the **Refresh data** option in the report menu forces an update on the spot.

### Bonus: or just ask the AI Agent to build it for you

Prefer to describe the report rather than click through it? The Coupler.io AI Agent waits in the app's right sidebar; type the request there:

> *"Build a Google Data Studio data source with weekly follower gains and page performance insights for our three LinkedIn Company Pages over the last six months, plus a separate one with follower demographics by seniority, so I can make a monthly employer brand dashboard."*

The Agent chooses the report types, the date window and the period split for you. Four jobs remain yours:

1. **Connect LinkedIn** — the sign-in belongs to you.
2. **Select the pages** — only you know which Company Pages belong in the report.
3. **Give the Google Data Studio connector access** — through your own Google sign-in.
4. **Pick where it lands** — the URL of a LinkedIn report you already keep in Google Data Studio, or a newly generated data source.

With one run complete, the charting in Google Data Studio is yours.

## What data can you export from LinkedIn Public Data to Google Data Studio with Coupler.io?

Nine report types are available, and each flow carries one of them. That is less of a limit than it sounds: Coupler.io's Join and Append combine report types before anything reaches Google Data Studio, so a page trend and a post table can arrive as one data source. If you would rather keep them separate, each flow becomes its own data source and Google Data Studio can blend them inside the report.

- **Page: lifetime overview** — the all-time totals for each Company Page, a quick headline number for a cover slide or a scorecard row.
- **Page: performance insights** — how the page itself performs over time, split by day, week or month. This is what most trend lines in a LinkedIn report are built from.
- **Page: cumulative posts performance** — the combined results of everything the page published in the period, so you can see whether content output as a whole is pulling its weight.
- **Page: follower gains trend** — new followers per day, week or month. The clearest single answer to "is the page growing?"
- **Page: follower demographics insights** — who follows the page, cut by one dimension such as Seniority, Industry, Company size, Job function, Country, Geo (market area) or Association type.
- **Page: audience demographics insights** — the same kind of breakdown for the wider audience your page reaches during the chosen period, useful for comparing reach with the following you already have.
- **Post: individual posts lifetime performance** — one row per post with its lifetime results, the table you sort to find what worked.
- **Post: video performance** — Views, Viewers, Time viewed (ms) and Time viewed for views (ms) for page videos, by day or week.
- **Post: social reactions & comments count** — reactions and comments per post, for a straight read on which updates started conversations.

## Why export LinkedIn Public Data to Google Data Studio — real life cases

These are the LinkedIn reports teams actually keep open in Google Data Studio, and who looks at them.

- **Monthly employer brand scorecard for leadership**

  HR and leadership want one page that says whether the company is becoming more visible to future hires. A row of scorecards fed by **Page: follower gains trend** with Monthly split, next to a line chart from **Page: performance insights**, answers that in a glance, and a date range control lets anyone switch from this quarter to last year. It replaces the slide someone used to rebuild from LinkedIn screenshots before every all-hands.

- **Is the following the audience sales actually wants?**

  B2B marketers care less about follower totals than about who those followers are. Separate flows for **Page: follower demographics insights** by Seniority, Job function, Industry and Company size feed bar charts that show at a glance whether the page attracts decision makers or mostly students and peers. Put them next to the target customer profile in the quarterly planning review and the content plan tends to rewrite itself.

- **Post leaderboard for the weekly content meeting**

  The social team opens a sortable table built from **Post: individual posts lifetime performance**, joined in Coupler.io with **Post: social reactions & comments count** so every post carries its conversation numbers. Conditional colors flag the top and bottom performers, and the meeting moves from "what did we post?" to "do more of this, stop that."

- **Video retention you can compare across posts**

  LinkedIn gives watch time in milliseconds, which nobody reads well. Coupler.io's Column management and Custom SQL turn Time viewed (ms) and Viewers into average seconds watched per viewer before the data lands, and Google Data Studio charts it per video alongside Views. Teams quickly see whether short cuts outperform long uploads and stop over-investing in the format that loses people in the first seconds.

- **One branded LinkedIn report per agency client**

  Agencies select every client's page under **Pages** in one flow, then build a single template with a page selector and hand each client a link locked to their own page. A scheduled email set up in Google Data Studio drops the PDF into every client inbox on the first of the month, so the account manager no longer exports and formats it by hand.

- **A social media overview with every network on one page**

  Coupler.io's Append places LinkedIn page performance under Facebook Page Insights, Instagram Insights and TikTok Organic rows with matching column names, so a single Google Data Studio data source holds the whole social footprint. The head of marketing gets one time series chart with a network breakdown instead of four tabs from four tools.

- **Choosing which regions deserve local content**

  **Page: audience demographics insights** by Geo (market area), shown on a Google Data Studio geo chart, reveals where the page already gets attention, while follower demographics by Country shows where people actually stayed. Gaps between the two point to markets worth a localized campaign or a regional showcase page, and the map is easy for a regional sales lead to read.

- **How much of the following is your own staff?**

  Follower demographics by Association type shows how many followers are associated with the company versus everyone else. Internal comms tracks it monthly to measure employee advocacy programs, and marketing uses it to explain why reach looks strong while external growth is flat. Set the schedule to append and the history builds itself month after month.

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
- [Connect Microsoft Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-microsoft-ads-to-google-data-studio.md)
- [Connect QuickBooks to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-quickbooks-to-google-data-studio.md)
- [Connect Shopify to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-shopify-to-google-data-studio.md)
- [Connect TikTok Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-ads-to-google-data-studio.md)
- [Connect TikTok Organic to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-organic-to-google-data-studio.md)
- [Connect WooCommerce to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-google-data-studio.md)
- [Connect Xero to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-google-data-studio.md)
- [Connect YouTube Analytics to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-google-data-studio.md)
