# top-looker-studio-integrations

Feed Data Studio (formerly Looker Studio) dashboards with data from ad platforms, social channels, analytics tools, online stores, and accounting software, with no code. These are Coupler.io's most-used Data Studio integrations: what each one can bring in, which dashboards and reports teams build on it, and how the setup works screen by screen.

Every page here covers a single source and answers three things: how the data flow is set up, which data you can pull, and what people end up charting with it. The pages are plain markdown, so they read the same on GitHub, in a code editor, or when an AI assistant fetches them.

## Where to find what

| You want to know | Look in |
| --- | --- |
| Which wizard screens and fields you will see | **How to export**, one subsection per wizard step, using the field names shown in the app |
| How to have the flow built for you from a plain-language request | **How to export → Bonus**, the last subsection |
| Which reports, entities, or records a source offers | **What data can you export**, one bullet per data category |
| Whether a particular metric or dimension is available | The **Metrics and dimensions** (or similarly named) step under **How to export** |
| How the flow connects to a Data Studio report | **How to export → Data Studio destination** |
| How often the dashboard data can refresh | **How to export → Schedule** |
| What dashboards and reports teams build with the data | **Why export**, the real life cases |
| Another source you can bring into Data Studio | **Other Data Studio integrations**, at the end of every page |

## How each page is structured

The order never changes, so after one page you can skim the rest.

1. **Frontmatter**, the metadata block described below.
2. **Source and Data Studio logos**, followed by the **H1**.
3. **Intro**, covering what is awkward about reporting on the source today and how Coupler.io handles it.
4. **How to export `{source}` data to Data Studio**, the setup walkthrough. Each wizard step gets a `###` subsection in the order it appears, with step and field names copied from the product so the page matches the screen. Every page then covers the same closing steps: blending and transforming the data, the Data Studio destination, and the schedule. A bonus subsection shows how the Coupler.io AI Agent, in the app's right sidebar, sets up the flow from a description.
5. **What data can you export from `{source}` to Data Studio with Coupler.io?**, listing every data category the connector exposes, each with a note on what it is good for. QuickBooks and Xero list both the records from the main source and the reports from the separate Reports source. Shopify also lists the Coupler.io dataset templates built on it.
6. **Why export `{source}` to Data Studio — real life cases**, seven or eight dashboards and reports teams build with the data, starting with the everyday one and getting more specialised.
7. **Other Data Studio integrations**, linking to every other page in this repo.

### Frontmatter fields

| Field | Meaning |
| --- | --- |
| `title` | The page's H1 |
| `slug` | URL-safe identifier, identical to the filename without `.md` |
| `canonical` | The page's own GitHub URL |
| `source` | The connector name as it appears in the Coupler.io app; two names when a page covers two connectors |
| `destination` | Always Data Studio in this repo |
| `meta_title` | Same as `title` |
| `meta_description` | Short summary for search results and link previews |

## Conventions

- **Plain markdown.** No HTML, which keeps headings and lists clean for readers, crawlers, and retrieval tools.
- **Product names are verbatim.** Step names, field names, data entities, and transformation names match the app. The explanations around them are written for these pages.
- **Logos** load from `static.coupler.io`, the asset host the Coupler.io app itself uses, instead of being stored in the repo.
- **Links between pages** use full GitHub URLs, so they keep working when a page is quoted or copied elsewhere.
- **Filenames** follow `connect-{source}-to-looker-studio.md`.

## Integrations

### Ads and paid media

- [Connect Facebook Ads to Data Studio](./connect-facebook-ads-to-looker-studio.md)
- [Connect Google Ads to Data Studio](./connect-google-ads-to-looker-studio.md)
- [Connect Instagram Ads to Data Studio](./connect-instagram-ads-to-looker-studio.md)
- [Connect LinkedIn Ads to Data Studio](./connect-linkedin-ads-to-looker-studio.md)
- [Connect Microsoft Ads to Data Studio](./connect-microsoft-ads-to-looker-studio.md)
- [Connect TikTok Ads to Data Studio](./connect-tiktok-ads-to-looker-studio.md)

### Organic social and video

- [Connect Facebook Page Insights to Data Studio](./connect-facebook-page-insights-to-looker-studio.md)
- [Connect Instagram Insights to Data Studio](./connect-instagram-insights-to-looker-studio.md)
- [Connect LinkedIn Public Data to Data Studio](./connect-linkedin-public-data-to-looker-studio.md)
- [Connect TikTok Organic to Data Studio](./connect-tiktok-organic-to-looker-studio.md)
- [Connect YouTube Analytics to Data Studio](./connect-youtube-analytics-to-looker-studio.md)

### Web and search analytics

- [Connect Google Analytics to Data Studio](./connect-google-analytics-to-looker-studio.md)
- [Connect Google Search Console to Data Studio](./connect-google-search-console-to-looker-studio.md)

### Ecommerce

- [Connect Shopify to Data Studio](./connect-shopify-to-looker-studio.md)
- [Connect WooCommerce to Data Studio](./connect-woocommerce-to-looker-studio.md)

### Accounting

- [Connect QuickBooks to Data Studio](./connect-quickbooks-to-looker-studio.md)
- [Connect Xero to Data Studio](./connect-xero-to-looker-studio.md)
