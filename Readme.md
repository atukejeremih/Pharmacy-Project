# Pharmacy Chain Distributor Across Europe — Data Analysis Report

**Prepared by:** Data Analytics Team
**Reporting Period:** January 2024 – December 2025
**Dataset:** 62,139 sales transactions | 120 pharmacies | 220 products | 8 countries

---

## (a) Executive Summary

Between January 2024 and December 2025, the pharmacy chain generated **€8.63M in total revenue** across 120 stores in 8 European countries (Austria, Belgium, France, Germany, Italy, Netherlands, Poland, and Spain), producing **€2.42M in gross margin** — a blended margin rate of **28.0%**. The business sold **445,793 units** across 220 products spanning five categories: Prescription, OTC, Wellness, Personal Care, and Medical Devices.

Performance was broadly stable and modestly growing: revenue rose from **€4.22M in 2024 to €4.41M in 2025 (+4.4% YoY)**, with no signs of seasonal collapse — monthly revenue held in a tight €327K–€393K band throughout the two years, with a mild summer uplift each year.

Germany, France, and Italy are the top three revenue markets, together contributing roughly **48%** of total revenue, while Austria and Poland are the smallest markets. Margin rate is consistent across countries (all between 27.8% and 28.2%), indicating pricing and cost discipline is applied uniformly across geographies rather than being a country-specific issue.

At the category level, **Prescription** is the largest revenue driver (€2.80M, 32% of revenue) but carries the **lowest margin rate (21.9%)**, while **Wellness** and **Personal Care** are smaller in revenue but the most profitable categories (33.6% and 33.5% margin respectively). Promotional sales, while only 12% of transactions, are associated with a noticeably **lower margin rate (19.9% vs. 29.0% on non-promo sales)**, suggesting promotions are eroding profitability more than they are driving incremental volume.

Store performance varies significantly: the top 10 pharmacies each generate €135K–€162K in revenue, while several recently opened stores (partial trading year) sit well below €25K. Urban stores and Medium-sized stores are the strongest performing segments overall.

---

## (b) Business Problem

The pharmacy chain's leadership team lacks a consolidated, cross-market view of sales, profitability, and store/product performance. Data currently sits in disconnected transactional, store, and product records, making it difficult to answer fundamental commercial questions such as:

- Which countries, regions, and individual pharmacies are over- or under-performing, and why?
- Which product categories and brands are the most profitable — not just the highest-selling?
- Is the promotional strategy actually profitable, or is it discounting margin away without a matching lift in volume?
- Are newly opened stores ramping up as expected, and are underperforming stores a location issue or a maturity (time-since-opening) issue?
- How is the business trending over time — is growth being driven by volume, price, or mix?

Without a structured, reliable analytical view of this data, the business risks making resourcing, pricing, promotion, and expansion decisions based on incomplete or anecdotal information rather than evidence.

---

## (c) Objective

The objective of this analysis is to:

1. Consolidate the four related data tables (**FactSales, DimDate, DimPharmacy, DimProduct**) into a single, relationship-driven analytical model.
2. Calculate core commercial KPIs — **Revenue, Cost, Margin, Margin %, Units Sold** — at the overall, country, category, and store level.
3. Identify top and bottom performing pharmacies, products, and brands to guide operational and commercial decisions.
4. Quantify the impact of **promotions** and **generic vs. branded** products on profitability.
5. Surface time-based trends (year-over-year and month-over-month) to distinguish genuine growth from seasonal noise.
6. Translate these findings into clear, actionable recommendations for commercial and operations stakeholders.

---

## (d) Tools

| Tool | Purpose |
|---|---|
| **Microsoft Excel** | Source data format (star-schema workbook: FactSales, DimDate, DimPharmacy, DimProduct) |
| **Python (pandas)** | Data consolidation, joining of fact/dimension tables, aggregation, and KPI calculation |
| **Power BI** (recommended for ongoing reporting) | Interactive dashboarding using the documented star-schema relationships (DimDate/DimPharmacy/DimProduct → FactSales) and pre-built hierarchies (Geography, Product, Time) |
| **Markdown** | Structured report documentation |

The dataset is pre-modeled as a classic **star schema** — one fact table (`FactSales`) with three dimension tables joined on `DateKey`, `PharmacyID`, and `ProductID` — which made it directly suitable for both the Python analysis performed here and for one-to-one loading into Power BI using the relationships documented in the workbook's README.

---

## (e) Recommendations

1. **Review promotional strategy.** Promoted transactions carry a margin rate of 19.9% versus 29.0% for non-promoted sales — a ~9-point margin gap. Audit promo depth/eligibility by category (Prescription and OTC in particular) to confirm promotions are driving incremental volume rather than simply discounting sales that would have happened anyway.

2. **Protect margin on Prescription products.** Prescription is the single largest revenue category (32% of total) but the weakest margin (21.9%, ~6 points below the company average). Given its scale, even a small margin improvement here (via cost negotiation or pricing review) would have an outsized impact on total company profit.

3. **Double down on Wellness and Personal Care.** These two categories combine strong revenue (a combined €3.17M) with the best margins in the portfolio (33.6% and 33.5%). Consider expanding shelf space, marketing focus, or new product introductions in these categories.

4. **Investigate underperforming stores individually rather than as a category.** Several of the lowest-revenue stores (e.g., Vienna HealthPoint #115, Frankfurt HealthPoint #084, Seville HealthPoint #040) opened in 2025 and simply have less trading history in the dataset — their low totals are a maturity effect, not necessarily a location or management issue. Store performance should be evaluated on a **revenue-per-day-open** basis, not raw cumulative revenue, before flagging a store as underperforming.

5. **Study the top-10 pharmacy playbook.** The leading stores (Munich #095, Rotterdam #023, Utrecht #058, Brussels #078, Liège #010) all generate 3–4x the average store's revenue. Understanding what these locations have in common (store size, urban positioning, product mix, local demographics) could inform site selection for future openings.

6. **Prioritize Germany, France, and Italy for continued investment**, as they represent the largest markets (48% of revenue combined) with consistent ~28% margins, while treating Austria and Poland as smaller, stable markets worth monitoring rather than immediate expansion targets.

7. **Build this into a live Power BI dashboard** using the star-schema relationships already defined in the source workbook, so that country, category, store, and promo performance can be monitored on an ongoing basis rather than through a point-in-time report.

---

## (f) Conclusion

The pharmacy chain's two-year performance (2024–2025) shows a stable, modestly growing business (+4.4% YoY) with a consistent ~28% margin across all eight countries — evidence of disciplined, uniform pricing and cost management at the geography level. However, profitability is not evenly distributed across the business: **Prescription products drive the most revenue but the least margin**, while **Wellness and Personal Care products are smaller but far more profitable**, and **promotional sales are measurably less profitable than non-promoted sales**. These patterns represent the highest-value opportunities for margin improvement without requiring revenue growth.

At the store level, performance is led by a clear group of top-10 pharmacies generating multiples of the network average, while several of the lowest-revenue stores are simply newer openings rather than genuine underperformers. Correcting for store maturity is essential before making any store-level operational decisions.

Overall, the dataset supports a clear, evidence-based set of next steps: rebalance category and promotional strategy toward margin, validate underperforming stores against their opening date, and replicate the characteristics of top-performing pharmacies across the network — all of which can be operationalized through a live Power BI dashboard built on the existing star-schema data model.
