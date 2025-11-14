# Business_Synopsis
Integrated sales analytics project that merges order, order-detail and target datasets to evaluate category-level sales and profitability, month-over-month target achievement, and regional performance by state. Includes identification of top/underperforming segments, regional disparities, and data-driven recommendations for performance improvement.
# Sales and Profitability Analysis Project

## Overview

This project provides comprehensive analysis of sales data across three main categories (Clothing, Electronics, and Furniture) to evaluate performance metrics, profitability trends, target achievement, and regional performance insights. The analysis is divided into three main parts: Sales & Profitability Analysis, Target Analysis with Month-over-Month trends, and Regional Performance Insights.

## Project Structure

The analysis uses three main datasets:

* `Sales_target_1.xlsx` \- Sales targets by category and month
* `List_of_Orders_1.xlsx` \- Order information including location data
* `Order_Details_1.xlsx` \- Detailed order information with amounts and profits

## Dependencies

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

## Installation

```bash
pip install pandas numpy matplotlib 
```

## Data Loading

The project begins by loading three Excel datasets into pandas DataFrames:

```python
sales = pd.read_excel(r"Your_File_Path")
orders_list = pd.read_excel(r"Your_File_Path")
order_details = pd.read_excel(r"Your_File_Path")
```

## Analysis Parts

### Part 1: Sales and Profitability Analysis

#### Question 1: Calculate the total sales (Amount) for each category across all orders. 

Calculates total sales for each category by merging order data:
```
python
merged_df = pd.merge(
    orders_list,
    order_details,
    on="Order ID",   
    how="inner"      
)

category_sales = (
    merged_df
    .groupby("Category", as_index=False)["Amount"]
    .sum()
    .rename(columns={"Amount": "Total Sales"})
)

print(category_sales)
```

**Key Findings:**

* **Electronics**: ₹165,267 (highest revenue)
* **Clothing**: ₹139,054
* **Furniture**: ₹127,181 (lowest revenue)

#### Question 2: Profit Metrics Analysis

Computes comprehensive profit metrics including:

* Average profit per order
* Total profit margin percentage
* Unique order counts per category

**Key Metrics:**

| Category | Avg Profit/Order | Profit Margin % |
| -------- | ---------------- | --------------- |
| Electronics | ₹51.44 | 6.35% |
| Clothing | ₹28.40 | 8.03% |
| Furniture | ₹12.35 | 1.81% |

#### Question 3: Performance Classification

**Top Performers:**

* **Total Sales**: Electronics (₹165,267)
* **Profit Margin**: Clothing (8.03%)
* **Profit per Order**: Electronics (₹51.44)

**Underperformers:**

* **Furniture** consistently ranks lowest across all metrics

**Category Analysis:**

* **Clothing**: High margin, high volume, steady demand with best profit margin (8.03%)
* **Electronics**: Revenue leader with highest profit per order but competitive pricing pressure
* **Furniture**: Underperformer with extremely thin margins (1.81%) due to high logistics costs

### Part 2: Target Analysis and Trends

#### Question 1: Month-over-Month Target Changes

Analyzes target fluctuations for Furniture category:

**Key Observations:**

* Furniture targets show relatively stable month-over-month changes
* Largest drop: -11.86% in April 2025
* Generally maintains targets between ₹10,400 - ₹11,800

#### Question 2: Significant Target Fluctuations

Identifies months with target changes >15%:

**Significant Changes Detected:**

* **Clothing**: -25% in April, +16.67% in July
* **Electronics**: -43.75% in April (most dramatic change)
* **Furniture**: No changes exceeding 15% threshold

**Visualization Features:**

* Monthly target trend lines by category
* Month-over-Month percentage change charts
* Total portfolio target analysis
* Statistical distribution analysis with bell curves

### Part 3: Regional Performance Insights

#### Question 1: Top 5 States Analysis

**Top 5 States by Order Count:**

1. **Madhya Pradesh**: 101 orders, ₹105,140 sales, ₹16.33 avg profit
2. **Maharashtra**: 90 orders, ₹95,348 sales, ₹21.30 avg profit
3. **Rajasthan**: 32 orders, ₹21,149 sales, ₹16.99 avg profit
4. **Gujarat**: 27 orders, ₹21,058 sales, ₹5.34 avg profit
5. **Punjab**: 25 orders, ₹16,786 sales, -₹10.15 avg profit (loss)

#### Question 2: Regional Disparities

**High Performers:**

* **Uttar Pradesh**: 14.48% profit margin, ₹147.14 profit/order
* **West Bengal**: 17.75% profit margin, ₹113.64 profit/order
* **Delhi**: 13.26% profit margin, ₹135.77 profit/order

**Underperformers:**

* **Tamil Nadu**: -36.41% profit margin (significant losses)
* **Punjab**: -3.63% profit margin
* **Andhra Pradesh**: -3.74% profit margin

## Key Business Insights

### Category Performance Summary:

1. **Electronics** drives revenue but faces margin pressure
2. **Clothing** offers best profitability with consistent demand
3. **Furniture** requires strategic review due to poor performance across all metrics

### Target Setting Insights:

* April 2025 shows significant target reductions across categories
* Electronics targets show highest volatility
* Overall target management appears reactive rather than strategic

### Regional Insights:

* Strong performance concentration in Northern and Western states
* Southern states (Tamil Nadu, Andhra Pradesh) show profitability challenges
* Madhya Pradesh and Maharashtra drive volume but need margin optimization

## Output Files

The analysis generates the following output file:

* `Top5_States_Sales_Profit_Summary.xlsx` \- Summary of top 5 states by order count

## Visualizations

The project includes comprehensive visualizations:

* Category sales comparison charts
* Monthly target trend analysis
* Month-over-Month change tracking
* Regional performance comparisons
* Statistical distribution plots

## Usage

1. Update file paths in the data loading section to match your local directory
2. Run each section sequentially for complete analysis
3. Modify category filters and thresholds as needed for specific analysis requirements
4. Use the visualization outputs for presentation and decision-making

## Business Applications

This analysis supports:

* Category portfolio optimization decisions
* Regional expansion and resource allocation strategies
* Target setting and performance management
* Pricing and margin improvement initiatives
* Operational efficiency improvements across categories and regions
