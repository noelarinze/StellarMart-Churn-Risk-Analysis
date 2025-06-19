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

Dashboard 1: Churn Risk & Revenue Impact

This dashboard highlights the magnitude and business impact of customer churn.

Key Insights:
	1.	Total At-Risk Customers:
→ 1,056 customers identified as at risk of churn.
	2.	Revenue at Risk:
→ €8.71M, representing 47.1% of total revenue.
	3.	Churn Risk Segmentation:
→ Low (47%), Medium (37%), High (16%).
	4.	Top 10 Customers by Spend:
→ Many top spenders fall into Medium/High risk categories.
	5.	Recency Patterns:
→ High-risk customers have the longest inactivity gap (Avg. 65 days); low-risk customers are the most active (Avg. 6 days).
	6.	Profitability by Churn Level:
→ Low-risk customers contribute the highest profit. High-risk customers show reduced margins.
	7.	Revenue by Churn Risk:
→ €9.8M (Low), €6.7M (Medium), €2.02M (High).

⸻

Dashboard 2: Customer Behavior & Risk Drivers

This second dashboard (not shown visually here) focused on churn drivers and customer behavior:

Highlights:
	1.	Churn Risk by Payment Method:
→ A 100% stacked chart showed how Credit Card, PayPal, and Debit Card users were distributed across churn levels.
	2.	Customer Profitability Table:
→ A matrix showing individual customers with total amount, recency days, profit, and risk level for quick profiling.
	3.	(Optional) Recency Group Heatmap or Segmentation:
→ Recency groups (0–30, 31–60, 61–90+) helped visualize which segments are cooling off and need re-engagement.
