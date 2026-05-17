# 🔬 Project Methodology

This document explains the **step-by-step approach** taken to deliver the analysis.

---

## 1. Data Acquisition
- Downloaded the E-Commerce Customer Behavior dataset from **Kaggle**
- File format: CSV (UTF-8), ~500 KB
- Validated record count: 5,000 rows × 18 columns

---

## 2. Data Cleaning (Microsoft Excel)
- Inspected for missing values, blanks, and duplicates (none found)
- Standardized date format to YYYY-MM-DD
- Verified data types per column
- Validated logical relationships (e.g., Total_Amount math)
- Standardized text fields (City, Gender, Payment_Method, Device_Type)
- Created Discount Range and Delivery Group categorical buckets

---

## 3. Data Loading (Power BI)
- Imported cleaned Excel file into Power BI Desktop
- Confirmed data types per column in Power Query

---

## 4. Data Modeling
- Adopted a **Star Schema** with:
  - One central **Fact Table** (transactions)
  - One **Date Dimension Table** auto-generated using **Bravo BI**
- Established relationship: `Sales[Date]` → `Date[Date]`

---

## 5. DAX Measure Creation
- Built core KPIs (Total Orders, Total Net Revenue, AOV, etc.)
- Built discount analysis measures
- Built time intelligence measures (MoM comparisons) using Bravo BI

---

## 6. Dashboard Design
- Designed a 3-page dashboard with consistent green theme
- Page 1: Customer Behavior & Payment Analysis
- Page 2: Product & Discount Performance
- Page 3: Executive Sales & Time Intelligence Overview
- Added interactive slicers for Year, Month, City, Device, Payment Method, etc.

---

## 7. Insight Generation
- Reviewed each dashboard page to extract business insights
- Documented findings and recommendations

---

## 8. Documentation & Delivery
- Wrote complete README and supporting docs
- Organized GitHub repository structure
- Uploaded screenshots, .pbix file, and cleaned dataset
