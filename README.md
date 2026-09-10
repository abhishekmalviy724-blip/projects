# E-commerce Sales Data Analysis project

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

a = pd.read_csv("ecommerce_sales.csv")

print("FIRST 5 ROWS")
print(a.head())

print("\nSHAPE")
print(a.shape)

print("\nCOLUMNS")
print(a.columns)

print("\nINFO")
print(a.info())

print("\nSTATISTICS")
print(a.describe())

print("\nMISSING VALUES")
print(a.isnull().sum())

print("\nDUPLICATES")
print(a.duplicated().sum())

a = a.drop_duplicates()

a["Order_Date"] = pd.to_datetime(a["Order_Date"], errors="coerce")

a["Sales"] = pd.to_numeric(a["Sales"], errors="coerce")
a["Profit"] = pd.to_numeric(a["Profit"], errors="coerce")
a["Quantity"] = pd.to_numeric(a["Quantity"], errors="coerce")
a["Unit_Price"] = pd.to_numeric(a["Unit_Price"], errors="coerce")
a["Discount"] = pd.to_numeric(a["Discount"], errors="coerce")

a["Sales"] = a["Sales"].fillna(a["Sales"].median())
a["Profit"] = a["Profit"].fillna(a["Profit"].median())
a["Quantity"] = a["Quantity"].fillna(a["Quantity"].median())

a = a.dropna(subset=["Order_ID", "Order_Date", "Category", "Product"])

a["Month"] = a["Order_Date"].dt.month
a["Month_Name"] = a["Order_Date"].dt.strftime("%B")
a["Year"] = a["Order_Date"].dt.year

a["Profit_Margin"] = (a["Profit"] / a["Sales"]) * 100
a["Revenue_per_Unit"] = a["Sales"] / a["Quantity"]

total_sales = a["Sales"].sum()
total_profit = a["Profit"].sum()
total_orders = a["Order_ID"].nunique()
total_quantity = a["Quantity"].sum()

average_order_value = total_sales / total_orders
profit_margin = (total_profit / total_sales) * 100

print("\nTOTAL SALES:", total_sales)
print("TOTAL PROFIT:", total_profit)
print("TOTAL ORDERS:", total_orders)
print("TOTAL QUANTITY:", total_quantity)
print("AVERAGE ORDER VALUE:", average_order_value)
print("PROFIT MARGIN:", profit_margin)

category_sales = (
    a.groupby("Category")["Sales"]
    .sum()
    .sort_values(ascending=False)
)

category_profit = (
    a.groupby("Category")["Profit"]
    .sum()
    .sort_values(ascending=False)
)

category_quantity = (
    a.groupby("Category")["Quantity"]
    .sum()
    .sort_values(ascending=False)
)

print("\nSALES BY CATEGORY")
print(category_sales)

print("\nPROFIT BY CATEGORY")
print(category_profit)

print("\nQUANTITY BY CATEGORY")
print(category_quantity)

top_products = (
    a.groupby("Product")["Sales"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

top_profit_products = (
    a.groupby("Product")["Profit"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

most_sold = (
    a.groupby("Product")["Quantity"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

print("\nTOP 10 PRODUCTS BY SALES")
print(top_products)

print("\nTOP 10 PRODUCTS BY PROFIT")
print(top_profit_products)

print("\nTOP 10 MOST SOLD PRODUCTS")
print(most_sold)

state_sales = (
    a.groupby("State")["Sales"]
    .sum()
    .sort_values(ascending=False)
)

city_sales = (
    a.groupby("City")["Sales"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

print("\nSTATE-WISE SALES")
print(state_sales)

print("\nTOP 10 CITIES")
print(city_sales)

top_customers = (
    a.groupby("Customer_ID")["Sales"]
    .sum()
    .sort_values(ascending=False)
    .head(10)
)

customer_orders = (
    a.groupby("Customer_ID")["Order_ID"]
    .nunique()
    .sort_values(ascending=False)
    .head(10)
)

print("\nTOP CUSTOMERS")
print(top_customers)

print("\nCUSTOMERS BY NUMBER OF ORDERS")
print(customer_orders)

monthly_sales = (
    a.groupby(a["Order_Date"].dt.to_period("M"))["Sales"]
    .sum()
)

monthly_profit = (
    a.groupby(a["Order_Date"].dt.to_period("M"))["Profit"]
    .sum()
)

print("\nMONTHLY SALES")
print(monthly_sales)

print("\nMONTHLY PROFIT")
print(monthly_profit)

payment_sales = (
    a.groupby("Payment_Mode")["Sales"]
    .sum()
    .sort_values(ascending=False)
)

print("\nPAYMENT MODE SALES")
print(payment_sales)

plt.figure(figsize=(8,5))
sns.barplot(x=category_sales.index, y=category_sales.values)
plt.title("Sales by Category")
plt.xlabel("Category")
plt.ylabel("Sales")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

plt.figure(figsize=(8,5))
sns.barplot(x=category_profit.index, y=category_profit.values)
plt.title("Profit by Category")
plt.xlabel("Category")
plt.ylabel("Profit")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

plt.figure(figsize=(10,5))
plt.plot(monthly_sales.index.astype(str), monthly_sales.values, marker="o")
plt.title("Monthly Sales Trend")
plt.xlabel("Month")
plt.ylabel("Sales")
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

plt.figure(figsize=(10,6))
sns.barplot(x=top_products.values, y=top_products.index)
plt.title("Top 10 Products by Sales")
plt.xlabel("Sales")
plt.ylabel("Product")
plt.tight_layout()
plt.show()

plt.figure(figsize=(7,7))
plt.pie(
    payment_sales.values,
    labels=payment_sales.index,
    autopct="%1.1f%%"
)
plt.title("Sales by Payment Mode")
plt.show()

plt.figure(figsize=(8,5))
sns.scatterplot(
    data=a,
    x="Discount",
    y="Profit"
)
plt.title("Discount vs Profit")
plt.xlabel("Discount")
plt.ylabel("Profit")
plt.show()

plt.figure(figsize=(8,5))
sns.scatterplot(
    data=a,
    x="Sales",
    y="Profit"
)
plt.title("Sales vs Profit")
plt.xlabel("Sales")
plt.ylabel("Profit")
plt.show()

numeric_columns = [
    "Quantity",
    "Unit_Price",
    "Discount",
    "Sales",
    "Profit",
    "Profit_Margin"
]

correlation = a[numeric_columns].corr()

print("\nCORRELATION")
print(correlation)

plt.figure(figsize=(9,6))
sns.heatmap(
    correlation,
    annot=True,
    cmap="coolwarm"
)
plt.title("Correlation Heatmap")
plt.tight_layout()
plt.show()

best_category = category_sales.idxmax()
best_profit_category = category_profit.idxmax()
best_product = top_products.idxmax()
best_state = state_sales.idxmax()
best_payment = payment_sales.idxmax()

print("\nBUSINESS INSIGHTS")
print("Best Selling Category:", best_category)
print("Most Profitable Category:", best_profit_category)
print("Best Selling Product:", best_product)
print("Top State:", best_state)
print("Most Used Payment Mode:", best_payment)
