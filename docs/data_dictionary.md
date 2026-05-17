# 📚 Data Dictionary

**Dataset:** E-Commerce Customer Behavior and Sales Dataset  
**Source:** Kaggle (Turkish Online Retail Platform)  
**Total Records:** 5,000 transactions  
**Total Columns:** 18

---

## Column Details

| # | Column Name | Data Type | Description | Example |
|---|-------------|-----------|-------------|---------|
| 1 | Order_ID | String | Unique identifier for each order | ORD_001337 |
| 2 | Customer_ID | String | Unique customer identifier | CUST_01337 |
| 3 | Date | DateTime | Transaction date | 2023-06-15 |
| 4 | Age | Integer | Customer age (18–75) | 35 |
| 5 | Gender | String | Customer gender (Male, Female, Other) | Female |
| 6 | City | String | Customer city (10 major Turkish cities) | Istanbul |
| 7 | Product_Category | String | One of 8 product categories | Electronics |
| 8 | Unit_Price | Float | Price per unit in TRY | 1299.99 |
| 9 | Quantity | Integer | Units purchased (1–5) | 2 |
| 10 | Discount_Amount | Float | Discount applied (if any) | 129.99 |
| 11 | Total_Amount | Float | Final amount after discount | 2469.99 |
| 12 | Payment_Method | String | One of 5 payment types | Credit Card |
| 13 | Device_Type | String | Mobile, Desktop, or Tablet | Mobile |
| 14 | Session_Duration_Minutes | Integer | Session length (1–120) | 15 |
| 15 | Pages_Viewed | Integer | Pages viewed in session (1–50) | 8 |
| 16 | Is_Returning_Customer | Boolean | Returning customer flag | True |
| 17 | Delivery_Time_Days | Integer | Delivery duration (1–30 days) | 3 |
| 18 | Customer_Rating | Integer | Satisfaction rating (1–5) | 5 |

---

## Categorical Values

### Cities (10)
Istanbul, Ankara, Izmir, Bursa, Adana, Antalya, Gaziantep, Konya, Kayseri, Eskisehir

### Product Categories (8)
Electronics, Fashion, Home & Garden, Sports, Books, Beauty, Toys, Food

### Payment Methods (5)
Credit Card, Debit Card, Digital Wallet, Bank Transfer, Cash on Delivery

### Device Types (3)
Mobile, Desktop, Tablet

### Gender (3)
Male, Female, Other

---

## Derived / Calculated Columns

| Column | Logic | Description |
|--------|-------|-------------|
| **Discount Range** | SWITCH on Discount % | Buckets: 0–5%, 6–10%, 11–20%, 21%+ |
| **Delivery Group** | SWITCH on Delivery_Time_Days | Buckets: 1–3 days, 4–7 days, 8–14 days, 15–30 days |
