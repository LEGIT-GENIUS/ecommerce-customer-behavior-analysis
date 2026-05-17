<img width="286" height="176" alt="download" src="https://github.com/user-attachments/assets/ab1ca8d7-8a0a-4cbc-9b88-cba44ff9bd04" />

## 📑 Table of Contents
1. [Project Overview](#-project-overview)
2. [Problem Statement](#-problem-statement)
3. [Tools & Technologies Used](#-tools--technologies-used)
4. [Dataset Description](#-dataset-description)
5. [Data Cleaning & Preparation](#-data-cleaning--preparation)
6. [Data Modeling](#-data-modeling)
7. [DAX Calculations & Time Intelligence](#-dax-calculations--time-intelligence)
8. [Dashboard Overview](#-dashboard-overview)
9. [Key Insights](#-key-insights)
10. [Recommendations](#-recommendations)
11. [Challenges Encountered](#-challenges-encountered)
12. [Future Improvements](#-future-improvements)
13. [Repository Structure](#-repository-structure)
14. [Author Information](#-author-information)


# 📌 Project Overview

This project delivers a comprehensive end-to-end **business intelligence analysis** of **5,000 e-commerce transactions** from a Turkish online retail platform spanning **January 2023 to March 2024 (15 months)**.

The analysis explores **customer demographics, purchasing behavior, product category performance, discount effectiveness, delivery performance, payment preferences, and revenue trends** across **10 major Turkish cities**.

Through a fully interactive **3-page Power BI dashboard**, raw transactional data is transformed into **clear, actionable business intelligence** — empowering stakeholders to make data-driven decisions on marketing, logistics, product strategy, and customer engagement.

> **Industry/Domain:** Retail & E-Commerce  
> **Currency:** Turkish Lira (TRY) | Displayed in USD ($) within the dashboard

--

## 🎯 Problem Statement

The platform required a data-driven view of business performance to answer the following critical questions:

1. **Which product categories generate the most revenue and profit?**
2. **How do customers behave across different devices (Mobile, Desktop, Tablet)?**
3. **Which cities are top-performing markets and which are underperforming?**
4. **What is the impact of discounts on sales, and how is discount usage distributed?**
5. **How does delivery performance affect customer satisfaction?**
6. **What are the month-over-month revenue and order trends?**
7. **Which payment methods are most preferred and by which customer segments?**
8. **What is the gender-based purchasing pattern and returning-customer rate?**

--

## 🛠 Tools & Technologies Used

| Tool | Purpose |
|------|---------|
| **Microsoft Excel** | Data cleaning, standardization, and preliminary inspection |
| **Power BI Desktop** | Data modeling, visualization, and dashboard creation |
| **Bravo BI (by SQLBI)** | Date dimension generation, time intelligence calculations, and DAX optimization |
| **DAX (Data Analysis Expressions)** | Custom measures, calculated columns, and KPIs |

---

## 📂 Dataset Description

| Attribute | Details |
|-----------|---------|
| **Dataset Name** | E-Commerce Customer Behavior and Sales Dataset |
| **Source** | Kaggle (Public Domain – CC0 License) |
| **Origin** | Turkish Online Retail Platform |
| **Records** | 5,000 transactions |
| **Columns** | 18 features |
| **Time Period** | January 2023 – March 2024 (15 months) |
| **File Format** | CSV (UTF-8 encoded) |
| **File Size** | ~500 KB |

### Key Field Groups:

| Category | Fields |
|----------|--------|
| **Order Info** | Order_ID, Date |
| **Customer Demographics** | Customer_ID, Age, Gender, City |
| **Product Info** | Product_Category, Unit_Price, Quantity |
| **Transaction Details** | Discount_Amount, Total_Amount, Payment_Method |
| **Behavior Metrics** | Device_Type, Session_Duration_Minutes, Pages_Viewed, Is_Returning_Customer |
| **Post-Purchase** | Delivery_Time_Days, Customer_Rating |

📄 Full column descriptions available in (https://github.com/LEGIT-GENIUS/ecommerce-customer-behavior-analysis/blob/main/docs/data_dictionary.md)

---

## 🧹 Data Cleaning & Preparation

All cleaning was performed in **Microsoft Excel** before importing the data into Power BI.

### Steps Performed:
1. ✅ **Inspected the dataset** for missing values, duplicates, and inconsistencies
2. ✅ **Standardized date formats** (YYYY-MM-DD) to support time intelligence
3. ✅ **Verified data types** for every column (numerical, categorical, boolean)
4. ✅ **Checked outliers** in Unit_Price, Quantity, and Total_Amount
5. ✅ **Validated logical consistency** (e.g., Total_Amount = (Unit_Price × Quantity) − Discount_Amount)
6. ✅ **Standardized text categories** (Gender, City, Payment_Method, Device_Type)
7. ✅ **Created Discount Range buckets** (0–5%, 6–10%, 11–20%, 21%+) for segmentation
8. ✅ **Created Delivery Group buckets** (1–3 days, 4–7 days, 8–14 days, 15–30 days)

📄 Full methodology in (https://github.com/LEGIT-GENIUS/ecommerce-customer-behavior-analysis/blob/main/docs/docs/methodology.md)

---

## 🔗 Data Modeling

A **Star Schema** approach was adopted:
- A central **Fact Table** (transactions)
- A supporting **Date Dimension Table** (auto-generated via Bravo BI)

The Date dimension enabled robust time intelligence functions such as **MTD, YTD, MoM, and YoY** comparisons.

---

## 🧮 DAX Calculations & Time Intelligence

Key DAX measures were built using **Bravo BI** and native Power BI DAX.

### Core Measures
- **Total Orders** = `DISTINCTCOUNT(Order_ID)`
- **Total Quantity** = `SUM(Quantity)`
- **Total Gross Revenue** = `SUMX(Sales, Unit_Price * Quantity)`
- **Total Net Revenue** = `SUM(Total_Amount)`
- **Average Order Value (AOV)** = `[Total Net Revenue] / [Total Orders]`
- **Purchase Frequency** = `[Total Orders] / [Total Customers]`
- **Discount Usage Rate** = `[Discounted Transactions] / [Total Transactions]`

### Time Intelligence Measures (Bravo BI)
- **MOM Total Orders** (Month over Month)
- **PM Total Orders** (Previous Month)
- **MOM Total Quantity**
- **MOM Net Revenue**
- **MOM Gross Revenue**
- **% Growth vs Previous Month**

📄 Full DAX documentation in (https://github.com/LEGIT-GENIUS/ecommerce-customer-behavior-analysis/blob/main/docs/dax_calculations.md)

---

# 📊 Dashboard Overview

The Power BI report contains **3 interactive pages**:

---

### 📄 Page 1 – Customer Behavior & Payment Analysis
Explores customer demographics, payment preferences, device usage patterns, gender distribution, and city-level discount behavior.

**Key Visuals:**
- KPI Cards: Purchase Frequency, Avg Pages Viewed, Avg Session Duration, Total Customers
- Total Orders by Payment Method & Gender (Bar)
- Gross Revenue by Product Category (Bar)
- Unique Customers by Device Type & Gender (Clustered Column)
- Average Discount by City (Line trend)
- Unique Customers by Gender (Pie)
- Payment Method × Device Type (Matrix)
- Discount Distribution table

🖼 ![Page 1](![<img width="1459" height="754" alt="CONSUMER-BEHAVIOUR-AND-ENGAGEMENT-ANALYSIS" src="https://github.com/user-attachments/assets/3232118a-c526-49e8-8df2-10a03f1d2c9e" />
)

---

### 📄 Page 2 – Product & Discount Performance
A deep dive into product category performance, discount impact, delivery group analysis, and the relationship between delivery time, revenue, and customer satisfaction.

**Key Visuals:**
- KPI Cards: Product Categories, Discount Usage Rate, Discounted Transactions, Avg Discounts
- Delivery Group matrix across categories
- Total Quantity vs Total Orders by Category (Area)
- Net Revenue & Gross Revenue by Category (Bar)
- Avg Delivery Time vs Customer Rating (Bubble)
- Net Revenue vs Customer Rating (Bubble)
- Discount Analysis table

🖼 ![Page 2](<img width="1471" height="746" alt="PRODUCT-PERFORMANCE" src="https://github.com/user-attachments/assets/c5574e0a-79c3-4796-aa3d-3e686b1bfa6c" />)

---

###
 📄 Page 3 – Executive Sales Performance & Time Intelligence
An executive-level overview featuring high-level KPIs, MoM time intelligence comparisons, geographic performance, and operational metrics.

**Key Visuals:**
- KPI Cards: Total Quantity, Total Orders, AOV, Total Gross Revenue, Total Net Revenue
- MOM KPIs vs Previous Month
- Total Quantity & Net Revenue by City
- Net Revenue trend by Month
- Payment Method & Device Type performance tables
- Delivery Group interpretation table
- Avg Customer Rating Gauge (3.90/5)
- Avg Delivery Time Gauge (6.50 days)

🖼 ![Page 3](<img width="1463" height="756" alt="EXECUTIVE_SUMMARY" src="https://github.com/user-attachments/assets/9ff7f208-5ad7-404c-938d-177f9dd76a85" />
)

---

#💡 Key Insights

### 🏆 Revenue & Product Performance
- **Electronics dominates** with **$11.1M in gross revenue** — about **2.5× the second-best category** (Home & Garden at $4.3M)
- **Books and Food** are the lowest-performing categories ($0.4M each)
- Business totals: **$23M Gross Revenue**, **$22M Net Revenue**, and **17K total orders**

### 🌆 Geographic Insights
- **Istanbul leads** all cities with **13,329 units sold** and **$5.6M net revenue**
- **Eskisehir** is the lowest-performing city ($0.9M net revenue)
- Top 3 cities (Istanbul, Ankara, Izmir) generate over **50% of total revenue**

### 📱 Device & Customer Behavior
- **Mobile dominates**, driving **55.97% of orders** and **$12M net revenue**
- **Desktop** generates strong revenue ($7.6M) with higher AOV per session
- **Tablet usage is minimal** (~9.74%)

### 💳 Payment Methods
- **Credit Card** is the top payment method (40.33% quantity / 41.64% net revenue)
- **Debit Card** follows at 24.90%
- **Cash on Delivery** is the least used (5.18%)

### 👥 Customer Demographics
- Near-equal gender split: **49.84% Female, 48.7% Male, 1.46% Other**
- **60% returning customers** — strong loyalty indicator

### 🎁 Discount Analysis
- **38% of transactions** received a discount
- Average discount (when applied): **41%**
- Discount distribution: **0–5% range = 62%**, **21%+ range = 28%**, **11–20% = 7%**, **6–10% = 2%**

### 🚚 Delivery Performance
- **Average delivery time:** 6.50 days
- **48.22% standard delivery (4–7 days)**
- **29.45% slow delivery (8–14 days)** — improvement opportunity
- Only **19.54% highly efficient delivery (1–3 days)**
- **2.79% logistics inefficiency (15–30 days)**

### ⭐ Customer Satisfaction
- **Average rating: 3.90 / 5** — solid but with room to grow
- Delivery time clearly influences rating distribution

### 📈 Sales Trends
- **December 2023 peaked at $1.59M** — strong holiday season effect
- **March 2024 dropped to $1.27M** — lowest in recent months
- **Consistent MoM growth observed: ~6.91% – 6.93%** across key metrics

---

## ✅ Recommendations

1. **Double down on Electronics** with bundled promotions and exclusive launches — it is the clear revenue driver
2. **Investigate underperformance in Books & Food** — reassess pricing, marketing, and product range
3. **Adopt a mobile-first strategy** — optimize mobile UX, checkout, and app experience
4. **Reduce slow deliveries** — bring the 29.45% slow-delivery segment down to improve ratings and retention
5. **Expand marketing in Istanbul, Ankara, and Izmir** while building growth campaigns in Eskisehir, Kayseri, and Konya
6. **Promote Credit & Debit card usage** with cashback offers; reduce Cash-on-Delivery friction
7. **Leverage the 60% returning customer base** with loyalty programs and personalized recommendations
8. **Plan inventory and marketing around Q4 (Oct–Dec)** based on observed seasonality
9. **Review discount strategy** — heavy discounts (21%+) account for 28% of usage; ensure they are driving profit, not eroding margin

---

## ⚠️ Challenges Encountered

- Building accurate **Month-over-Month (MoM)** comparisons required a properly structured Date dimension table — solved using **Bravo BI**
- Designing a **clean visual hierarchy** across 3 pages with consistent green-themed branding
- Balancing **information density vs readability** in KPI- and matrix-heavy layouts
- Ensuring DAX measures performed efficiently across all 3 dashboard pages with multiple slicer interactions

---

## 🚀 Future Improvements

- Integrate **SQL Server / PostgreSQL** as the data source for live refresh
- Add **Customer Lifetime Value (CLV)** and **Churn Prediction** measures
- Build a **Customer Segmentation page** using RFM (Recency, Frequency, Monetary) analysis
- Deploy the dashboard to **Power BI Service** with scheduled refresh
- Add **drill-through pages** for deep dives by customer or product
- Implement **Row-Level Security (RLS)** for multi-user enterprise environments


## 📁 Repository Structure

```
ecommerce-customer-behavior-analysis/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── data/
│   ├── raw/
│   │   └── ecommerce_raw.csv
│   └── cleaned/
│       └── ecommerce_cleaned.xlsx
│
├── dashboards/
│   ├── powerbi/
│   │   └── ecommerce_dashboard.pbix
│   └── screenshots/
│       ├── page1_customer_behavior.png
│       ├── page2_product_discount.png
│       └── page3_executive_overview.png
│
├── docs/
│   ├── data_dictionary.md
│   ├── methodology.md
│   ├── dax_calculations.md
│   └── business_insights.md
│
├── images/
│   └── banner.png
│
└── reports/
    └── final_report.pdf
```

---

## 👤 Author Information

**GODWIN AJOMA**

- 💼 LinkedIn: [https://www.linkedin.com/in/ajoma-godwin-b3086824b/?skipRedirect=true]
- 📧 Email: [Ajoma14@gmail.com]
- 🐙 GitHub: [@yourusername](https://github.com/yourusername)

---

## 📜 License
This project is licensed under the **MIT License** — see the [LICENSE](https://www.mit.edu/~amini/LICENSE.md) file for details.  
Dataset is under **CC0: Public Domain** license from Kaggle.

---

## 🙏 Acknowledgments
- Dataset provided by the Kaggle community
- **Bravo BI** by SQLBI for DAX optimization and Date table generation
- Power BI Community for visualization inspiration

---

⭐ **If you find this project useful, please consider giving it a star!** ⭐
