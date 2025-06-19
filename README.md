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
- Total Revenue = SUM(Transaction[TotalAmount])
- Total Profit = SUM(Transaction[Profit])
- High Risk Revenue = CALCULATE([Total Revenue], Transaction[Churn_Risk_Level] = “High”)
- Percentage Revenue at Risk = DIVIDE([High Risk Revenue], [Total Revenue])
- Customer Count by Risk = COUNTROWS(FILTER(Transaction, Transaction[Churn_Risk_Level] = “High”))
- Average Recency = AVERAGE(Transaction[Recency_Days])

# Data Analysis

The churn analysis was structured to answer critical business questions on risk exposure, customer value, and behavioral signals. The analysis was visualized across two dashboard pages:

### Dashboard 1: Churn Risk & Revenue Impact

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

### Dashboard 2: Customer Behavior & Risk Drivers

This second dashboard (not shown visually here) focused on churn drivers and customer behavior:

Highlights:
- Churn Risk by Payment Method:
→ A 100% stacked chart showed how Credit Card, PayPal, and Debit Card users were distributed across churn levels.
- Customer Profitability Table:
→ A matrix showing individual customers with total amount, recency days, profit, and risk level for quick profiling.
- Recency Group Heatmap or Segmentation:
→ Recency groups (0–30, 31–60, 61–90+) helped visualize which segments are cooling off and need re-engagement.

# Results 
### 1. Churn Exposure 

In this project, one of the first things we aimed to understand was how many customers were at risk of no longer buying from StellarMart — a situation known in business as customer churn.

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

Who exactly are these customers — and what do we know about their behavior?

To answer this, we grouped customers into different risk segments based on how long it had been since their last purchase. This allowed us to analyze the behavior and contribution of each group — High Risk, Medium Risk, and Low Risk.

What we discovered:
- High Risk Customers: 
  These are the customers who haven’t made any purchase in a long time.
  They made up about 23.7% of the customer base.
  Surprisingly, they still account for €4.18 million in revenue, or about 22.6% of total revenue.
  This means even though they’ve gone quiet, they’re valuable and shouldn’t be ignored.
- Medium Risk Customers: 
  These are customers who are showing signs of slowing down, but haven’t fully churned yet.
  They represent 25.6% of the customer base.
  They contributed €4.52 million in revenue, around 24.5% of the total.
- Low Risk Customers: 
  These are the most recent and active buyers.
  They account for the remaining 50.7% of customers and contribute around €9.55 million (52.9%) of revenue.


Visual Tool Used:

We visualized this insight using a donut chart that shows the percentage of customers in each churn risk level. Another pie chart showed the revenue share by each risk level, helping us see the imbalance between customer activity and revenue contribution.


This breakdown shows us that a small number of customers might be bringing in a large chunk of revenue — but they are slipping away.

It also tells us:
- Which groups to focus on first for retention campaigns
- That not all churn risk is equal — high-revenue churners hurt more than low-spending ones
- And that the medium-risk group may still be won back before it’s too late

### 3. Payment Behaviors by Risk Level (Expanded Explanation)
Another key insight I uncovered was how payment method influences churn. By analyzing which payment methods are more common among different risk levels, patterns can be spotted in customer behavior that help predict future churn.

What was discovered:
Credit Card Users:

- These customers were fairly evenly spread across Medium and High risk segments.

- Credit card users are often high-value customers, but their churn risk increases as payment frequency drops.

- The recency gap is more noticeable among credit card users, indicating a lack of engagement with automatic payments.

PayPal Users:

- PayPal customers were predominantly in the Low Risk category, suggesting stronger retention or ease of payment flexibility.

- This could be due to automatic payments or loyalty features associated with PayPal.

Debit Card Users:

- Most debit card users fall into the Medium Risk segment, suggesting moderate engagement, but still some drop-off in activity after a few purchases.

Visual Tool Used:
A stacked bar chart was used to show the breakdown of churn risk across each payment method.

The chart clearly highlights how credit card users make up a large portion of high-risk customers, while PayPal shows stronger retention.

Why this matters to the business
- The analysis of payment methods by churn risk helps target specific payment behaviors for retention efforts.

- PayPal users seem to have better retention, so introducing similar payment flexibility for credit card or debit card users might help reduce churn.

- Targeting credit card users with incentives (e.g., loyalty programs, discounts) might reduce the high-risk churn in that group.

### 4. Recency Group Heatmap (Customer Engagement Timing)
What was analyzed:
In churn analysis, recency refers to how recently a customer made their last purchase. The assumption is simple:
The longer it has been since the last purchase, the higher the risk of churn.
To capture this pattern, we grouped customers based on recency intervals (e.g., 0–7 days, 8–14 days, ..., 120+ days). Then we visualized how many customers fell into each group using a heatmap.

What we discovered:
Most active (low risk) customers had purchased within the last 7 to 14 days.
As the number of days since last purchase increased, the volume of customers in each group dropped sharply — especially beyond the 30-day mark.
A notable cluster of high-risk customers appeared in the 45–60 days group, signaling a potential retention intervention point.

Visual Tool Used:
A heatmap-style bar chart or table was used where:
- Columns = Recency Groups
- Rows = Number of Customers
- Color Gradient = Churn Risk Level or Customer Volume
This gave a quick visual cue showing where the customer base was most and least engaged.

Why this matter to the business: 
This helps identify when to intervene. For example, if you notice churn spikes after 30 days of inactivity, your team can schedule targeted campaigns at Day 25.
Recency trends also help with forecasting churn by identifying time thresholds after which customers tend to disappear.

### 5. Customer Behavior Matrix (Churn Risk vs. Payment Method)
What we analyzed:
To understand how payment behaviors relate to churn, we cross-tabulated two variables:
Churn Risk Level (Low, Medium, High)
Payment Method (e.g., Credit Card, Bank Transfer, Cash, PayPal)
This allowed us to see if certain payment methods were more common among high-risk customers — a signal of behavioral risk patterns.

What wad discovered:
Customers paying with Cash and Bank Transfers showed higher churn risk than those using Credit Cards.
Low-risk customers were more likely to use digital payment methods like Credit Card and PayPal.
This suggested that payment method may correlate with digital savviness or engagement — a valuable insight for marketing and product teams.

Visual Tool Used:
A Matrix Table or Stacked Bar Chart, where:
Axis/Columns = Churn Risk Levels
Rows/Legends = Payment Methods
Values = Count of Customers (or % Share)
This format helped highlight trends across both dimensions at once.

Why this matters:
Helps segment churn interventions. For example, if high churn risk is clustered among bank transfer users, targeted outreach or education might be needed for that group.
It also informs payment optimization strategies — possibly incentivizing card usage or app-based payments, which align with low churn.

### 6. Profit vs. Churn Risk Overlap
What was analyzed:
We explored how profitability aligns with churn risk by comparing:
Customer Profitability (Total Profit per Customer)
Churn Risk Level (High, Medium, Low)
This helped us uncover whether the most profitable customers are at risk of leaving — a major red flag for any business.

What was discovered:
A significant portion of high-risk customers had above-average profit contributions.
This meant that not all churn is equal — losing a few high-risk, high-profit customers could have a larger financial impact than losing many low-profit ones.
Some medium-risk customers were also high spenders, representing the next priority for retention efforts.

Visual Tool Used:
A Grouped Bar Chart or Profit Distribution Table, where:
- Axis = Churn Risk Level
- Bars = Average Profit or Total Profit
This visual made it easy to identify whether high churn risk = high financial risk.

Why this matters:
- Prioritizes retention strategy by revenue impact, not just churn count.
- Helps the business focus resources on saving customers that matter most to the bottom line.
- A great foundation for developing tiered customer retention programs.

# Conclusion
This Churn Risk Analysis provided a comprehensive view into the customer retention landscape at StellarMart, revealing not just how many customers are at risk, but who they are, how much they contribute, and why they might leave. By combining behavior-based metrics (like Recency and Frequency) with financial indicators (like Total Amount and Profit), we transformed raw transactions into actionable customer insights.
The insights were brought to life across two complementary dashboards:

Dashboard 1: Churn Overview
Gave a snapshot of churn segmentation, top spenders, total revenue at risk, and key churn drivers.

Dashboard 2: Customer Behavior & Risk Drivers
Answered the deeper question: Who is at risk — and why? It broke down risk patterns by payment method, customer group, recency behavior, and profit overlap.
These tools give business leaders a data-backed view of customer health, enabling smarter decisions around retention investments.

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

