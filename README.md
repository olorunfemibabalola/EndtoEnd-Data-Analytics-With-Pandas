# ASOS E-Commerce Data Analytics: Phantom Revenue & Inventory Analysis

![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Seaborn](https://img.shields.io/badge/Seaborn-3776AB?style=for-the-badge&logo=python&logoColor=white)

## 📌 Project Overview
This project is an end-to-end data analytics pipeline designed to extract actionable business intelligence from ASOS e-commerce data[cite: 1]. Built in Python, the workflow focuses on data sanitization, custom feature engineering, and exploratory data analysis (EDA) to evaluate brand performance and inventory health[cite: 1]. The core objective is to quantify "Phantom Revenue"—the potential revenue lost due to out-of-stock sizes across different brands[cite: 1].

## 🛠️ Core Logic & Workflow

### 1. Data Ingestion & Sanitization
*   **Safe Loading:** Ingests the raw `products_asos.csv` file while systematically skipping corrupted lines to maintain pipeline stability[cite: 1].
*   **Price Formatting:** Casts the `price` column to a strict numeric format, coercing errors and immediately dropping unrecoverable null values to ensure downstream calculation accuracy[cite: 1].

### 2. Text Parsing & Brand Standardization
*   **String Manipulation:** Implements a custom function (`getBrand`) to parse unstructured text within the `description` column, isolating brand names using specific string delimiters (e.g., 'by The ' or 'by ')[cite: 1].
*   **Data Consolidation:** Utilizes a comprehensive mapping dictionary to clean and standardize highly fragmented brand data (e.g., unifying varying 'Bershka' and 'Monki' promotional strings into single brand entities)[cite: 1]. 
*   **Noise Reduction:** Filters the dataset to only include established brands with a minimum frequency threshold (5+ items) for statistical validity[cite: 1].

### 3. Feature Engineering (Inventory Metrics)
The project constructs new business metrics by analyzing the comma-separated `size` data[cite: 1]:
*   **`Out_of_Stock_Count`:** Calculates the absolute number of unavailable sizes per product[cite: 1].
*   **`Out_of_Stock_Rate`:** Determines the ratio of out-of-stock sizes against the total size range offered for that specific item[cite: 1].
*   **`Lost_Revenue`:** A calculated metric multiplying the `Out_of_Stock_Count` by the item's `price` to quantify the financial impact of poor inventory depth[cite: 1].

### 4. Exploratory Data Analysis & Visualization
*   **Brand Aggregation:** Groups the cleaned dataset by brand to calculate the mean price, mean out-of-stock rate, and total sum of lost revenue for brands with more than 10 products[cite: 1].
*   **Strategic Visualization:** Generates a multi-dimensional scatter plot using Seaborn to map brand strategies[cite: 1]:
    *   **X-Axis:** Average Price[cite: 1].
    *   **Y-Axis:** Out of Stock Rate[cite: 1].
    *   **Bubble Size:** Total Lost Revenue[cite: 1].
*   **Actionable Insights:** Automatically isolates and annotates "Winners" (brands with an average price > £40 and an out-of-stock rate > 40%) to highlight high-value areas suffering from inventory constraints[cite: 1].

## 🚀 How to Run
1.  Upload the `.ipynb` file to Google Colab or your local Jupyter environment.
2.  Ensure `products_asos.csv` is located in the same working directory.
3.  Execute the cells sequentially to reproduce the data cleaning pipeline and visual analysis.

## 📦 Dependencies
*   `pandas`
*   `numpy`
*   `matplotlib.pyplot`
*   `seaborn`


## 💼 Business Takeaways, Next Steps & Conclusions

### The Big Picture (Business Implications)
*   **The Hidden Cost of Sold-Out Sizes:** This project measures "Phantom Revenue"—which is simply the money left on the table when a customer wants to buy an item, but their specific size is out of stock[cite: 1]. 
*   **Expensive Items Hurt the Most:** By comparing average prices to how often items sell out, the data reveals that running out of stock on higher-priced items creates the biggest dent in potential profits[cite: 1].
*   **Not All Brands Struggle Equally:** Inventory issues aren't the same across the board[cite: 1]. Some brands are losing significantly more potential money due to missing sizes than others, meaning a one-size-fits-all approach to inventory won't work[cite: 1].

### What to Do About It (Actionable Insights)
*   **Restock the "Winners" First:** The code specifically highlights "winner" brands—items that cost more than £40 but are missing sizes over 40% of the time[cite: 1]. The purchasing team should rush to restock these specific items right away because we know customers are trying to buy them.
*   **Focus on the Biggest Money Drain:** In the project's chart, the biggest bubbles represent the brands losing the most money[cite: 1]. The supply chain team can use this visual to quickly see which brands they need to reorder on a more frequent schedule.
*   **Order Smarter Next Time:** When placing initial orders for the next season, the company needs to buy a lot more of the core sizes for those expensive, high-demand items to prevent them from selling out so fast[cite: 1].

### The Bottom Line (Conclusions)
This project proves that simply buying more inventory of *everything* is a waste of money. By calculating exactly how much cash is lost when sizes are out of stock[cite: 1], the analysis shows that a smarter approach is needed. The company should focus its budget specifically on keeping those popular, higher-priced brands fully stocked, as that is where the most potential revenue is currently slipping away.
