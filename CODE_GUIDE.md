# E-Commerce Sales Analysis - Code Guide

## Overview
This guide provides step-by-step instructions for running the E-Commerce Sales Analysis project. The project analyzes sales data from a Superstore dataset using Python, Pandas, and Plotly for data analysis and visualization.

## Table of Contents
1. [Prerequisites](#prerequisites)
2. [Installation](#installation)
3. [Project Structure](#project-structure)
4. [Dataset](#dataset)
5. [Running the Analysis](#running-the-analysis)
6. [Code Walkthrough](#code-walkthrough)
7. [Visualizations](#visualizations)

## Prerequisites
- Python 3.7 or higher
- pip (Python package manager)
- Basic understanding of Python and data analysis

## Installation

### Step 1: Install Required Libraries
```bash
pip install pandas
pip install plotly
```

Alternatively, you can install all dependencies using:
```bash
pip install pandas plotly
```

### Required Libraries:
- **pandas**: For data manipulation and analysis
- **plotly.express**: For creating interactive visualizations
- **plotly.graph_objects**: For advanced plotting
- **plotly.io**: For template configuration
- **plotly.colors**: For color palette management

## Project Structure

```
E-Commerce-Sales-Analysis/
│
├── Sample - Superstore.csv    # Dataset file
├── analysis.py                # Main analysis script
├── README.md                  # Project documentation
├── CODE_GUIDE.md             # This guide
└── sales_analysis.pdf        # Detailed analysis report
```

## Dataset

### Dataset Information
- **File**: Sample - Superstore.csv
- **Encoding**: latin-1
- **Rows**: 9,994 entries
- **Columns**: 21 columns

### Key Columns:
- Row ID, Order ID, Order Date, Ship Date
- Ship Mode, Customer ID, Customer Name, Segment
- Country, City, State, Postal Code, Region
- Product ID, Category, Sub-Category, Product Name
- Sales, Quantity, Discount, Profit

## Running the Analysis

### Step 1: Import Libraries
```python
import pandas as pd
import plotly.express as px
import plotly.graph_objects as go
import plotly.io as pio
import plotly.colors as colors

# Set default template
pio.templates.default = "plotly_white"
```

### Step 2: Load the Dataset
```python
# Load data with latin-1 encoding
data = pd.read_csv('Sample - Superstore.csv', encoding='latin-1')

# Display first few rows
print(data.head())
```

### Step 3: Data Exploration
```python
# View dataset info
data.info()

# Get statistical summary
data.describe()
```

## Code Walkthrough

### 1. Data Preprocessing

#### Converting Date Columns
```python
# Convert Order Date to datetime
data['Order Date'] = pd.to_datetime(data['Order Date'])

# Convert Ship Date to datetime
data['Ship Date'] = pd.to_datetime(data['Ship Date'])

# Verify the conversion
data.info()
```

#### Creating Date Features
```python
# Extract month, year, and day of week
data['Order Month'] = data['Order Date'].dt.month
data['Order Year'] = data['Order Date'].dt.year
data['Order Day of Week'] = data['Order Date'].dt.dayofweek

# View the new columns
print(data.head())
```

### 2. Monthly Sales Analysis

```python
# Aggregate sales by month
sales_by_month = data.groupby('Order Month')['Sales'].sum().reset_index()

print(sales_by_month)

# Create line chart
fig = px.line(sales_by_month, 
              x='Order Month', 
              y='Sales',
              title='Monthly Sales Analysis')
fig.show()
```

**Key Insights:**
- Peak sales months: September ($307,649.95), November ($352,461.07), December ($325,293.50)
- Lowest sales month: February ($59,751.25)

### 3. Sales Analysis by Category

```python
# Aggregate sales by category
sales_by_category = data.groupby('Category')['Sales'].sum().reset_index()

print(sales_by_category)

# Create pie chart
fig = px.pie(sales_by_category, 
             values='Sales', 
             names='Category',
             hole=0.5,
             color_discrete_sequence=px.colors.qualitative.Pastel)

fig.update_traces(textposition='inside', textinfo='percent+label')
fig.update_layout(title_text='Sales Analysis by Category',
                  title_font=dict(size=24))
fig.show()
```

**Sales Distribution:**
- Technology: $836,154.03
- Furniture: $741,999.80
- Office Supplies: $719,047.03

### 4. Sales Analysis by Sub-Category

```python
# Aggregate sales by sub-category
sales_by_subcategory = data.groupby('Sub-Category')['Sales'].sum().reset_index()

print(sales_by_subcategory)

# Create bar chart
fig = px.bar(sales_by_subcategory, 
             x='Sub-Category', 
             y='Sales',
             title='Sales Analysis by Subcategory')
fig.show()
```

**Top Sub-Categories:**
- Phones: $330,007.05
- Chairs: $328,449.10
- Storage: $223,843.61
- Tables: $206,965.53
- Binders: $203,412.73

### 5. Monthly Profit Analysis

```python
# Aggregate profit by month
profit_by_month = data.groupby('Order Month')['Profit'].sum().reset_index()

print(profit_by_month)

# Create line chart
fig = px.line(profit_by_month, 
              x='Order Month', 
              y='Profit',
              title='Monthly Profit Analysis')
fig.show()
```

**Profit Trends:**
- Highest profit: December ($43,369.19)
- Strong Q4 performance: September, October, November, December

### 6. Profit Analysis by Category

```python
# Aggregate profit by category
profit_by_category = data.groupby('Category')['Profit'].sum().reset_index()

print(profit_by_category)

# Create pie chart
fig = px.pie(profit_by_category, 
             values='Profit', 
             names='Category',
             hole=0.5,
             color_discrete_sequence=px.colors.qualitative.Pastel)

fig.update_traces(textposition='inside', textinfo='percent+label')
fig.update_layout(title_text='Profit Analysis by Category',
                  title_font=dict(size=24))
fig.show()
```

**Profit by Category:**
- Technology: $145,454.95
- Office Supplies: $122,490.80
- Furniture: $18,451.27

### 7. Profit Analysis by Sub-Category

```python
# Aggregate profit by sub-category
profit_by_subcategory = data.groupby('Sub-Category')['Profit'].sum().reset_index()

# Create bar chart
fig = px.bar(profit_by_subcategory, 
             x='Sub-Category', 
             y='Profit',
             title='Profit Analysis by Sub-Category')
fig.show()
```

### 8. Sales and Profit by Customer Segment

```python
# Aggregate by customer segment
sales_profit_by_segment = data.groupby('Segment').agg({
    'Sales': 'sum',
    'Profit': 'sum'
}).reset_index()

# Define color palette
color_palette = colors.qualitative.Pastel

# Create grouped bar chart
fig = go.Figure()

fig.add_trace(go.Bar(
    x=sales_profit_by_segment['Segment'],
    y=sales_profit_by_segment['Sales'],
    name='Sales',
    marker_color=color_palette[0]
))

fig.add_trace(go.Bar(
    x=sales_profit_by_segment['Segment'],
    y=sales_profit_by_segment['Profit'],
    name='Profit',
    marker_color=color_palette[1]
))

fig.update_layout(
    title='Sales and Profit Analysis by Customer Segment',
    xaxis_title='Customer Segment',
    yaxis_title='Amount'
)

fig.show()
```

### 9. Sales-to-Profit Ratio Analysis

```python
# Calculate sales-to-profit ratio
sales_profit_by_segment['Sales_to_Profit_Ratio'] = (sales_profit_by_segment['Sales'] / 
                                                      sales_profit_by_segment['Profit'])

print(sales_profit_by_segment[['Segment', 'Sales_to_Profit_Ratio']])
```

**Ratio Results:**
- Consumer: 8.66
- Corporate: 7.68
- Home Office: 7.13 (most efficient)

## Visualizations

The project generates the following interactive visualizations:

1. **Monthly Sales Trend Line Chart**: Shows sales patterns throughout the year
2. **Category Sales Pie Chart**: Displays sales distribution across main categories
3. **Sub-Category Sales Bar Chart**: Compares sales across all sub-categories
4. **Monthly Profit Trend Line Chart**: Tracks profit over the year
5. **Category Profit Pie Chart**: Shows profit contribution by category
6. **Sub-Category Profit Bar Chart**: Compares profitability across sub-categories
7. **Segment Analysis Grouped Bar Chart**: Compares sales and profit by customer segment

## Key Findings

1. **Seasonal Trends**: Q4 (Sep-Dec) shows the strongest sales and profit performance
2. **Category Performance**: Technology leads in both sales and profit
3. **Sub-Category Leaders**: Phones and Chairs are top revenue generators
4. **Customer Segments**: Consumer segment has highest sales volume
5. **Efficiency**: Home Office segment has the best sales-to-profit ratio (7.13)

## Troubleshooting

### Common Issues:

**Issue**: `FileNotFoundError` when loading CSV
- **Solution**: Ensure 'Sample - Superstore.csv' is in the same directory as your script

**Issue**: `UnicodeDecodeError` when reading CSV
- **Solution**: Use encoding='latin-1' parameter in pd.read_csv()

**Issue**: Plotly charts not displaying
- **Solution**: 
  - In Jupyter: Charts should display inline
  - In Python scripts: Use `fig.write_html('filename.html')` to save charts
  - Ensure plotly is properly installed

## Next Steps

1. Explore correlation between discount and profit
2. Analyze shipping mode impact on sales
3. Geographic analysis by region and state
4. Customer behavior analysis
5. Product-level profitability analysis
6. Time series forecasting

## Additional Resources

- [Pandas Documentation](https://pandas.pydata.org/docs/)
- [Plotly Python Documentation](https://plotly.com/python/)
- [Plotly Express Guide](https://plotly.com/python/plotly-express/)

## Author

Saurav Shejwal

## License

This project is available for educational and research purposes.

---

For detailed analysis results and visualizations, refer to `sales_analysis.pdf`.
