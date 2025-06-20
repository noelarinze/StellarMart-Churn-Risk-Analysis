# Table of Content
- [Project Overview](https://github.com/noelarinze/StellarMart-Churn-Risk-Analysis/edit/main/README.md#Project-Overview) 
- [Data source](https://github.com/noelarinze/StellarMart-Churn-Risk-Analysis/edit/main/README.md#Data-source)
- [Tools](https://github.com/noelarinze/StellarMart-Churn-Risk-Analysis/edit/main/README.md#tools)
- [Exploratory data analysis](https://github.com/noelarinze/StellarMart-Churn-Risk-Analysis/edit/main/README.md#exploratory-data-analysis)
- [Data analysis](https://github.com/noelarinze/StellarMart-Churn-Risk-Analysis/edit/main/README.md#data-analysis)
- [Results](https://github.com/noelarinze/StellarMart-Churn-Risk-Analysis/edit/main/README.md#results)
- [Recommendations](https://github.com/noelarinze/StellarMart-Churn-Risk-Analysis/edit/main/README.md#recommendations)
# Project Overview

This customer churn analysis project was conducted for StellarMart, a retail business, with the goal of identifying customers who are at risk of churning, understanding behavioral patterns, and estimating potential revenue loss. The project uses transaction-level data to highlight revenue and profit vulnerabilities while guiding retention strategies.

# Data Source

The dataset used in this project is a cleaned CSV file titled MyStellarMart_transactions_cleaned.csv. It contains detailed transaction-level information for customers of a retail business. The key fields include:
- Customer_ID: Unique identifier for each customer
- Order_ID: Individual purchase transactions
- Recency_Days: Number of days since the customer’s last purchase
- Total_Amount: Total revenue from the customer
- Profit: Net profit contributed by the customer
- Payment_Method: Method used to complete the transaction
- Churn_Risk_Level: Classified churn risk (Low, Medium, High)

This dataset was designed to simulate real-world customer behavior for churn prediction and analysis in the retail sector.
# Tools Used

To conduct this churn risk analysis project, the following tools were used:
- Microsoft Power BI
Used for interactive data visualization, dashboard creation, and dynamic reporting through slicers and filters. It allowed visual storytelling with charts like donut, bar, pie, and table visuals.
- Microsoft Excel
Used for initial exploration and column review. Also helpful for basic data understanding before importing to Power BI.
- DAX (Data Analysis Expressions)
Used within Power BI to create calculated columns and KPIs such as total revenue, churn rate, profit margins, and percentage revenue at risk. DAX formulas enabled segment analysis and metric computation.

These tools enabled end-to-end analysis, from raw transaction data to actionable churn insights in a visually compelling format.
# Exploratory Data Analysis

## Data Cleaning & Preparation

Data preparation was done in Power BI using Power Query. Key steps included:
	•	Removed duplicate customer entries
	•	Ensured data types were correctly set (numeric, date, text)
	•	Removed blank rows and unnecessary columns
	•	Replaced null values where needed
	•	Validated consistency in payment methods and risk labels

## Feature Engineering

Several new columns and measures were created to support the churn analysis:

Calculated Columns
- Churn_Risk_Level – based on recency (e.g., >90 days = High Risk)
- Customer_Profitability – derived from total amount and profit
- Recency_Group – categorized into ranges (e.g., 0–30, 31–60)

DAX Measures
- Total Revenue = SUM(mystellarmart_transaction_cleaned[TotalAmount])
- Total Profit = SUM(mystellarmart_transaction_cleaned[Profit])
- High Risk Revenue = CALCULATE([Total Revenue], mystellarmart_transaction_cleaned[Churn_Risk_Level] = “High”)
- Percentage Revenue at Risk = DIVIDE([High Risk Revenue], [Total Revenue])
- Customer Count by Risk = COUNTROWS(FILTER(mystellarmart_transaction_cleaned, mystellarmart_transaction_cleaned[Churn_Risk_Level] = “High”))
- Average Recency = AVERAGE(mystellarmart_transaction_cleaned[Recency_Days])

# Data Analysis

The churn analysis was structured to answer critical business questions on risk exposure, customer value, and behavioral signals. The analysis was visualized aa dollows:

### Dashboard: Churn Risk & Revenue Impact

This dashboard highlights the magnitude and business impact of customer churn.

Key Insights:
- Total At-Risk Customers:
→ 1,056 customers identified as at risk of churn.
- Revenue at Risk:
→ €8.71M, representing 47.1% of total revenue.
- Churn Risk Segmentation:
→ Low (47%), Medium (37%), High (16%).
- Top 10 Customers by Spend:
→ Many top spenders fall into Medium/High risk categories.
- Recency Patterns:
→ High-risk customers have the longest inactivity gap (Avg. 65 days); low-risk customers are the most active (Avg. 6 days).
- Profitability by Churn Level:
→ Low-risk customers contribute the highest profit. High-risk customers show reduced margins.
- Revenue by Churn Risk:
→ €9.8M (Low), €6.7M (Medium), €2.02M (High).

# Results 
### 1. Churn Exposure 

In this project, one of the first things aimed at is to understand how many customers were at risk of no longer buying from StellarMart — a situation known in business as customer churn.

To do this, we analyzed a column called Recency_Days, which tells us how many days have passed since each customer last made a purchase.

We set a simple rule:

If a customer hasn’t made a purchase in the last 30 days, we consider them at risk of churn.

This rule helped us classify customers into three groups:
- Low Risk: Very recent purchases
- Medium Risk: Some gap in purchasing behavior
- High Risk: Long time since last purchase (i.e., likely to leave)

What was found?
- Out of the total customer base, 1,056 customers were identified as being at risk (either medium or high risk).
- These customers are responsible for generating a total of €8.71 million in revenue.
- To put this into perspective, 47.1% of StellarMart’s entire revenue comes from these at-risk customers.

This is a red flag for the business. It means nearly half of StellarMart’s income is coming from customers who are likely to stop buying soon if no action is taken.

It also highlights the urgency to:
- Engage with these customers
- Offer them incentives to stay
- Understand why they might be leaving

### 2. Segment-Level Insights

After identifying that 47.1% of revenue was at risk, the next question became:

Who exactly are these customers — and what is known about their behavior?

To answer this, I grouped customers into different risk segments based on how long it had been since their last purchase. This allowed me to analyze the behavior and contribution of each group — High Risk, Medium Risk, and Low Risk.

What I discovered:
- High Risk Customers: 
  These are the customers who haven’t made any purchase in a long time.
  They made up about 23.7% of the customer base.
  Surprisingly, they still account for €4.18 million in revenue, or about 22.6% of total revenue.
  This means even though they’ve gone quiet, they’re are valuable  and shouldn’t be ignored.
- Medium Risk Customers: 
  These are customers who are showing signs of slowing down, but haven’t fully churned yet.
  They represent 25.6% of the customer base.
  They contributed €4.52 million in revenue, around 24.5% of the total.
- Low Risk Customers: 
  These are the most recent and active buyers.
  They account for the remaining 50.7% of customers and contribute around €9.55 million (52.9%) of revenue.


Visual Tool Used:

I visualized this insight using a donut chart that shows the percentage of customers in each churn risk level. Another pie chart showed the revenue share by each risk level, helping me see the imbalance between customer activity and revenue contribution.


This breakdown shows that a small number of customers might be bringing in a large chunk of revenue — but they are slipping away.

It also tells:
- Which groups to focus on first for retention campaigns
- That not all churn risk is equal — high-revenue churners hurt more than low-spending ones
- And that the medium-risk group may still be won back before it’s too late


### 3. Profit vs. Churn Risk Overlap
What was analyzed:
We explored how profitability aligns with churn risk by comparing:
Customer Profitability (Total Profit per Customer)
Churn Risk Level (High, Medium, Low)
This helped me uncover whether the most profitable customers are at risk of leaving — a major red flag for any business.

What was discovered:
A significant portion of high-risk customers had above-average profit contributions.
This meant that not all churn is equal — losing a few high-risk, high-profit customers could have a larger financial impact than losing many low-profit ones.
Some medium-risk customers were also high spenders, representing the next priority for retention efforts.

Visual Tool Used:
A Grouped Bar Chart where:
- Axis = Churn Risk Level
- Bars = Average Profit or Total Profit
This visual made it easy to identify whether high churn risk = high financial risk.

Why this matters:
- Prioritizes retention strategy by revenue impact, not just churn count.
- Helps the business focus resources on saving customers that matter most to the bottom line.
- A great foundation for developing tiered customer retention programs.

# Conclusion
This Churn Risk Analysis provided a comprehensive view into the customer retention landscape at StellarMart, revealing not just how many customers are at risk, but who they are, how much they contribute, and why they might leave. By combining behavior-based metrics (like Recency and Frequency) with financial indicators (like Total Amount and Profit), we transformed raw transactions into actionable customer insights.
The insights were brought to life across a complementary dashboard


### Key Takeaways
- 47% of revenue is at risk from High-risk customers — an urgent issue.
- High-spending customers are present in the churn risk group — not all churn has equal impact.
- Customer segments (by group and behavior) show clear churn patterns that should guide intervention strategies.
Recency and frequency are strong indicators of disengagement — low recency, low frequency = high churn risk.

# Recommendations
- Launch targeted retention campaigns focused on high-risk, high-value customers.
- Reward recent purchasers in the Medium risk group to maintain engagement.
- Monitor churn drivers over time, such as specific payment types or customer tiers.
- Add survey or support ticket integration to identify friction causing customer dropout.
- Use this dashboard as a living tool, updating it monthly/quarterly to track retention progress and refine strategies.

