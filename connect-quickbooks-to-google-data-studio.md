---
title: Connect QuickBooks to Google Data Studio with Coupler.io
slug: connect-quickbooks-to-google-data-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-quickbooks-to-google-data-studio.md
source: "QuickBooks, QuickBooks Reports"
destination: Google Data Studio
meta_title: Connect QuickBooks to Google Data Studio with Coupler.io
meta_description: Send QuickBooks invoices, bills, budgets, P&L, AR aging and cash flow reports to Google Data Studio on a schedule and keep finance dashboards current.
---

![QuickBooks](https://static.coupler.io/importers/quickbooks.svg) → ![Google Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect QuickBooks to Google Data Studio (Looker Studio) with Coupler.io

QuickBooks Online gives you reports you can read, print, or email as a PDF, and not much else. There is no Google-built QuickBooks connector in Google Data Studio, so finance teams usually end up exporting a spreadsheet every month, uploading it, and fixing the chart that broke because a column moved. Coupler.io connects to QuickBooks directly and hands Google Data Studio a data source that refreshes on a timetable: raw records such as invoices, bills, and budgets from the QuickBooks source, and finished statements like the Balance Sheet, the P&L, and the AR and AP aging reports from the QuickBooks Reports source.

## How to export QuickBooks data to Google Data Studio

Coupler.io splits QuickBooks into two sources. **QuickBooks** returns accounting records (customers, invoices, payments, journal entries) one entity per flow. **QuickBooks Reports** returns the standard QuickBooks reports, already calculated. Sign in with Intuit once and both sources reuse the connection. The steps below follow the QuickBooks source and point out where QuickBooks Reports asks for something different.

### Step 1. Basic settings

- **Data entity** — the record type this flow brings over, from Account through VendorCredit. Pick one and the rest of the wizard adjusts to it. The complete list of 33 is further down.

Working in QuickBooks Reports instead? Its **Basic settings** step asks for two things:

- **Report name** — which of the 28 QuickBooks reports to pull, from Account List Detail to Vendor Balance Detail.
- **Display columns by** — how the report spreads across columns. Summary reports such as Profit and Loss Summary or Balance Sheet split by Total, Month, Week, Quarter, Year, or by Customers, Vendors, Classes, Departments, and more. Transaction lists group by Name, Account, Transaction Type, Location, Payment Method, or a time grain instead.

QuickBooks Reports then adds a **Report period** step:

- **Report period** — the accounting window, chosen from relative options such as This Month, Last Month, This Fiscal Quarter, Last Fiscal Year, or This Fiscal Year-to-date. A relative choice rolls forward by itself, so a monthly dashboard never needs its dates edited. Pick Custom when you need fixed dates.
- **Start date** — the first day of a Custom period. It accepts macros, so `{{365daysago}}` gives you a rolling trailing year.
- **End date** — the last day of that Custom period.
- **Report date** — the as-of date for AP Aging Summary and AR Aging Summary, which decides which aging bucket each open balance falls into.

And a **Columns** step:

- **Columns** — the fields included in detail reports such as General Ledger Detail, Profit and Loss Detail, AR Aging Detail, or Transaction List. Each report starts with a sensible default set; add Past Due, Class, Location, or the multicurrency amounts when your company has those features switched on.

### Step 2. Advanced settings

- **Where** — a filter written as a QuickBooks query condition, for example only accounts of the Accounts Receivable type, or only invoices for one customer. Keeps the data source lean before Google Data Studio ever loads it.
- **Order** — sorts the records, ascending or descending, by any field the entity has.
- **Split by** — breaks a nested field into its own rows. Type `Line` for Invoice and every line item becomes a row, which is what you need for product-level revenue charts.

In QuickBooks Reports, this step holds different fields:

- **Report structure** — the layout of the output. **QuickBooks-style format** mirrors the report as QuickBooks shows it. **Values-by-row format** moves months, accounts, or categories out of the column headers into one column, which is the shape Google Data Studio time series and date range controls need. Detail reports offer a **Flat structure** with one row per transaction instead.
- **Query parameters** — extra key and value settings that QuickBooks accepts for a report, such as switching `accounting_method` between Cash and Accrual.

### Step 3. Blend and transform data

- **Column management** — drop the columns nobody charts, give QuickBooks field names friendlier labels, reorder them, and correct a data type where needed.
- **Join** — match QuickBooks data to another dataset on a shared key: Budget to Profit and Loss Summary by account, or Invoice to your CRM deals by customer.
- **Append** — stack the same entity or report from several QuickBooks companies into one dataset, which is how a bookkeeper or a group finance team gets one consolidated view.
- **Aggregate** — total transaction rows by month, class, or customer before they reach Google Data Studio, so the report loads quickly even on years of history.
- **Custom SQL** — write a query for anything the other transformations do not cover, and Coupler.io sends its result to Google Data Studio.

### Step 4. Google Data Studio destination

Choose Google Data Studio as the destination and Coupler.io creates a data source for this flow through its Google Data Studio connector. You authorize the connector and Coupler.io with one Google account; using a different Google login for each is the most common reason a first setup fails, so keep them matched.

- **Report / data source URL** — optional. To hook this flow up to a management report you already maintain, paste that report's URL or its data source's URL (`https://datastudio.google.com/reporting/...`). Otherwise Coupler.io starts you on a new data source.

Column types come from the data itself. Invoice dates land as dates, so a date range control filters them straight away, and amounts land as numbers ready for sums and scorecards. Run the flow successfully once before you open Google Data Studio to build charts; scheduling also becomes available after that first run. A single report can hold several QuickBooks flows as separate data sources, for example P&L, AR aging, and cash flow on three pages of one finance dashboard.

### Step 5. Schedule

Set how often the flow refreshes: every 15 minutes at most, or hourly, daily, weekly, or monthly. Then decide what each run does. Replacing the data gives the dashboard a clean, current picture, which suits a P&L or a balance sheet. Appending keeps every run, which turns an AR Aging Summary into a weekly history of receivables. Google Data Studio keeps its own cache and checks for new data every 12 hours by default; when the controller wants today's numbers during a meeting, **Refresh data** in the report menu fetches them right away.

### Bonus: or just ask the AI Agent to build it for you

Prefer to describe the dashboard instead of clicking through the wizard? Open the Coupler.io AI Agent in the right sidebar of the Coupler.io app and tell it what the finance team needs to see:

> *"Send QuickBooks Profit and Loss Summary for this fiscal year, by month, in values-by-row format, plus AR Aging Detail, to Google Data Studio. I want a monthly P&L trend and a collections page in one report, refreshed every morning."*

The Agent chooses the source, report, period, column grouping, and structure, and sets up a flow for each data source. A few steps remain with you:

1. **Connect QuickBooks** — the Intuit sign-in is yours to complete.
2. **Choose the company** — pick which QuickBooks company file each flow reads.
3. **Authorize the Google Data Studio connector** — with your Google account, the same one you use in Coupler.io.
4. **Decide where the data lands** — paste an existing report URL, or let Coupler.io create a new data source.

After that, open Google Data Studio and lay out the charts, scorecards, and filters.

## What data can you export from QuickBooks to Google Data Studio with Coupler.io?

QuickBooks data reaches Google Data Studio through two Coupler.io sources: 33 data entities in the QuickBooks source and 28 reports in QuickBooks Reports, 61 options in all. Each flow carries one entity or one report, so a finance dashboard usually runs several. Coupler.io's **Join** and **Append** can combine them into a single dataset before Google Data Studio sees it, such as budgets next to actuals, or one report stacked across companies; keeping separate data sources and blending them inside Google Data Studio is the fallback.

- **Account** — the chart of accounts with type, detail type, and current balance. The dimension most finance charts group by.
- **Attachable** — receipts, contracts, and other files attached to transactions, with the record each one belongs to. Useful for spotting expenses that have no supporting document.
- **Bill** — supplier bills with vendor, due date, total, and remaining balance. Feeds a chart of payables coming due.
- **BillPayment** — payments made against bills, with date and payment account. Shows when cash actually left the business.
- **Budget** — the budgets set up in QuickBooks, by account and period. The plan side of any budget vs actual chart.
- **Class** — your class list, the custom segment many businesses use for brands, programs, or service lines.
- **CompanyInfo** — company name, address, and fiscal year start. Handy for labeling a multi-company report correctly.
- **CreditMemo** — credits issued to customers, with amounts and remaining credit. Explains the gap between gross and net sales.
- **Customer** — customers with contact details, terms, and open balance. The lookup behind every revenue-by-customer chart.
- **Department** — the locations or departments you track, for comparing sites side by side.
- **Deposit** — money deposited into bank accounts, including the payments grouped into each deposit.
- **Employee** — employee records, for labeling time and expense data.
- **Estimate** — quotes sent to customers with status and amount. A view of the work that has not turned into invoices yet.
- **ExchangeRate** — the currency rates QuickBooks holds, for converting foreign amounts in charts.
- **Invoice** — every invoice with customer, dates, total, balance due, and line items. Split by `Line` and you can chart revenue by product.
- **Item** — products and services with prices, cost, and quantity on hand.
- **JournalEntry** — manual journal entries with their debit and credit lines, for reviewing adjustments.
- **JournalCode** — journal codes, used by QuickBooks editions that require them, such as in France.
- **Payment** — customer payments received and the invoices they settle. The basis for days-to-pay charts.
- **PaymentMethod** — the payment methods you accept, such as card, check, or bank transfer.
- **Preferences** — company settings like accounting method, home currency, and enabled features, which explain how the other data behaves.
- **Purchase** — expenses, checks, and card charges, with payee and account. Most day-to-day spending lives here.
- **PurchaseOrder** — orders placed with suppliers before they become bills. Committed spend.
- **RefundReceipt** — refunds paid back to customers, for tracking returns.
- **SalesReceipt** — sales paid in full at the time of sale, with no invoice in between.
- **TaxAgency** — the tax agencies you file with.
- **TaxCode** — tax codes applied to transactions.
- **TaxRate** — the rates behind each tax code.
- **Term** — payment terms such as Net 30, for comparing agreed terms with actual payment timing.
- **TimeActivity** — time logged by employees and contractors, with billable status and hours. Fuel for utilization charts.
- **Transfer** — money moved between your own accounts, so internal moves are not counted as income or spend.
- **Vendor** — suppliers with contact details, terms, and balance owed.
- **VendorCredit** — credits suppliers have issued to you, waiting to be applied to bills.

> **Note:** The reports below are available in the **QuickBooks Reports** source in Coupler.io, separate from the QuickBooks source above. Pick QuickBooks Reports when you create the flow, then choose the report in **Report name**.

- **Account List Detail** — every account with number, type, description, balance, and currency. A reference page for the dashboard.
- **AP Aging Detail** — each unpaid supplier bill with due date and days past due. Tells you which vendors to pay first.
- **AP Aging Summary** — payables per supplier grouped into aging buckets, as of the **Report date** you choose.
- **AR Aging Detail** — each open customer invoice with due date, past due days, and open balance. The working list for collections.
- **AR Aging Summary** — receivables per customer by aging bucket. Good for a stacked bar of overdue money.
- **Balance Sheet** — assets, liabilities, and equity. Run it by month to chart how the balance sheet moves.
- **Cash Flow** — operating, investing, and financing cash for the period. Shows where cash went even in a profitable month.
- **Customer Balance** — the amount each customer owes, one row per customer.
- **Customer Balance Detail** — the invoices and payments behind each customer balance.
- **Customer Income** — income, expenses, and net income per customer, for spotting accounts that cost more than they bring in.
- **Expenses by Vendor** — total spend per supplier for the period, for a quick vendor ranking.
- **General Ledger Detail** — every posting to every account. In **Flat structure**, it is the most flexible table you can give Google Data Studio.
- **Inventory Valuation Summary** — quantity, value, and average cost of each inventory item.
- **Journal Report** — journal entries listed with debits and credits, for reviewing what was posted.
- **Profit and Loss Summary** — income and expenses by account for the period. Split by Month for the classic P&L trend.
- **Profit and Loss Detail** — the transactions behind every P&L line, so a spike in one account can be explained with a click.
- **Sales by Class Summary** — revenue per class, for businesses that track brands or programs as classes.
- **Sales by Customer** — revenue per customer for the period.
- **Sales by Department** — revenue per department or location.
- **Sales by Product** — quantity, revenue, and share of sales per product or service.
- **Tax Summary** — tax collected and owed for the period, as a filing check.
- **Transaction List** — all transactions in the period with type, account, and amount.
- **Transaction List by Customer** — the same transactions grouped by customer.
- **Transaction List by Vendor** — the same transactions grouped by supplier.
- **Transaction List with Splits** — transactions with every split line shown, for when one total covers several accounts.
- **Trial Balance** — debit and credit balances per account, the standard close check.
- **Vendor Balance** — the amount you owe each supplier.
- **Vendor Balance Detail** — the bills and payments behind each supplier balance.

## Why export QuickBooks to Google Data Studio — real life cases

Here are the finance dashboards teams most often build once QuickBooks refreshes itself into Google Data Studio.

- **Monthly P&L dashboard for the owner**

  Pull Profit and Loss Summary from QuickBooks Reports with **Display columns by** set to Month and **Values-by-row format**, and Google Data Studio can draw income, expenses, and net income as one time series. Scorecards on top show this month against last, and a date range control lets the owner compare any two quarters. It replaces the P&L PDF someone emails at the start of each month.

- **Collections dashboard from AR aging**

  AR Aging Detail gives one row per open invoice with Customer, Due Date, Past Due, and Open Balance. In Google Data Studio that becomes a bar chart of overdue money by bucket and a table sorted by days past due, filtered by customer. Schedule an email delivery of the report every Monday morning and the person chasing payments starts the week with the current list.

- **Weekly cash position for the leadership meeting**

  Combine the Cash Flow report with Deposit and BillPayment records to show what came in and what went out each week. Coupler.io's Append puts the inflows and outflows into one dataset before Google Data Studio loads it, so a single chart shows net cash movement. The meeting looks at the same link every week instead of a slide built the night before.

- **Budget vs actual by account**

  Bring in the Budget entity and Profit and Loss Summary, then let Coupler.io's Join match them by account and month. Google Data Studio charts actual against plan with a variance column, and conditional colors flag accounts running more than ten percent over. Department heads can open it any time instead of waiting for the quarterly review.

- **Client-facing reports for accountants and bookkeepers**

  Set up one flow per client company and build a single report template in Google Data Studio. Copy it for each client, swap in that client's data source, and share a view-only link. Clients see their own Profit and Loss, Balance Sheet, and AR Aging Summary refreshed every morning, and the practice stops preparing monthly packs by hand.

- **Revenue by product and customer**

  Invoice split by `Line` gives one row per item sold, with amounts and dates; Sales by Product and Sales by Customer give the period totals. A treemap shows which products carry revenue, a table ranks the top customers, and a date range control makes seasonality easy to see. Sales and finance read the same numbers.

- **Vendor spend and payables review**

  Expenses by Vendor ranks suppliers by spend, while Bill and AP Aging Summary show what is due and how late. In Google Data Studio, a bar chart of top vendors sits beside a timeline of upcoming due dates. Operations sees where the money goes, and finance plans payments a week ahead instead of reacting to reminders.

- **Profitability by class or location**

  Sales by Class Summary and Sales by Department show revenue by segment, and Profit and Loss Detail with the Class column added shows costs for the same segments. Coupler.io's Aggregate totals them by month before loading, so the Google Data Studio report stays fast. A filter control lets each manager open the dashboard on their own brand or site.

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
- [Connect Microsoft Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-microsoft-ads-to-google-data-studio.md)
- [Connect Shopify to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-shopify-to-google-data-studio.md)
- [Connect TikTok Ads to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-ads-to-google-data-studio.md)
- [Connect TikTok Organic to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-tiktok-organic-to-google-data-studio.md)
- [Connect WooCommerce to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-google-data-studio.md)
- [Connect Xero to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-google-data-studio.md)
- [Connect YouTube Analytics to Google Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-google-data-studio.md)
