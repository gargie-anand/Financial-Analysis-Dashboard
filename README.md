# Financial-Analysis-Dashboard
- This dashboard provides a comprehensive financial overview of FestMan Stores, highlighting key trends in sales, profitability, discount strategies, and regional performance. The analysis compares current performance with the previous year and identifies major drivers of business growth.

## Table of Content
- [Problem Statement](https://github.com/gargie-anand/Financial-Analysis-Dashboard/edit/main/README.md#problem-statement)
- [Tools Used](https://github.com/gargie-anand/Financial-Analysis-Dashboard/edit/main/README.md#tools-used)
- [Data Source](https://github.com/gargie-anand/Financial-Analysis-Dashboard/edit/main/README.md#data-source)
- [Data Preparation](https://github.com/gargie-anand/Financial-Analysis-Dashboard/edit/main/README.md#data-preparation)
- [DAX Codes](https://github.com/gargie-anand/Financial-Analysis-Dashboard/edit/main/README.md#dax-codes)
- [Dashboard](https://github.com/gargie-anand/Financial-Analysis-Dashboard/edit/main/README.md#dashboards)
- [Insights](https://github.com/gargie-anand/Financial-Analysis-Dashboard/edit/main/README.md#insights)

## Problem Statement
To create a Power BI dashboard to clearly show sales, profit, discounts, and performance across countries and products.

## Tools Used
Microsoft Power BI

## Data Source
Financial-Analysis Dataset: 

## Data Preparation
After importing the csv file `Financial_Data_Sample`, cleaned the data in the power query.

Dataset contains `1` table; `16 columns` and `5701 rows`.
- The headers were promoted.
- Data types were adjusted.

## DAX Codes

### Measures Used:

- Discount Offered = `SUM(Financials[Discounts])`
- Discount Offered LY = `CALCULATE([Discount Offered], DATEADD('Date Table'[Date],-1,YEAR))`
- Orders = `SUM(Financials[Units Sold])`
- Orders LY = `CALCULATE([Orders], DATEADD('Date Table'[Date],-1,YEAR))`
- Profit = `SUM(Financials[Profit])`
- Profit LY = `CALCULATE([Profit], DATEADD('Date Table'[Date],-1,YEAR))`
- Profit Margin = `DIVIDE([Profit],[Sales Amount])`
- Profit Margin LY = `CALCULATE([Profit Margin], DATEADD('Date Table'[Date],-1,YEAR))`
- Sales Amount = `SUM(Financials[Net Sales])`
- Sales Amount LY = `CALCULATE([Sales Amount], DATEADD('Date Table'[Date],-1,YEAR))`
- Top 3 product by Sales = 
  `CALCULATE([Sales Amount],TOPN(3,ALLSELECTED(Financials[Product]),
    [Sales Amount],DESC),VALUES(Financials[Product]))`
- Top Highlight = 
  `IF(ISBLANK([Top 3 product by Sales]),0,1)`

### Table Used
- Date Table = 
 
   `ADDCOLUMNS(CALENDARAUTO(),
   "Month No", MONTH([Date]),
   "Month Name", FORMAT([Date], "MMM"),
   "Year", YEAR([Date])
   )`

## Dashboard

### Overall Business Performance
- FestMan Stores shows strong year-over-year growth across all key financial indicators.
- Total Sales: 12.66M (↑ 200.7% YoY)
- Total Orders: 5.10M (↑ 197.2% YoY)
- Total Profit: Significant increase consistent with sales growth
- Profit Margin: Stable at 40.3%
- Total Discounts: Increased by 205%, supporting higher sales volume

### Country-Level Performance
- Profit margins are relatively consistent across countries, ranging from 37.8% to 41.7%, indicating balanced international performance.
- Mexico and the United States show the highest profit margins.
- France has the lowest margin but remains profitable.
- Order volumes are highest in Mexico and Canada, indicating strong demand in these markets.

This suggests that the company maintains stable pricing and cost structures across regions.

The results indicate that aggressive sales expansion combined with strategic discounting contributed to substantial revenue growth, while maintaining healthy profitability.

### Segment Performance

- Profitability varies slightly across business segments:
- Channel Partners and Government segments show the highest margins (~42%)
- Midmarket and Enterprise segments show moderate margins (~39–40%)
- Small Business segment shows the lowest margin (~37%)

Higher margins in Government and Channel Partner segments indicate efficient large-volume transactions and lower relative costs.

### Product Performance

- Sales are concentrated among a few key products:
- Paseo is the top-selling product by a significant margin.
- VTT and Velo are the next strongest performers.
- Carretera and Montana contribute smaller but consistent sales volumes.

This indicates a strong dependency on top-performing products, particularly Paseo.

### Discount Strategy Analysis

Discount distribution shows:

- High Discounts: 71%
- Medium Discounts: 23%
- Low Discounts: 6%

The company relies heavily on high discounting strategies to drive sales volume.
Despite this, profit margins remain above 40%, suggesting that discounts are well-managed and financially sustainable.

### Sales Trends Over Time

Monthly sales trends indicate steady growth throughout the year, with minor fluctuations.

- Sales peak during mid-year periods.
- The final month shows a sharp drop, likely due to partial-month or incomplete data.

Overall, the trend indicates consistent business expansion.

## Insights
- Sales and orders have increased significantly compared to last year, showing strong business growth.
- Profit margin has slightly decreased compared to last year, although the company remains profitable.
- Most sales come from high discount offers, showing that discounts play an important role in driving sales.
- Paseo is the top-performing product and contributes the highest share of total sales.
- Sales performance is fairly consistent across different countries and business segments.
- Government and Channel Partner segments show relatively higher profitability compared to other segments.
