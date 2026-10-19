---
title: Connect TikTok Organic to Data Studio with Coupler.io
slug: connect-tiktok-organic-to-looker-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-organic-to-looker-studio.md
source: TikTok Organic
destination: Data Studio
meta_title: Connect TikTok Organic to Data Studio with Coupler.io
meta_description: Load TikTok profile insights, audience genders, countries, hourly activity and video insights into Data Studio, and keep history past the 60-day limit.
---

![TikTok Organic](https://static.coupler.io/importers/tiktok.svg) → ![Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect TikTok Organic to Data Studio with Coupler.io

TikTok's in-app analytics are built for a creator scrolling on a phone, not for a brand reporting to a manager, and the platform only lets you reach roughly the last 60 days of profile data. There is no Google-made TikTok connector in Data Studio (formerly Looker Studio), so the usual workaround is screenshots. Coupler.io connects to your TikTok account, pulls profile and video reports on a schedule, and delivers them to Data Studio as a data source, so the numbers are already there when the report is opened and older periods are kept instead of expiring.

## How to export TikTok Organic data to Data Studio

The data falls into three groups: profile-level insights over time, audience breakdowns (gender, country, hour of activity), and per-video results. Setup is two short steps plus the shared transform, destination and schedule screens.

### Step 1. Basic settings

- **Report type** — the only choice on this screen, and it defines the flow. Pick one of six reports: four describe the profile and its audience, two list your videos. Details are further down this page.

### Step 2. Report period

- **Start date** — the beginning of the window. TikTok will not return profile data older than about 60 days, so 60 *days ago* is the practical maximum and also the default. Shorter relative picks such as *this month* or *last month* fit inside that limit too; *this year* and *last year* reach further back than TikTok allows.
- **End date** — where the window stops; it defaults to yesterday, the last complete day TikTok has figures for.

These dates apply to the four profile and audience reports. The two video list reports come back without a period, so this step does not ask for anything there.

### Step 3. Blend and transform data

- **Column management** — trim TikTok's columns down to the ones on your report, rename them in plain English and fix types where needed.
- **Join** — attach **Video list top countries** to **Video list insights** by video so each video row knows where it was watched.
- **Append** — stack TikTok profile numbers under Instagram Insights or YouTube rows to get one short-form video data source.
- **Aggregate** — group daily profile rows into weekly or monthly totals before Data Studio sees them.
- **Custom SQL** — query the combined data directly, for example to rank videos by engagement per view.

### Step 4. Data Studio destination

With Data Studio picked as the target, the Coupler.io connector for Data Studio sets up a matching data source. The first time, you grant access to both Data Studio and Coupler.io. Make sure it is one Google account for both; a second account in the mix is the most common reason the connection fails.

- **Report / data source URL** — optional. Building on a TikTok report you made earlier? Paste its URL (it begins with `https://datastudio.google.com/reporting/...`, whether it points at the report or its data source) and Coupler.io ties the flow to it and can open it directly, instead of making another one.

Field types are read from the TikTok data, so dates are true dates that a date range control can filter and counts are numbers a scorecard can add up. Nothing can be charted until the flow has completed once, and that same first run is what unlocks scheduling. Several TikTok flows can sit in the same report, each as a separate data source.

### Step 5. Schedule

Pick a TikTok refresh rhythm: every 15 minutes at the quickest, otherwise hourly, daily, weekly or monthly. For TikTok the run mode matters more than usual. Replace keeps a tidy view of the last 60 days, which is fine for a live dashboard. Append keeps every run's rows, so your history keeps growing long after TikTok has stopped showing those days. One more timing detail: a Data Studio report shows its own cached version, which it renews about twice a day by default (every 12 hours). Hit **Refresh data** in the report menu to skip the wait.

### Bonus: or just ask the AI Agent to build it for you

You can also hand the configuration to the AI Agent, found on the right-hand side of the Coupler.io app. Tell it the dashboard you have in mind:

> *"Set up TikTok Organic flows for profile insights and audience hourly activity for the last 60 days, plus video list insights, and send them to Data Studio so I can build a weekly posting dashboard."*

It sets up one flow per report type and fills in the dates. What is left for you:

1. **Connect TikTok** — you sign in to the account yourself.
2. **Authorize the Data Studio connector** — with your own Google account.
3. **Decide where the data lands** — attach the flow to a TikTok report you already have, or start from a fresh data source.

From there, the visuals are built in Data Studio.

## What data can you export from TikTok Organic to Data Studio with Coupler.io?

There are six report types, one per flow. Coupler.io's Join and Append can merge them before delivery, for example putting video insights and top countries in one data source. Keeping them as separate data sources and blending inside Data Studio also works if you prefer.

- **Profile audience genders** — the gender split of your audience over the chosen period, the slide every brand partnership pitch asks for.
- **Profile audience countries** — where your viewers are, ready for a geo chart and for deciding which language your captions should be in.
- **Profile audience hourly activity** — when your audience is on TikTok, hour by hour. The basis for a posting schedule built on evidence rather than habit.
- **Profile insights** — the account's performance day by day, the trend line at the top of any TikTok report.
- **Video list top countries** — for each video, the countries where it was viewed most, so you can see which clips traveled beyond your home market.
- **Video list insights** — one row per video with its results; sort it and the next content brief practically writes itself.

## Why export TikTok Organic to Data Studio — real life cases

Here is how social teams, creators and agencies use TikTok data once it sits in Data Studio.

- **A weekly TikTok scorecard nobody has to screenshot**

  The social lead opens a Data Studio page where **Profile insights** drives a line chart and a few scorecards, with a date range control set to the last 7 days compared with the 7 before. Monday's update becomes a shared link rather than a set of phone screenshots pasted into Slack.

- **Posting when the audience is actually awake**

  **Profile audience hourly activity** fits naturally into a Data Studio pivot table with a heatmap: hours across, days down. The darkest cells show the windows to schedule posts in, and the content calendar is adjusted with data instead of guesswork. Revisit it monthly, because audiences shift as the account grows.

- **An audience map for localization decisions**

  A geo chart fed by **Profile audience countries** shows where the following really is. When a meaningful share turns out to be outside the home market, that becomes the case for subtitles, a second-language account or a regional creator partnership, and the map makes the argument for you in the planning meeting.

- **A self-updating media kit for brand deals**

  Creators and talent managers keep a Data Studio report with **Profile audience genders**, countries and recent profile performance, and share it with brands as a live link instead of a PDF that is outdated a week later. Partners see current numbers, and the creator stops re-exporting stats for every pitch.

- **Video post-mortems for the content team**

  A sortable table from **Video list insights**, joined in Coupler.io with **Video list top countries**, lists every recent video with its results and the markets it reached. In the weekly creative review the team filters to the top ten, looks for the shared hook or format, and briefs the next batch from what the data shows.

- **Keeping TikTok history past the 60-day window**

  Because TikTok only exposes about 60 days of profile data, a dashboard that replaces its data can never show last year. Switch the flow to append and Coupler.io keeps adding each run's rows, so after a few months Data Studio can draw a long-term follower and views trend and compare this season with the last one.

- **TikTok next to the other short-form channels**

  Coupler.io's Append puts TikTok profile metrics under Instagram Insights and YouTube rows with aligned column names. The marketing director gets one Data Studio chart comparing short-form channels, and Data Studio's scheduled email delivery sends it to the leadership team every Monday morning.

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
- [Connect TikTok Ads to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-ads-to-looker-studio.md)
- [Connect WooCommerce to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-looker-studio.md)
- [Connect Xero to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-looker-studio.md)
- [Connect YouTube Analytics to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-looker-studio.md)
