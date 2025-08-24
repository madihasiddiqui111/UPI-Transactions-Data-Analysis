# UPI-Transactions-Data-Analysis

## Report Link

[https://app.powerbi.com/links/RYTMa_XOb5?ctid=5bcca112-41e4-4d5e-a805-c5ba21ed65b6&pbi_source=linkShare](https://app.powerbi.com/links/l-KkQtN2Yp?ctid=5bcca112-41e4-4d5e-a805-c5ba21ed65b6&pbi_source=linkShare&bookmarkGuid=cb9f4482-9380-48f6-8a11-98981ad87890)

## Problem Statement

This project analyzes UPI Transactions data to understand customer behavior, payment preferences, and transaction patterns.
- It answers key business questions such as:

- Which payment modes are most frequently used?

- What are the peak hours of UPI activity?

- How do transactions vary by age group & gender?

- Which are the top purposes for UPI payments?

- What are the insights on remaining balances and transaction frequency across customers?

- By analyzing these factors, financial service providers and businesses can optimize digital payment strategies, offers, and customer engagement models.

## Steps Followed

**Step 1:** Loaded dataset (InsuranceData.csv) into Power BI Desktop.

**Step 2:** Data cleaning in Power Query

Checked column distributions & quality.

Converted date fields (PolicyStartDate, PolicyEndDate, ClaimDate) into Date format.

Handled missing values in ClaimDate (no claim filed).

**Step 3:** Created Relationships between fact table and supporting dimensions.

**Step 4:** Built DAX Measures for key metrics (Total Transactions, Avg Transaction Value, Balance Remaining, Gender-wise split).

**Step 5:** Designed Trend Analysis (daily, monthly transaction behavior).

**Step 6:** Performed Segmentation (by Age Group, Gender, City, Purpose).

**Step 7:** Published interactive report to Power BI Service.

## DAX Measures Used

Age Group = SWITCH(
    TRUE(),
    DimCustomer[CustomerAge] < 25, "Youth",
    DimCustomer[CustomerAge] BETWEEN 25 && 40, "Young Adults",
    DimCustomer[CustomerAge] BETWEEN 41 && 60, "Middle Age",
    "Senior"
)

Txn by Gender = CALCULATE([Total Transactions], GROUPBY(DimCustomer[Gender]))

Remaining Balance = SUM(Transactions[Balance])

Avg Transaction = AVERAGE(Transactions[TransactionAmount])

Total Value = SUM(Transactions[TransactionAmount])

Total Transactions = COUNT(Transactions[TransactionID])

## Visuals & Interactivity

The report uses a variety of visuals and interactive features:

# Slicers → For Date, Payment Mode, Age Group, Gender, City

# Matrix Visual → Comparison of metrics across customer segments

# Bar Chart → Sum of Balance over months.

# Conditional Formatting → Highlights high/low transaction values

# Bookmarks →

- One for Transactions Overview

- One for Remaining Balance Analysis

# Synced Slicers → Applied across multiple pages for consistent filtering



## Insights
**- Payment Modes:** UPI Lite dominates small-value payments; wallets & bank transfers cover large amounts.

 **- Peak Hours:** Most transactions occur between 6 PM – 10 PM, showing evening activity dominance.

**- Purpose:** Top categories → Shopping, Bill Payments, Recharges.

 **- Age Insights:**

-  Youth (<25) → High in recharges & shopping.

-  Middle Age (40–60) → Focus on bills & transfers.

 **- Gender:** Males dominate transaction count, but females show higher average transaction value.

**- Cities:** Metro cities lead, but Tier-2 cities show fast adoption growth.

## Conclusion

This UPI report provides a holistic view of digital payment behavior. With strong DAX measures, visuals, and interactivity, it enables stakeholders to:
- Identify peak transaction times
  
- Understand customer preferences

- Optimize digital offers & discounts

- With this analysis, businesses and financial institutions can boost UPI adoption, improve customer retention, and maximize growth.
