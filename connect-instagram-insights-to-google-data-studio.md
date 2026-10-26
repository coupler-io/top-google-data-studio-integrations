---
title: Connect Instagram Insights to Google Data Studio with Coupler.io
slug: connect-instagram-insights-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-instagram-insights-to-google-data-studio.md
source: Instagram Insights
destination: Google Data Studio
meta_title: Connect Instagram Insights to Google Data Studio with Coupler.io
meta_description: Move Instagram post totals, story stats, daily reach, follower demographics, and comments into Google Data Studio automatically. Social reports, no copy-paste.
---

![Instagram Insights](https://static.coupler.io/importers/instagram-ads.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect Instagram Insights to Google Data Studio (Looker Studio) with Coupler.io

Instagram's in-app Insights are made for a quick glance on a phone: short lookback windows, one account at a time, and stories that disappear from the stats a day after they expire. Google Data Studio has no Google-built Instagram connector to fill the gap. Coupler.io pulls post, story, and profile insights from every business profile you manage into a Google Data Studio data source on a schedule, so the numbers are kept and shared instead of glanced at and lost.

## How to export Instagram Insights data to Google Data Studio

The connector covers post performance and comments, 24-hour story statistics, daily profile reach and follower activity, breakdowns by media type and follow type, and audience demographics. Here is each screen of the setup.

### Step 1. Basic settings

- **Profiles** — choose the Instagram business or creator profiles to include. Several profiles go into one data source, which is handy for brands with regional accounts.
- **Report type** — sets what each row is: a post, a story, a comment, a day of profile activity, or a demographic slice. All 16 options are described lower on this page.

### Step 2. Report period

- **Start date** — for the profile reports that work by date range. A relative value like *days ago*, *this month* or *last month* keeps the window moving forward on its own. Instagram limits these reports to roughly 30 days per request, so the default starts 30 days back.
- **End date** — where the range finishes; yesterday by default, because today's figures are still incomplete.
- **Timeframe** — for **Profile: new audience demography insights**. Pick *This month* or *This week*.
- **Published after** — for post performance, post profile interactions, and comment reports. Only posts published after this date.
- **Published before** — for the same post reports. Only posts published before this date.
- **Split by** — for **Profile: performance insights** and **Profile: performance by media type**. Choose *Totals only*, *Daily*, or *Monthly*.

### Step 3. Metrics and dimensions

- **Metrics** — for **Profile: new audience demography insights**. Choose Engaged audience demographics, Reached audience demographics, or both.
- **Dimension** — for the two demography reports. Group by Age, Gender, "Age, Gender", City, or Country.

### Step 4. Advanced settings

- **Show promoted posts ad ids in separate rows** — for **Post: performance totals**. When a post was boosted, each ad ID gets its own row, so organic and promoted versions are easy to tell apart.
- **Data behavior** — for overview, demography, post, comment, and story reports. *Latest data* keeps only current values; *Track changes over time* stores a daily snapshot so you can see how a post or a follower count develops.

### Step 5. Blend and transform data

- **Column management** — keep the columns your charts use, rename metrics into plain English, and set types where needed.
- **Join** — connect post totals with comment details or profile interactions on the post ID, so one row tells the whole story of a post.
- **Append** — stack Facebook Page Insights, TikTok, or LinkedIn Company Pages data under Instagram for a combined organic social data source.
- **Aggregate** — sum daily reach into weekly or monthly totals, or roll post rows up by media type.
- **Custom SQL** — write a query for calculations the other tools do not cover.

### Step 6. Google Data Studio destination

- **Report / data source URL** — optional. When your Instagram dashboard already exists, give the flow its URL (a `https://datastudio.google.com/reporting/...` link to the report or its data source). Coupler.io remembers the connection and takes you there from the flow page.

Choosing Google Data Studio tells Coupler.io to produce a data source using the Coupler.io connector for Google Data Studio. Authorize both sides once, and do it with the **same Google account**; switching accounts halfway is the usual reason the connection fails. Coupler.io detects types from the values themselves, so dates behave as dates in your date controls and reach or likes stay numeric. A first successful run is required before you can build on the data source or set a schedule. If you have post, story, and profile flows, attach them all to one report as separate data sources.

### Step 7. Schedule

Choose the refresh rhythm: every 15 minutes, hourly, daily, weekly, or monthly. With replace, each run gives Google Data Studio a fresh, current copy; with append, rows accumulate, which is how you keep story stats long after Instagram drops them. Google Data Studio refreshes its own cache on a 12-hour cycle unless you change it, so after a run, choose **Refresh data** in the report menu to see the update straight away.

### Bonus: or just ask the AI Agent to build it for you

Find the Coupler.io AI Agent in the right sidebar of the app and type something like:

> *"Export daily reach for my Instagram profiles for the last 30 days, plus follower demographics by country, and connect both to Google Data Studio so I can build an audience growth dashboard."*

It chooses the report types, date ranges, and dimensions. You take care of:

1. **Connect Instagram** — the sign-in through Facebook and Instagram is yours.
2. **Select the profiles** — you choose which accounts are covered.
3. **Authorize the Google Data Studio connector** — using your Google account.
4. **Decide the destination** — paste a Google Data Studio report URL, or let Coupler.io start a new data source.

Then head to Google Data Studio and lay out the charts.

## What data can you export from Instagram Insights to Google Data Studio with Coupler.io?

There are 16 report types, each exported by its own flow. Coupler.io's **Join** and **Append** bring post, story, and profile data together before Google Data Studio receives it, so your report reads from one data source; alternatively, connect each flow separately and blend them in Google Data Studio.

- **Post: performance totals** — lifetime engagement and reach for every post, the go-to report for judging content.
- **Profile: account overview** — a current snapshot of each profile and its audience size, ideal for a portfolio summary.
- **Profile: performance insights** — profile-level reach, views, and interactions over your chosen period, in totals, daily, or monthly.
- **Profile: followers daily breakdown (last 30 days)** — follower gains day by day over the last month.
- **Profile: followers demography insights** — who follows you, by age, gender, city, or country.
- **Post: comment details review** — the comments themselves, with text and timing, for community management and sentiment work.
- **Post: profile interactions breakdown** — the profile visits, follows, and link taps a post triggered.
- **Story: performance totals (last 24 hours)** — reach, views, and replies for stories still live.
- **Story: navigation by action type (last 24 hours)** — taps forward, taps back, exits, and swipes on each story.
- **Story: profile interactions breakdown (last 24 hours)** — the profile visits and follows each story generated.
- **Profile: daily reach** — how many accounts saw your content each day.
- **Profile: performance by media type** — results split by posts, reels, stories, and other formats.
- **Profile: performance by follow type** — reach and interactions from followers versus non-followers.
- **Profile: links taps by contact button type** — taps on call, email, directions, and other contact buttons.
- **Profile: reach by media product type and follow type** — reach split by format and by follower status together.
- **Profile: new audience demography insights** — demographics of the people you reached or engaged this week or month.

## Why export Instagram Insights to Google Data Studio — real life cases

Instagram rewards teams that learn quickly from what they post. These reports turn that learning into a habit instead of a scramble.

- **Weekly content performance review**

  A Google Data Studio table built on Post: performance totals, sorted by reach or saves, with a media type filter and a date range control. The content team opens it every Monday and decides what to repeat and what to drop, without anyone scrolling through the app to collect numbers.

- **Story archive that outlives Instagram's 24 hours**

  Story reports cover only the last day. Run Story: performance totals (last 24 hours) and Story: navigation by action type (last 24 hours) every few hours in append mode, and Google Data Studio holds a permanent history. A chart of exits versus taps forward per story shows which formats hold attention across months of stories.

- **Follower growth dashboard for the brand manager**

  Profile: followers daily breakdown (last 30 days) appended daily builds a long-run follower series that Instagram does not keep for you. A Google Data Studio time series with a profile filter, next to Profile: account overview scorecards, gives the brand manager a growth story to share with leadership.

- **Audience demographics deck replacement**

  Profile: followers demography insights by Age, Gender, and Country drives Google Data Studio bar and geo charts. Marketing and sales teams use it to check that the audience matches the target customer, and it removes the screenshot slides from the quarterly brand review.

- **Reels versus posts versus stories comparison**

  Profile: performance by media type split daily shows how each format contributes to reach. A stacked area chart in Google Data Studio settles the recurring debate about whether reels deserve more production time, using numbers rather than gut feeling.

- **Followers versus new audience reach**

  Profile: performance by follow type and Profile: reach by media product type and follow type show how much reach comes from people who do not follow you yet. Growth teams track that share on a Google Data Studio scorecard as the main indicator of discovery.

- **Community management queue**

  Post: comment details review, refreshed every 15 minutes, feeds a Google Data Studio table filtered to the latest comments per post. Community managers have one place to see what needs a reply across all profiles, and leadership can see response volume over time.

- **Agency client reporting with scheduled delivery**

  Agencies connect each client's profiles, add a profile filter, and use Google Data Studio's scheduled email delivery to send a monthly PDF of reach, follower growth, and top posts. The client gets the same polished report every month and the account team stops building it by hand.

## Other Google Data Studio integrations

Every other source you can land in Google Data Studio with the same no-code setup:

- [Connect Facebook Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-ads-to-google-data-studio.md)
- [Connect Facebook Page Insights to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-facebook-page-insights-to-google-data-studio.md)
- [Connect Google Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-ads-to-google-data-studio.md)
- [Connect Google Analytics to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-analytics-to-google-data-studio.md)
- [Connect Google Search Console to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-google-search-console-to-google-data-studio.md)
- [Connect Instagram Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-instagram-ads-to-google-data-studio.md)
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
