# E-Commerce Sales Analysis

**Portfolio Project #2** by Saurav Shejwal

## Project Background

This project analyzes e-commerce sales data from a Superstore dataset to uncover business insights and trends. The analysis focuses on understanding sales performance, profitability patterns, and customer behavior across different dimensions including time periods, product categories, and customer segments.

The dataset contains 9,994 transaction records spanning multiple years (2015-2016) with 21 columns including order details, customer information, product categories, sales figures, and profit metrics.

## Objectives

The main objectives of this analysis are:

1. **Identify temporal patterns** - Analyze monthly sales and profit trends to understand seasonality and business cycles
2. **Category performance analysis** - Evaluate sales and profit distribution across different product categories and sub-categories
3. **Customer segment insights** - Understand purchasing behavior and profitability across Consumer, Corporate, and Home Office segments
4. **Profitability optimization** - Identify high-performing and underperforming product lines to inform business strategy

## Techniques and Tools Used

### Technologies
- **Python** - Core programming language for data analysis
- **Pandas** - Data manipulation, aggregation, and statistical analysis
- **Plotly Express & Plotly Graph Objects** - Interactive data visualizations
- **Datetime operations** - Time-series data processing

### Analysis Methods
- Data cleaning and type conversion
- Groupby aggregations for multi-dimensional analysis
- Time-series decomposition (monthly, yearly trends)
- Categorical analysis across multiple dimensions
- Ratio calculations (Sales-to-Profit ratios)

## Key Insights

### Monthly Sales and Profit Trends
- **Peak sales months**: November ($352,461) and December ($325,294) show significantly higher sales, indicating strong holiday season performance
- **Peak profit month**: December ($43,369) generates the highest profit
- **Growth pattern**: Sales show an upward trend from January through year-end with September-December being the strongest quarter
- **Lowest performance**: February shows the lowest sales ($59,751) and January has minimal profit ($9,134)

### Category-wise Analysis

**Sales Distribution:**
- Technology: $836,154 (36.4%)
- Furniture: $741,999 (32.3%)
- Office Supplies: $719,047 (31.3%)

**Profit Distribution:**
- Technology: $145,455 (50.8%) - Highest profit margin
- Office Supplies: $122,491 (42.8%)
- Furniture: $18,451 (6.4%) - Lowest profitability despite high sales

**Sub-category Performance:**
- Top sales: Phones ($330,007), Chairs ($328,449), Storage ($223,844)
- Top profit: Copiers, Phones, Accessories
- Concern areas: Tables show significant sales but need profit margin review

### Customer Segment Insights

**Sales-to-Profit Ratios:**
- Consumer: 8.66 (largest segment but lower efficiency)
- Corporate: 7.68 (most efficient profit conversion)
- Home Office: 7.13 (best profit efficiency)

**Key Finding**: While Consumer segment generates highest absolute sales, Corporate and Home Office segments show better profit efficiency, suggesting opportunities for targeted marketing and product mix optimization.

## Conclusions

1. **Seasonal Strategy**: Strong Q4 performance indicates successful holiday season execution. However, Q1 (especially February) requires strategic intervention to boost sales.

2. **Product Portfolio Optimization**: 
   - Technology products drive profitability despite not having the highest sales
   - Furniture category needs margin improvement - high sales but disproportionately low profit
   - Focus on high-margin sub-categories: Copiers, Phones, and Accessories

3. **Customer Segment Strategy**: 
   - Maintain Consumer segment volume while improving margins
   - Expand Corporate and Home Office segments due to superior profit efficiency
   - Develop segment-specific product bundles and pricing strategies

4. **Operational Efficiency**: The Sales-to-Profit ratios reveal opportunities to optimize discounting strategies and operational costs, particularly in the Furniture category and Consumer segment.

## Project Files

- `sales_analysis.pdf` - Complete analysis with visualizations and detailed findings
- `README.md` - This file, project documentation

## About This Project

This is my second portfolio project demonstrating data analysis capabilities using Python's data science stack. The project showcases skills in data manipulation, statistical analysis, and creating actionable business insights from raw data.

---

*Analysis completed: October 2025*
