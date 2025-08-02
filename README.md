# AtLiq Hardware Sales Insight Dashboard

This project delivers a real-time sales insight dashboard built using Power BI for *AtLiq Hardware*, a computer hardware company navigating a dynamic and fast-changing market. The dashboard provides actionable sales analytics to assist the sales leadership and management team in making data-driven decisions.


## Project Overview

AtLiq Hardware faced challenges in adapting to dynamic market conditions affecting sales performance. To address this, a data-driven solution was developed to capture, analyze, and visualize sales data effectively. 
 
The Power BI dashboard offers real-time insights on sales trends, product performance, and customer purchasing behavior to empower leadership with timely and actionable intelligence.

KPI's:
1} Total quantity sold
2} Revenue by Markets
3}Sales quantity by markets
4} Track revenue by Year
5} Revenue by Month
6}Top 5 customers by Revenue
7} Which 5 products are most successful in the market
8} Revenue trend

**Data Analysis Using SQL**
1)Show all customer records

SELECT * FROM customers;

2)Show total number of customers

SELECT count(*) FROM customers;

3)Show transactions for Chennai market (market code for chennai is Mark001

SELECT * FROM transactions where market_code='Mark001';

4)Show distrinct product codes that were sold in chennai

SELECT distinct product_code FROM transactions where market_code='Mark001';

5)Show transactions where currency is US dollars

SELECT * from transactions where currency="USD"

6)Show transactions in 2020 join by date table

SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;

7)Show total revenue in year 2020,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";

8)Show total revenue in year 2020, January Month,

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");

9)Show total revenue in year 2020 in Chennai

SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.market_code="Mark001";

**Data Analysis Using Power BI**
Formula to create norm_amount column
= Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)
