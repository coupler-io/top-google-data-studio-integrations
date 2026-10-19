---
title: Connect WooCommerce to Data Studio with Coupler.io
slug: connect-woocommerce-to-looker-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-looker-studio.md
source: WooCommerce
destination: Data Studio
meta_title: Connect WooCommerce to Data Studio with Coupler.io
meta_description: Sync WooCommerce orders, line items, customers, products, coupons, and sales reports to Data Studio on a schedule for store dashboards that stay current.
---

![WooCommerce](https://static.coupler.io/importers/woocommerce.svg) → ![Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect WooCommerce to Data Studio with Coupler.io

WooCommerce Analytics lives inside WordPress admin, which means anyone who wants to see sales needs a login to the website itself, and the reports stop at what the plugin was designed to show. Getting the numbers into Data Studio (formerly Looker Studio) usually involves an export plugin, a CSV, and a spreadsheet that is out of date by lunchtime. Coupler.io reads directly from your store's REST API and keeps Data Studio filled with orders, products, customers, and WooCommerce's own report totals, on whatever schedule you choose.

## How to export WooCommerce data to Data Studio

The wizard handles transactional data (orders and their line items), catalog data (products, categories, tags, attributes, reviews), customers and coupons, store setup like shipping zones and tax rates, and WooCommerce's built-in report totals. After you connect the store with its URL and API keys, three short screens remain.

### Step 1. Basic settings

- **Data entity** — choose what this flow exports. Twenty-three options, from Orders and Products to the "Report:" totals; the complete list is further down.

### Step 2. Advanced settings

- **After date** — export only records dated after this moment. Applies to Coupons, Products, Product reviews, Orders, and Orders with line items. The relative picker (*days ago*, *this month*, *last month*, *this year*, *last year*) keeps the window rolling without edits.
- **Before date** — the closing boundary for the same entities. Leave it open to include everything up to the latest run.
- **Search** — return only exact matches for a word or phrase, for example a customer's surname on orders, or a product title to find every order containing it. Works for orders, products, customers, coupons, reviews, categories, tags, and shipping classes.
- **Status** — limit orders to one state: *Pending*, *Processing*, *On-hold*, *Completed*, *Cancelled*, *Refunded*, *Failed*, *Trash*, or *Any*. Only for Orders and Orders with line items.
- **Period** — the time span for *Report: Sales report* and *Report: Top sellers report*: *Today*, *This Week*, *This Month*, *Last Month*, *This Year*, or *Custom*.
- **Start date** — appears when Period is *Custom*; the first day the report covers.
- **End date** — also for *Custom*; the last day covered.

### Step 3. Columns

- **Columns** — type the column names you want, one per line, in the order they should appear. Leave it empty and every column comes through.

### Step 4. Blend and transform data

- **Column management** — trim the field list, rename WooCommerce's API keys into readable labels, set the column order, and fix data types.
- **Join** — add Products to Orders with line items by product ID so category and stock details sit on every sale.
- **Append** — merge two WooCommerce stores, or WooCommerce and Shopify, into a single sales table.
- **Aggregate** — sum line items into revenue per product per week, or count orders per status per day.
- **Custom SQL** — for any reshaping beyond the visual tools, write a query and Coupler.io loads its result.

### Step 5. Data Studio destination

Set Data Studio as the destination; Coupler.io then builds a data source using its Data Studio connector. There's a single authorization step, and Data Studio and Coupler.io have to be signed in with the **same Google account** — two different accounts is what breaks most first attempts.

- **Report / data source URL** — optional. If a WooCommerce report already exists in Data Studio, paste its URL (in the form `https://datastudio.google.com/reporting/...`) to link this flow to it and reach it from Coupler.io in one click. With no URL, you start from a new data source.

Coupler.io infers each field's type from the store data, so order dates work with Data Studio's date range control and totals arrive as numbers you can sum and average. Before building charts, complete one successful run; scheduling switches on after it. Keep orders and coupons as separate flows if you like and add both to one report as distinct data sources.

### Step 6. Schedule

Most stores refresh daily or hourly; during a promotion you can go down to every 15 minutes, and weekly or monthly suits slower catalog data. Choose **replace** so each run overwrites the data with the current picture, or **append** to grow a running record. Keep in mind Data Studio caches results and re-fetches them every 12 hours unless you change it, so use **Refresh data** from the report menu after a sync you want to see now.

### Bonus: or just ask the AI Agent to build it for you

The Coupler.io AI Agent is in the right-hand sidebar of the app. Describe the store report in a sentence:

> *"Export completed WooCommerce orders with line items since the start of this month to Data Studio, refreshed every hour, so I can track product revenue and order volume on a dashboard."*

The Agent picks the data entity, sets the status and date filters, and prepares the Data Studio destination. Your part:

1. **Connect WooCommerce** — enter the store URL and API keys yourself.
2. **Pick the store** — if you run several, choose which one this flow reads.
3. **Authorize the Data Studio connector** — with the Google account you also use in Coupler.io.
4. **Choose where it lands** — paste an existing report or data source URL, or let Coupler.io create a new data source.

After the first run, build your charts in Data Studio.

## What data can you export from WooCommerce to Data Studio with Coupler.io?

There are 23 data entities, and each flow exports one. Coupler.io's **Join** and **Append** bring entities together inside the flow, for example orders enriched with product categories, so Data Studio receives a single ready data source; blending separate data sources in the report is the alternative.

- **Continents** — the continent reference list WooCommerce uses, for grouping countries in geo charts.
- **Countries** — countries and their states as configured in WooCommerce, handy for clean location lookups.
- **Coupons** — coupon codes with discount type, amount, usage count, limits, and expiry, to see which promotions are actually used.
- **Currencies** — the currencies the store knows about, with codes and symbols.
- **Customers** — registered customers with contact, billing, and shipping details, for building customer lists and location maps.
- **Orders** — one row per order with status, totals, payment method, and billing and shipping details. The core of any sales dashboard.
- **Orders with line items** — every product within every order, with quantity, price, and totals, for product-level revenue.
- **Product attributes** — the attributes such as size or color defined in the store.
- **Product categories** — the category tree with names, parents, and product counts.
- **Product reviews** — customer reviews with rating, reviewer, and status, to track product sentiment.
- **Product shipping classes** — the shipping classes assigned to products.
- **Product tags** — tags and how many products carry each.
- **Products** — the catalog with SKU, prices, stock status, stock quantity, and categories.
- **Report: Coupon totals** — counts of coupons by type.
- **Report: Customer totals** — paying versus non-paying customer counts.
- **Report: Order totals** — order counts by status, a quick health check on the pipeline.
- **Report: Product totals** — product counts by type.
- **Report: Review totals** — review counts by star rating.
- **Report: Sales report** — WooCommerce's sales summary for the chosen period: sales, orders, items, tax, shipping, and discounts.
- **Report: Top sellers report** — the best-selling products and their quantities for the chosen period.
- **Shipping zones** — the shipping zones set up in the store.
- **Tax classes** — the tax classes in use.
- **Tax rates** — tax rates by country, state, and class, for checking what you charge.

## Why export WooCommerce to Data Studio — real life cases

Below are the WooCommerce dashboards that store owners, managers, and agencies build in Data Studio once the data refreshes without help.

- **Daily revenue page that doesn't need a WordPress login**

  Orders with *Status* set to *Completed* and *Processing* power scorecards for revenue, order count, and average order value, with a date range control defaulting to *this month*. The team bookmarks one Data Studio link and stops asking for admin access to the website.

- **Best sellers and slow movers**

  Orders with line items, joined to Products in Coupler.io, give a table chart of quantity and revenue per product and category. Sorting ascending surfaces the products that haven't sold in weeks, which feeds the next clearance decision.

- **Coupon performance review**

  Join Coupons with Orders to see revenue and order count per coupon code next to its usage limit and expiry. The marketing manager reviews it after each campaign and retires codes that discount sales which would have happened anyway.

- **Order pipeline for operations**

  *Report: Order totals* shows how many orders sit in *Processing*, *On-hold*, or *Pending*. A bar chart refreshed hourly sits on the warehouse screen, and a growing *On-hold* bar is the cue to chase payments before packing.

- **Regional sales map**

  Orders carry billing and shipping countries and states. A geo chart in Data Studio colored by revenue, plus a table of top regions, guides decisions on shipping zones and where to run localized ads.

- **Review and reputation tracker**

  Product reviews with ratings, combined with *Report: Review totals*, produce a monthly report of average rating per product and the share of one-star reviews. Product and support teams get it by scheduled email from Data Studio and follow up on items trending down.

- **Agency report across client stores**

  Agencies managing several WooCommerce shops append each store's orders into one data source with a store column. A single Data Studio template, filtered per client and shared as a view-only link, replaces a monthly spreadsheet for every account.

- **Tax and shipping check for the bookkeeper**

  *Report: Sales report* for *Last Month* gives total sales, tax, shipping, and discounts in one row per period. Next to Tax rates, it gives the bookkeeper a ready Data Studio page for the monthly close instead of a WordPress export.

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
- [Connect TikTok Organic to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-organic-to-looker-studio.md)
- [Connect Xero to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-looker-studio.md)
- [Connect YouTube Analytics to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-looker-studio.md)
