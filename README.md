# Jumia Product Data Analysis

## Overview
This repository contains an end-to-end data processing, transformation, and analytical model performed on product listings extracted from **Jumia**. The primary goal of this workbook is to evaluate pricing strategies, discount structures, customer engagement, and product ratings across various product offerings.

---

## File Structure & Contents

The workbook **`Excel_Jumia_Product_Analysis.xlsx`** consists of six structured sheets:

| Sheet Name | Description | Key Contents / Function |
| :--- | :--- | :--- |
| `Raw_data` | Initial unprocessed dataset | Product titles, current prices (`KSh`), old prices, discount percentages, raw review counts, and customer ratings. |
| `Cleaned_data` | Cleaned and feature-engineered dataset | Standardized numerical formats, calculated discounts, threshold categories, status verifications, and engagement metrics. |
| `Analysis` | Statistical summary and metrics | Summary statistics, price bounds (min/max), mean values, total reviews, and correlation analysis between ratings and discount strategies. |
| `Pivot Tables` | Aggregated pivot tables | Breakdown of product counts by Rating Category, Discount Tier, and Average Rating by Price Tier. |
| `Dashboard` | Interactive visual dashboard | Slicers, KPI cards, and charts summarizing key e-commerce performance indicators. |
| `Data Dictionary` | Metadata documentation | Definitions and descriptions of all attributes used in the cleaned dataset. |

---

## Data Cleaning & Feature Engineering

The raw data underwent several cleaning and transformation steps in the `Cleaned_data` tab:

1. **Numeric Standardizations:**
   * Stripped currency indicators (`KSh`) and formatted `Current Price` and `Old Price` into standard numeric values.
   * Converted raw text ratings (e.g., `"4.5 out of 5"`) into standalone float values (`4.5`).
   * Processed negative review flags into positive absolute engagement counts.

2. **Categorical Classifications:**
   * **Price Category:** Categorized into `High Price`, `Medium Price`, and `Low Price` bands.
   * **Discount Category:** Grouped based on calculated discount percentage:
     * `Low Discount`: $< 20\%$
     * `Medium Discount`: $20\% - 40\%$
     * `High Discount`: $> 40\%$
   * **Rating Category:** Segmented ratings into `Excellent` ($\ge 4.6$), `Average` ($3.0 - 4.5$), `Poor` ($< 3.0$), or `Missing`.

3. **Data Quality & Validation Flags:**
   * `Check Discount` / `Checking Rating`: Formula checks verifying whether advertised discounts match calculated figures ($\frac{\text{Old Price} - \text{Current Price}}{\text{Old Price}}$).
   * `Engagement Strength`: Classified into `Strong Engagement` vs. `Weak Engagement` based on review volumes and ratings.
   * `High Discount + Low Rating` & cross-variable flags to identify underperforming or clearance products.

---

## Summary Statistics

* **Total Products Analyzed:** 112 listings
* **Average Current Price:** KSh 1,186.69
* **Average Original Price:** KSh 1,811.11
* **Average Discount:** ~37%
* **Average Customer Rating:** 3.89 / 5.00
* **Total Reviews:** 678
* **Price Range:** KSh 38 (Minimum) to KSh 3,750 (Maximum)

---

## Key Findings & Aggregations

1. **Rating Distribution:**
   * **Excellent ($\ge 4.6$):** 19 products
   * **Average ($3.0 - 4.5$):** 26 products
   * **Poor ($< 3.0$):** 12 products
   * **Missing Ratings:** 55 products

2. **Discount Distribution:**
   * **High Discount ($> 40\%$):** 62 products
   * **Medium Discount ($20\% - 40\%$):** 32 products
   * **Low Discount ($< 20\%$):** 18 products

3. **Price vs. Rating Insights:**
   * Higher-priced products maintain a slightly higher average rating (**4.08 / 5**) compared to medium-priced (**3.88 / 5**) and lower-priced items (**3.64 / 5**).

---

## Requirements & Tools
* **Excel / Google Sheets:** Microsoft Excel 2016 or higher recommended (supports Slicers and Pivot Tables).
* **Python (Optional for Automation):** `pandas`, `openpyxl` for reading and reprocessing dataset pipeline.
