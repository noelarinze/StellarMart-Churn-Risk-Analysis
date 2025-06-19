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
