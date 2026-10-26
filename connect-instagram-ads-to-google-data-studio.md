---
title: Connect Instagram Ads to Google Data Studio with Coupler.io
slug: connect-instagram-ads-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-instagram-ads-to-google-data-studio.md
source: Instagram Ads
destination: Google Data Studio
meta_title: Connect Instagram Ads to Google Data Studio with Coupler.io
meta_description: Feed Instagram Ads insights plus campaign, ad set, and ad lists into Google Data Studio automatically, so reels and stories results are always one click away.
---

![Instagram Ads](https://static.coupler.io/importers/instagram-ads.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect Instagram Ads to Google Data Studio (Looker Studio) with Coupler.io

Instagram ads are bought and reported inside Meta's Ads Manager, where Instagram results share the screen with every other Meta placement and there's no direct line into Google Data Studio. The usual workaround is a weekly CSV that is stale by the time anyone reads it. Coupler.io connects to the same Meta ad accounts, lets you pull only the metrics and breakdowns you care about, and keeps a Google Data Studio data source updated on its own.

## How to export Instagram Ads data to Google Data Studio

There are four data categories here: performance insights, plus lists of campaigns, ad sets, and ads. Log in with the Meta profile that manages your ad accounts, then fill in the screens below — the period, metrics, and advanced screens only matter for insights.

### Step 1. Basic settings

- **Ad accounts** — select the Meta ad accounts that run your Instagram campaigns. Choosing several puts all of them in a single data source, each row tagged with its account.
- **Report type** — choose insights or one of the three structural lists. The rest of the wizard follows that choice.

### Step 2. Report period

- **Start date** — the opening day of the insights window, 60 days ago unless you change it. Relative picks such as *days ago*, *this month*, *last month*, *this year*, or *last year* keep the range current on every refresh.
- **End date** — the closing day, today by default.
- **Split data by period** — Daily, Weekly, Monthly, or Totals only. Keep Daily if you want trend lines; Totals only works for a simple campaign summary table.

### Step 3. Metrics and dimensions

- **Metrics and dimensions** — start from the defaults (account, campaign ID and name, Amount spend, Reach, Frequency, Impressions, Clicks, CPC, CPM, CTR) and add what your report needs: Instagram profile visits, Instagram profile follows, Video ThruPlay, video plays at 25% through 100%, Purchase ROAS, or any standard and custom conversion.
- **Breakdowns** — split results by Publisher platform and Platform position to separate Instagram from other Meta placements and compare positions within it, or by Age, Gender, Country, Region, and Impression device.

### Step 4. Advanced settings

- **Attribution settings** — follow the ad account's attribution, use the ad group's, or specify it yourself.
- **Action attribution windows** — when attribution is manual, pick the click, view, and engaged-view windows conversions should count within.
- **Filters** — a Graph API filter that trims the data at the source, for instance to one campaign objective.

### Step 5. Blend and transform data

- **Column management** — keep only the fields the report uses, give them readable names, put them in order, and correct types.
- **Join** — line up insights with the **List of Ads** or **List of Ad sets** on their IDs so status and budget sit next to the numbers.
- **Append** — add TikTok Ads or Facebook Ads rows beneath your Instagram data for one social ads data source.
- **Aggregate** — turn daily rows into weekly totals per campaign or placement.
- **Custom SQL** — write a query against the prepared data for calculated columns or custom filtering.

### Step 6. Google Data Studio destination

Set Google Data Studio as where this flow delivers. Coupler.io then sets up the data source via its Google Data Studio connector, and you grant access to Coupler.io and the connector one time. Both must run under the **same Google account**: Meta logins live separately, but on the Google side a mismatch between accounts is what typically breaks the connection.

- **Report / data source URL** — optional. Paste the link of a Google Data Studio report or data source you already have (`https://datastudio.google.com/reporting/...`) to bind this flow to it and open it from Coupler.io. Skip it and a new data source is created.

Coupler.io recognizes types from the values themselves — the date column arrives as a date, Reach and Amount spend arrive as numbers — so date range controls and number formatting work without tweaks. Let the flow complete a first successful run; only then build your report in Google Data Studio and switch on the schedule.

### Step 7. Schedule

Choose how often the flow runs: every 15 minutes, hourly, daily, weekly, or monthly. Pick replace to overwrite the data with the current picture each time, the usual choice for a campaign dashboard, or append to grow a log of past runs. Note that Google Data Studio serves a cached copy and updates it on its own timetable, every 12 hours unless changed; clicking **Refresh data** in the report menu fetches the newest values on demand.

### Bonus: or just ask the AI Agent to build it for you

Find the Coupler.io AI Agent in the right sidebar of the app and describe the report:

> *"Pull Instagram Ads insights for last month with Amount spend, Reach, Impressions, Video ThruPlay, and Instagram profile visits, broken down by Publisher platform and Platform position, and send it to Google Data Studio for a Reels versus Stories dashboard."*

The Agent picks the report type, metrics, breakdowns, and period, and sets up the destination. You still:

1. **Connect Instagram Ads** — sign in to Meta yourself.
2. **Select the ad accounts** — confirm which accounts are in scope.
3. **Authorize the Google Data Studio connector** — signed in to Google under the login you use for Coupler.io.
4. **Choose where it lands** — an existing report or data source URL, or a brand-new data source.

Once the first run finishes, build the visuals in Google Data Studio.

## What data can you export from Instagram Ads to Google Data Studio with Coupler.io?

Four data categories are on offer, one per flow. Because Coupler.io's **Join** and **Append** run before delivery, you can merge insights with the campaign, ad set, or ad lists into a single data source; blending separate data sources in the Google Data Studio report is the alternative if you want them kept apart.

- **Reports and Insights** — spend, reach, frequency, impressions, clicks, CPC, CPM, CTR, video plays, profile visits and follows, ROAS, and conversions, sliced by day, week, or month and by placement, device, or audience.
- **List of Campaigns** — every campaign with its status, objective, and budget, the context behind a spend chart.
- **List of Ad sets** — ad set settings like optimization goal, budget, and status.
- **List of Ads** — each ad's status and details, ready to be paired with performance rows.

## Why export Instagram Ads to Google Data Studio — real life cases

Instagram-heavy brands, social teams, and agencies tend to build these reports first.

- **Reels, Stories, and feed comparison**

  With Publisher platform and Platform position breakdowns, a bar chart compares CPM, CTR, and Video ThruPlay across Instagram placements. The social team uses it in the monthly planning session to decide how much of next month's budget goes to Reels.

- **Profile growth from paid**

  Instagram profile visits and Instagram profile follows sit in scorecards next to Amount spend, with a daily time series underneath. Brand managers can show how much paid activity is feeding the account's follower growth without pulling numbers from two tools.

- **Launch week tracker**

  For a product launch, a date range control locked to the campaign window and a table of ads by Reach and Frequency show whether the audience is saturating. The team checks it each morning of the launch week and rotates creatives when frequency climbs.

- **Audience demographics board**

  Age and Gender breakdowns drive a heat-map table of CTR and cost per result. It answers the recurring question from leadership about who actually engages with the brand's ads on Instagram.

- **Client social ads report**

  Agencies run one flow across client ad accounts and share a filtered report link per client. Google Data Studio's scheduled email delivery sends the weekly Instagram summary automatically, so account managers stop assembling screenshots on Friday afternoons.

- **Video completion funnel**

  Video plays at 25%, 50%, 75%, 95%, and 100% plotted as a descending bar chart per ad show where viewers drop off. Creative teams compare hooks across ads and brief editors on which openings to keep.

- **Social commerce returns**

  Purchase ROAS and purchase conversions by campaign, joined in Coupler.io with the **List of Campaigns** for objective and status, fill a sortable table. The e-commerce lead sees which active campaigns pay back and pauses the rest during the weekly trading meeting.

## Other Google Data Studio integrations

Every other source you can land in Google Data Studio with the same no-code setup:

- [Connect Facebook Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-google-data-studio.md)
- [Connect Facebook Page Insights to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-page-insights-to-google-data-studio.md)
- [Connect Google Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-ads-to-google-data-studio.md)
- [Connect Google Analytics to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-analytics-to-google-data-studio.md)
- [Connect Google Search Console to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-search-console-to-google-data-studio.md)
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
