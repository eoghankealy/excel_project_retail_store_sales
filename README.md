# 🧹 Retail Store Sales Data Cleaning & Excel Dashboard

## 📘 Overview
This project focuses on cleaning and analyzing a messy retail sales dataset from Kaggle, transforming it into a structured, validated, and interactive Excel dashboard.  
The aim was to practice real-world data cleaning, explore sales performance by product category, and develop a clear, data-driven visualization of retail trends.

**Dataset:** [Retail Store Sales (Dirty for Data Cleaning)](https://www.kaggle.com/datasets/ahmedmohamed2003/retail-store-sales-dirty-for-data-cleaning)  
**Tool Used:** Microsoft Excel (Mac)  
**Total Records:** 12,575  
**Removed Records:** 604 (≈4.8%)

---

## 🧾 Dataset Description
The dataset contains retail transaction data including:
- Transaction ID
- Customer ID
- Category  
- Item  
- Price per Unit  
- Quantity  
- Total Spent  
- Payment Method 
- Location 
- Transaction Date
- Discount Applied 

---

## 🧼 Data Cleaning Summary

| Column | Missing Values | Action Taken |
|---------|----------------|---------------|
| Quantity | 604 | Rows removed (same rows with blanks as Total Spent) |
| Total Spent | 604 | Removed same rows as Quantity |
| Price per Unit | 609 | Filled using Total Spent ÷ Quantity |
| Item | 1,213 | Inferred using Category & Price |
| Discount Applied | 4,199 | Left blank as unclear meaning |

---

## 🧮 Cleaning Highlights

- Converted dates to `YYYY-MM-DD`  
- Set proper data types and formatting  
- Checked for duplicates  
- Filled “Price per Unit” blanks using:

```excel
=[Total Spent]/[Quantity]
```


- When filtering for Category and Price all non blank Item cells have the same Item name, therefore it can be assumed the blanks should have that same name
- Used XLOOKUP to fill missing Item names:

```
=IF(D2<>"", D2, XLOOKUP(1,(C:C=C2)*(E:E=E2)*(D:D<>""),D:D))
```

- Removed 604 rows with both Quantity and Total Spent missing as amounted to less than 5% of Dataset
 



## 📊 Dashboard Insights
![Dashboard Preview](Dashboard/dashboard_screenshot.png)

- Butchers: Highest earning category but trending down. Qrt 1 2022 €20,999.50  Qrt 1 2024 €16,346.00. Yearly revenue down from €79,395.50 in 2022 to €66,067.50 in 2024, a drop of 16.78 %

- Beverages: Growing steadily  Qrt 1 2022 €16,734 Qrt 1 2024 €17,543. Yearly revenue up from €63,555 in 2022 to €74,205.50  an increase of 16.76%

- In general the revenue is relatively equally  spread throughout the Categories,  Items and time periods. The  highest revenue category is  Butchers with €208,118,00 while the lowest revenue category Milk Products has €180,112, a  percetage difference  of 13.5%

- Sales are also equally spread throughout the different payment options and whether the sales are online or instore. 

## 💡 Key Takeaways

- Logical inference and Excel formulas can repair many missing values.

