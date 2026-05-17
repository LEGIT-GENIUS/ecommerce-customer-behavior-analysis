# 🧮 DAX Calculations & Time Intelligence

This document outlines all DAX measures and calculated columns used in the project. Time intelligence was supported by **Bravo BI**, which auto-generated the Date dimension table.

---

## 📊 Core Measures

### Total Orders
```dax
Total Orders = DISTINCTCOUNT(Sales[Order_ID])
```

### Total Quantity
```dax
Total Quantity = SUM(Sales[Quantity])
```

### Total Gross Revenue
```dax
Total Gross Revenue = SUMX(Sales, Sales[Unit_Price] * Sales[Quantity])
```

### Total Net Revenue
```dax
Total Net Revenue = SUM(Sales[Total_Amount])
```

### Average Order Value (AOV)
```dax
AOV = DIVIDE([Total Net Revenue], [Total Orders])
```

### Total Customers
```dax
Total Customers = DISTINCTCOUNT(Sales[Customer_ID])
```

### Purchase Frequency
```dax
Purchase Frequency = DIVIDE([Total Orders], [Total Customers])
```

---

## 🎁 Discount Measures

### Discounted Transactions
```dax
Discounted Transactions = 
CALCULATE([Total Orders], Sales[Discount_Amount] > 0)
```

### Discount Usage Rate
```dax
Discount Usage Rate = 
DIVIDE([Discounted Transactions], [Total Orders])
```

### Average Discount (All)
```dax
Average Discount (All) = 
AVERAGEX(Sales, DIVIDE(Sales[Discount_Amount], Sales[Unit_Price] * Sales[Quantity]))
```

### Average Discount (Discounted Only)
```dax
Average Discount (Discounted Only) = 
CALCULATE([Average Discount (All)], Sales[Discount_Amount] > 0)
```

---

## ⏱ Time Intelligence Measures (Built with Bravo BI)

### Previous Month Total Orders
```dax
PM Total Orders = 
CALCULATE([Total Orders], DATEADD('Date'[Date], -1, MONTH))
```

### MOM Total Orders
```dax
MOM Total Orders = [Total Orders] - [PM Total Orders]
```

### MoM Growth %
```dax
MOM % Growth = 
DIVIDE([Total Orders] - [PM Total Orders], [PM Total Orders])
```

### PM Total Quantity
```dax
PM Total Quantity = 
CALCULATE([Total Quantity], DATEADD('Date'[Date], -1, MONTH))
```

### MOM Total Quantity
```dax
MOM Total Quantity = [Total Quantity] - [PM Total Quantity]
```

### PM Net Revenue
```dax
PM Total Net Revenue = 
CALCULATE([Total Net Revenue], DATEADD('Date'[Date], -1, MONTH))
```

### MOM Net Revenue
```dax
MOM Total Net Revenue = [Total Net Revenue] - [PM Total Net Revenue]
```

### PM Gross Revenue
```dax
PM Total Gross Revenue = 
CALCULATE([Total Gross Revenue], DATEADD('Date'[Date], -1, MONTH))
```

### MOM Gross Revenue
```dax
MOM Total Gross Revenue = [Total Gross Revenue] - [PM Total Gross Revenue]
```

---

## 🚚 Calculated Columns

### Delivery Group
```dax
Delivery Group = 
SWITCH(
    TRUE(),
    Sales[Delivery_Time_Days] <= 3, "1–3 days",
    Sales[Delivery_Time_Days] <= 7, "4–7 days",
    Sales[Delivery_Time_Days] <= 14, "8–14 days",
    "15–30 days"
)
```

### Discount Range
```dax
Discount Range = 
VAR DiscountPct = DIVIDE(Sales[Discount_Amount], Sales[Unit_Price] * Sales[Quantity])
RETURN
SWITCH(
    TRUE(),
    DiscountPct <= 0.05, "0–5%",
    DiscountPct <= 0.10, "6–10%",
    DiscountPct <= 0.20, "11–20%",
    "21%+"
)
```
