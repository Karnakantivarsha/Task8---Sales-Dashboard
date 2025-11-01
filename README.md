# 🧭 TASK 8 – Simple Sales Dashboard (Data Analytics Internship Project)

This project demonstrates how to clean, prepare, and visualize sales data using Python and Power BI. The goal is to design an interactive sales dashboard that helps analyze sales performance by month, region, and category for better decision-making.

---

## 🧰 Tools & Technologies
Power BI Desktop | Python (Pandas, NumPy) | CSV Dataset (Superstore_Sales.csv)

---

## 🧹 Data Cleaning using Python (Google Colab / Jupyter)
```python
import pandas as pd

# Load dataset
df = pd.read_csv('Superstore_Sales.csv', parse_dates=['Order Date'])

# Drop rows with missing essential fields
df = df.dropna(subset=['Order Date', 'Sales', 'Region'])

# Convert data types
df['Order Date'] = pd.to_datetime(df['Order Date'], errors='coerce')
df['Sales'] = pd.to_numeric(df['Sales'], errors='coerce')
df['Profit'] = pd.to_numeric(df['Profit'], errors='coerce')

# Create Month-Year column for trend analysis
df['MonthYear'] = df['Order Date'].dt.to_period('M').dt.to_timestamp()

# Fill missing numeric values and remove duplicates
df[['Sales','Profit']] = df[['Sales','Profit']].fillna(0)
df = df.drop_duplicates()

# Save the cleaned dataset
df.to_csv('Superstore_Sales_prepared.csv', index=False)
print("✅ Cleaned file saved as 'Superstore_Sales_prepared.csv'")

Power BI Dashboard Design Process

Import Data

Open Power BI → Home → Get Data → Text/CSV → select Superstore_Sales_prepared.csv

Create Visuals

Line Chart: Sales over MonthYear

Bar Chart: Sales by Region

Donut Chart: Sales by Category

Slicer: Region / Category filter

Card Visuals: Total Sales and Total Profit (KPI cards)

Create DAX Measures

Total Sales = SUM('Superstore'[Sales])
Total Profit = SUM('Superstore'[Profit])
MonthYear = FORMAT('Superstore'[Order Date], "MMM yyyy")


Layout & Formatting

Place KPI cards at top, line chart in center, bar and donut at bottom

Add slicers on right or left side for interactivity

Use consistent color theme and add clear chart titles

Example titles: “Monthly Sales Trend”, “Sales by Region”, “Sales by Category”

Add Interactivity

Use Slicer visual → drag Region or Category → users can click to filter entire dashboard

For multiple filters, add two slicers (Region + Category)

Export Dashboard

Go to File → Export → Export to PDF

Save as dashboard_export.pdf

*Project Summary

This project covers the complete data analytics workflow — from data cleaning using Python to dashboard creation in Power BI. The resulting dashboard provides clear visibility into monthly sales performance, top-performing regions, and profit insights, enabling quick and data-driven business decisions.

*Conclusion

This project successfully demonstrates the end-to-end data analysis process — from cleaning and preparing raw sales data using Python to designing an interactive Power BI dashboard that provides meaningful business insights.
The dashboard allows users to easily monitor monthly sales trends, regional performance, and category-wise revenue distribution through intuitive visuals and slicers.

By transforming data into a visual story, this task highlights the importance of data-driven decision-making and the practical use of analytical tools to improve business understanding and performance tracking.
