---
title: Connect Xero to Data Studio with Coupler.io
slug: connect-xero-to-looker-studio
canonical: https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-xero-to-looker-studio.md
source: "Xero, Xero Reports"
destination: Data Studio
meta_title: Connect Xero to Data Studio with Coupler.io
meta_description: Bring Xero invoices, payments, journals, payroll, Profit And Loss and aged receivables into Data Studio on a schedule for live finance dashboards.
---

![Xero](https://static.coupler.io/importers/xero.svg) → ![Data Studio](https://static.coupler.io/importers/data_studio.svg)

# Connect Xero to Data Studio with Coupler.io

Xero's built-in reports are tidy, but they live inside Xero: one organisation at a time, a fixed layout, and an export button when someone needs a chart. Google does not ship a Xero connector for Data Studio (formerly Looker Studio), which leaves most teams pasting CSV files into a sheet before every board meeting. Coupler.io reads Xero for you and keeps a Data Studio data source up to date, whether you want the records underneath (invoices, payments, journals, payroll, project time) from the Xero source or the finished statements (Profit And Loss, Balance Sheet, aged receivables) from the Xero Reports source.

## How to export Xero data to Data Studio

There are two Coupler.io sources for Xero, and both use the same Xero authorization. **Xero** delivers records, one data entity per flow, across accounting, payroll, and projects. **Xero Reports** delivers Xero's prepared reports. The steps below walk through the Xero source and call out what changes when you choose Xero Reports.

### Step 1. Basic settings

- **Xero tenant** — the organisation the flow reads. With several organisations under one login, you create a flow for each and combine them later.
- **Data entity** — the record type to export, grouped into accounting, payroll for the UK or New Zealand, payroll for Australia, and projects. All 57 are listed below.
- **Report type** — **Detailed** or **Simple**. Detailed adds many more fields and is offered for Bank transactions, Contacts, Credit notes, Invoices, Manual journals, Overpayments, and Prepayments; Simple gives the standard fields.
- **Projects** — for Tasks by projects and Time by projects, the projects to read from.

In Xero Reports, **Basic settings** contains **Xero tenant** plus:

- **Report type** — here it means the report itself, such as Profit And Loss, Balance Sheet, or Aged Payables By Contact.
- **Report structure** — for Balance Sheet, Budget Summary, Profit And Loss, and Executive Summary. **Xero-style format** keeps dates as column headers, the way Xero shows them; **Date-by-row format** puts dates in one column, which is the shape Data Studio date range controls and time series work with.

Xero Reports also has two short steps that apply to specific reports: **Contact**, with **Contact ID** for Aged Payables By Contact and Aged Receivables By Contact (each flow covers one contact), and **Bank account**, with **Bank Account ID** for Bank Statement.

### Step 2. Date filters

- **Changed after** — returns only records added or updated since this date. Pick a relative value such as *days ago*, *this month*, *last month*, *this year*, or *last year* and the window moves forward on its own. For a precise rolling year, the macro `{{365daysago}}` works too.
- **Start date** — the first day for UK or NZ Timesheets and for Time by projects.
- **End date** — the last day for those entities.
- **Created after** — the earliest creation date for Purchase orders and Quotes.
- **Created before** — the latest creation date for the same two.
- **Expiring after** — for Quotes, the start of the expiry window.
- **Expiring before** — the end of that window, so you can see which quotes lapse this month.

Xero Reports uses a **Report period** step instead, with **Date** (the as-of date for aged reports, Balance Sheet, Budget Summary, Executive Summary, and Trial Balance), **Start date**, and **End date** (for Profit And Loss, Bank Summary, Bank Statement, and the aged reports). The same relative choices keep a monthly report rolling without edits.

### Step 3. Advanced settings

- **Statuses** — for Invoices, which states to include: Draft, Submitted, Authorised, Paid, Voided, or Deleted. Leave out drafts and voided invoices for revenue charts.
- **Journal number more than** — start the Journals export after a known journal number.
- **Journal number less than** — stop it before a given number, for reloading one slice.
- **Split by** — breaks nested lines into rows. Invoices and Credit notes split by `LineItems` and Journals by `JournalLines` by default, so each line can be charted by account or item.
- **Status** — a single status filter for UK Pay runs, Timesheets, Linked transactions, Purchase orders, and Quotes.
- **Statuses** — for Projects, In progress or Closed; for Time by projects, Active or Invoiced.
- **Advanced settings** — property filters and sorting, plus entity-specific options such as Invoice Numbers, Contact Ids, Search term, or Unit decimal places.
- **Include archived** — whether archived Invoices, Contacts, and Tracking categories come along.

Xero Reports replaces this with a **Parameters** step:

- **Number of periods to compare** — for Balance Sheet, Budget Summary, and Profit And Loss, how many earlier periods to add next to the current one.
- **Period** — the size of each compared period: Month, Quarter, or Year.
- **Tracking category ID** — splits Profit And Loss by the options of one tracking category, such as region or department.
- **Tracking category ID-2** — a second tracking category for the same split.
- **Tracking option ID** — narrows a report to one tracking option.
- **Tracking option ID-2** — adds a second tracking option filter.
- **Include cash transactions only** — limits Balance Sheet, Profit And Loss, or Trial Balance to cash transactions, for a cash-basis view.
- **Standard layout** — uses Xero's standard layout instead of any custom layout set up in the organisation.

### Step 4. Blend and transform data

- **Column management** — hide unused Xero fields, rename them into plain labels, reorder them, and set types where you need to.
- **Join** — connect Xero data on a shared key: Invoices to Contacts by contact, or Time by projects to Projects by project ID.
- **Append** — stack the same entity or report from several Xero organisations into one dataset, with a column showing which one each row came from.
- **Aggregate** — total line items or journal lines by month, account, or tracking category before the data reaches Data Studio.
- **Custom SQL** — write your own query when you need logic the other transformations do not offer.

### Step 5. Data Studio destination

Pick Data Studio as the destination. Coupler.io builds the data source through its own Data Studio connector, which you authorize once. Sign in to Data Studio and Coupler.io with the same Google account; when the two accounts differ, the connector cannot find the flow, and that mismatch causes most failed first setups.

- **Report / data source URL** — optional. Finance pack already built? Link it by pasting the report or data source address (`https://datastudio.google.com/reporting/...`). The flow then belongs to that report, and opening it from Coupler.io lands you on it rather than on a blank one.

You do not set up fields yourself. Coupler.io reads the types from the Xero data, so invoice and due dates are real dates that respond to date range controls, and totals and amounts due are numbers you can sum or average. The first successful run has to happen before you start building the report and before a schedule can be turned on. One Data Studio report can take several Xero flows as separate data sources, for example invoices on one page and Profit And Loss on another.

### Step 6. Schedule

Choose a refresh rhythm: as frequently as every 15 minutes, or hourly, daily, weekly, or monthly. Each run can replace the previous data, which is right for nearly every dashboard because it shows the current state of the books, or append to it, which builds a log over time, such as a monthly snapshot of Aged Receivables By Contact. Keep in mind that Data Studio holds a cached copy and reloads it on its own cycle, every 12 hours unless you change it. Use **Refresh data** from the report's menu when you need the newest run on screen immediately.

### Bonus: or just ask the AI Agent to build it for you

You can also hand the setup to the Coupler.io AI Agent, which sits in the right sidebar of the Coupler.io app. Describe the dashboard you are after:

> *"Create flows from Xero to Data Studio: authorised and paid invoices split by line item, changed in the last 12 months, and the Xero Reports Profit And Loss for this year in date-by-row format by month. I am building a revenue and margin dashboard for our monthly board meeting."*

The Agent picks the sources, data entity, report, filters, and structure. These parts still need you:

1. **Connect Xero** — authorizing access to Xero stays in your hands.
2. **Pick the organisation** — choose the Xero tenant for each flow.
3. **Authorize the Data Studio connector** — using the Google account you sign in to Coupler.io with.
4. **Say where the data goes** — link an existing report by URL, or let Coupler.io create a new data source.

Then switch to Data Studio and design the charts and controls your board will look at.

## What data can you export from Xero to Data Studio with Coupler.io?

Xero covers 66 options across two Coupler.io sources: 57 data entities in the Xero source and 9 reports in Xero Reports. Because a flow carries a single entity or report, finance dashboards tend to draw on a handful of flows. Coupler.io's **Join** attaches contacts or projects to the transactions, and **Append** stacks organisations together, before anything reaches Data Studio; blending separate data sources inside the Data Studio report remains an option if you prefer it.

Accounting entities:

- **Accounts** — the chart of accounts with code, type, and status. Every P&L and balance chart groups by it.
- **Bank transactions** — spend and receive money transactions on your bank accounts, the closest view of real cash movement.
- **Bank transfers** — moves between your own bank accounts, kept apart from income and spending.
- **Branding themes** — the invoice and quote templates in use.
- **Contact groups** — the groups you have sorted contacts into, ready-made segments for revenue charts.
- **Contacts** — customers and suppliers with addresses, payment terms, and balances.
- **Credit notes** — credits issued or received, with the invoices they offset.
- **Currencies** — the currencies enabled for the organisation.
- **Employees** — employee records held in the accounting side of Xero.
- **Expense claims** — staff expense claims and their status.
- **Invoices** — sales and purchase invoices with contact, dates, totals, amount due, and status. Split by line item for product and account revenue charts.
- **Items** — products and services with sale and purchase prices.
- **Journals** — every journal Xero posted, line by line. The full audit trail behind the reports.
- **Linked transactions** — billable expenses linked to the customer they will be charged to.
- **Manual journals** — adjustments entered by hand, with narration.
- **Organisation** — settings such as base currency and financial year end.
- **Overpayments** — money received or paid beyond the invoice amount, waiting to be allocated.
- **Payments** — payments applied to invoices and credit notes, with dates. The base for days-to-pay charts.
- **Prepayments** — amounts paid before an invoice exists.
- **Purchase orders** — orders sent to suppliers, with status and delivery date.
- **Receipts** — expense receipts recorded in the organisation.
- **Repeating invoices** — recurring invoice schedules, a preview of future billing.
- **Tax rates** — the tax rates set up and their components.
- **Tracking categories** — custom dimensions like region or department, with their options.
- **Users** — people with access to the organisation and their roles.
- **Quotes** — quotes sent to customers with status and expiry date.

Payroll entities (United Kingdom or New Zealand):

- **Benefits** — the benefit types set up in payroll.
- **Deductions** — deduction types applied to pay.
- **Earning rates** — the pay rates used for earnings lines.
- **Earnings orders (Statutory deductions)** — court-ordered and other statutory deductions.
- **Employees (UK or NZ)** — payroll employee records.
- **Leave types** — the kinds of leave employees can take.
- **Pay run calendars** — the schedules pay runs follow.
- **Pay runs** — each pay run with period, status, and totals. Labor cost by month starts here.
- **Reimbursements** — reimbursement types paid through payroll.
- **Accounts (UK or NZ)** — the accounts payroll posts to.
- **Timesheets** — hours submitted by employees, with status.
- **Tracking categories (UK or NZ)** — tracking categories used by payroll.

Payroll entities (Australia):

- **Employees (AU)** — payroll employee records for Australian organisations.
- **Leave applications** — leave requested by employees.
- **Leave applications with leave periods** — the same, broken out by each leave period.
- **Earnings rates** — pay rates for earnings lines.
- **Deduction types** — deduction categories set up in payroll.
- **Leave types** — leave categories and their settings.
- **Reimbursement types** — reimbursement categories paid through payroll.
- **Pay runs** — pay runs with period, status, and wage totals.
- **Payroll calendars** — the pay cycles in use.
- **Settings** — payroll settings for the organisation.
- **Accounts (AU)** — the accounts payroll posts to.
- **Tracking categories (AU)** — tracking categories used in payroll.
- **Super funds** — superannuation funds linked to employees.
- **Timesheets** — submitted timesheets with status.
- **Timesheets with timesheet lines** — timesheets broken out to individual lines, for hours by day and earnings rate.

Projects entities:

- **Projects** — each project with contact, status, estimate, and deadline.
- **Tasks by projects** — tasks inside each project, with rate and estimated time.
- **Time by projects** — time entries per project and task, with duration and whether they are invoiced.
- **Users** — the people who log time on projects.

> **Note:** The reports below are available in the **Xero Reports** source in Coupler.io, separate from the Xero source above. Pick Xero Reports when you create the flow, then choose the report in **Report type**.

- **Aged Payables By Contact** — what you owe one supplier, bill by bill, with paid and due amounts as of the chosen **Date**. This is the default report.
- **Aged Receivables By Contact** — what one customer owes you, invoice by invoice, aged as of the chosen date.
- **Balance Sheet** — assets, liabilities, and equity at month end, with optional comparison periods.
- **Bank Statement** — the statement lines for one bank account between two dates.
- **Bank Summary** — opening balance, cash in, cash out, and closing balance for each bank account.
- **Budget Summary** — budgeted amounts by account for up to twelve periods.
- **Executive Summary** — monthly totals plus common ratios such as gross profit and debtor days.
- **Profit And Loss** — income and expenses for the period, optionally split by tracking category or compared across months.
- **Trial Balance** — debit and credit balances for every account on a date.

## Why export Xero to Data Studio — real life cases

These are the Data Studio reports finance teams and accountants set up first once Xero refreshes on its own.

- **Monthly Profit And Loss dashboard**

  Load Profit And Loss from Xero Reports in **Date-by-row format**, with **Period** set to Month and eleven periods to compare, and Data Studio gets a full year of monthly income, cost of sales, and expenses as a time series. Scorecards show gross and net profit for the selected month, and a date range control handles quarter or year views. The board pack chart builds itself.

- **Receivables and collections page**

  Invoices filtered by **Statuses** to Authorised give every open invoice with Contact, Due Date, and Amount Due. Data Studio turns that into an aging bar chart, built with a calculated bucket on days past due, plus a table of the largest overdue invoices. A scheduled email of the page every Monday gives the credit controller the week's call list.

- **Cash flow and bank balance tracker**

  Bank Summary from Xero Reports shows cash in, cash out, and closing balance per bank account; Bank transactions shows what made up those movements. A line chart of closing balance by week, with a filter for each account, answers whether the business can cover next month's payroll without opening Xero.

- **Budget vs actual review**

  Pull Budget Summary and Profit And Loss for the same months, and use Coupler.io's Join to line them up by account and period. Data Studio shows actual against budget with a variance column and red highlights where spending runs ahead. Department heads check it themselves instead of asking finance for an update.

- **Client dashboards for accounting practices**

  An accounting practice can create one flow per client organisation, then make a template report in Data Studio and copy it for each client with that client's data source. Each client gets a shared link to their own Profit And Loss, Balance Sheet, and aged receivables, refreshed daily. Monthly management reports stop being a manual job for the team.

- **Group view across several organisations**

  Coupler.io's Append combines Invoices or Profit And Loss from every Xero tenant into one dataset with an organisation column. In Data Studio, a filter control switches between entities and a stacked chart shows the group total. Owners of several companies see them side by side without logging in to each one.

- **Payroll cost by month and team**

  Pay runs and Timesheets with timesheet lines show wage totals and hours per period. Joined with Tracking categories in Coupler.io, Data Studio charts labor cost by department and month next to revenue. It makes hiring decisions easier to discuss with numbers instead of estimates.

- **Project profitability for service businesses**

  Time by projects, Tasks by projects, and Projects give hours logged, task rates, and project estimates. Data Studio shows estimated versus actual hours per project and the share of time already invoiced. Project managers see overruns while there is still time to talk to the client.

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
- [Connect WooCommerce to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-woocommerce-to-looker-studio.md)
- [Connect YouTube Analytics to Data Studio](https://github.com/coupler-io/top-looker-studio-integrations/blob/main/connect-youtube-analytics-to-looker-studio.md)
