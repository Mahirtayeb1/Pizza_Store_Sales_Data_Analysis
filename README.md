# 🍕 Pizza Sales Data Analysis Dashboard (Power BI)

> In the competitive world of business, understanding sales data is crucial for improving performance and making calculated decisions. This Power BI project analyzes real-world pizza sales data to uncover key customer preferences, identify sales trends, and provide actionable insights to optimize business performance.

---

## 📂 Dataset
- <a href="https://github.com/Mahirtayeb1/Pizza_Store_Sales_Data_Analysis/blob/main/Dataset/pizza_sales.xlsx"> [Kaggle Pizza Sales Dataset]</a>
- Rows: ~49,000  
- Columns: 9  
- Contents: Order date, order time, pizza name, size, quantity, unit price, etc.


## 🎯 Project Goals

- ✅ Identify the best-selling pizza types and sizes  
- ✅ Understand peak sales periods (morning, afternoon, evening, night)  
- ✅ Analyze sales performance across months  
- ✅ Provide data-driven recommendations to boost revenue and customer satisfaction  

---


## 🛠️ Challenges & Solutions

### 1. ⚠️ Date Format Inconsistency
- **Problem:** Power BI failed to load ~29,000 rows due to inconsistent date formats (DD-MM-YYYY vs DD/MM/YYYY).
- **Solution:**
  - Converted `order_date` to text in Power Query
  - Applied custom M code to reformat dates uniformly
  - Re-converted to Date format after cleaning

### 2. ⏰ Time of Day Categorization
- **Problem:** Needed to segment `order_time` into Morning, Afternoon, Evening, Night
- **Solution:** Created a calculated DAX column:

```DAX
Order_day_phase =
IF(HOUR('pizza_sales'[order_time]) >= 5 && HOUR('pizza_sales'[order_time]) < 12, "Morning",
IF(HOUR('pizza_sales'[order_time]) >= 12 && HOUR('pizza_sales'[order_time]) < 17, "Afternoon",
IF(HOUR('pizza_sales'[order_time]) >= 17 && HOUR('pizza_sales'[order_time]) < 21, "Evening", "Night")))
```

### 3. 💵 Total Revenue Calculation
- **Problem:** Dataset lacked a column for total revenue.

- **Solution:** Created new DAX column and measure:

```DAX
Total_sales = 'Table'[Unit_Price] * 'Table'[Quantity]
Total_Sales_Measure = SUM('Table'[Total_sales])
```

## 📊 Dashboard Overview
The dashboard includes the following visuals:

- 📈 Sales Summary: Total revenue & pizza-wise performance

- 🕒 Sales by Time of Day: Morning, Afternoon, Evening, Night breakdown

- 🍕 Top-Selling Pizzas & Sizes: Pizza type + size preference

- 📅 Monthly Sales Trends: Revenue by month

- 🔻 Declining Trends: Month-end drop & unpopular pizzas

- 🎯 Built using Power BI Desktop with custom DAX measures, filters, and slicers for interactivity.
  

## 🌟 Key Insights
|       Insight    |         Detail                        |
|------------------|---------------------------------------|
| 🍕 Top Pizza | Thai Chicken Pizza (6% of total revenue) |
| 🍕 Top Category | Classic Pizzas dominate |
| 🕒 Peak Time | Afternoon (12 PM – 5 PM) |
| 💰 Best Month | July (10% of total sales) |
| 📉 Drop Period | Last 4 months showed declining revenue |
| ⚖️ Size Preference | Large pizzas = 45% of total sales |


## 💡 Business Recommendations
- 📌 Targeted Promotions: Run afternoon-time discounts to boost orders

- 📌 Inventory Focus: Stock up on top-selling pizzas & large sizes

- 📌 Discount Campaigns: Promote low-performing pizzas to clear inventory

- 📌 Bundle Offers: Introduce combo deals with large pizzas

- 📌 Expansion Strategy: Consider new branches in high-sales regions


## 🔗 Demo & Files
- <a href="https://github.com/Mahirtayeb1/Pizza_Store_Sales_Data_Analysis/tree/main/Screenshoots"> [📊 Power BI Dashboard Screenshot]</a>

- <a href= "https://www.kaggle.com/datasets/nextmillionaire/pizza-sales-dataset"> [📁 Dataset Source: Kaggle]

- <a href= "https://medium.com/@mahirrfaisal07/pizza-sales-analysis-using-power-bi-6bb893920da4"> [📄 Project Report/ Medium Article]</a>

- <a href= "https://github.com/Mahirtayeb1/Pizza_Store_Sales_Data_Analysis/blob/main/Pizza_Sales_Dashboard.pbix"> [📄 Downdload PowerBi DashBoard]</a>


## 🧠 What I Learned
- Cleaning and transforming real-world messy datasets

- Writing DAX expressions and using calculated columns

- Designing interactive and insightful dashboards

- Communicating data findings with clarity


## 💼 This project is part of my effort to break into the data analytics industry. Feedback and collaboration opportunities are welcome!
