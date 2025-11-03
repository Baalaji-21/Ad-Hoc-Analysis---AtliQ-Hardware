#  Ad-Hoc Analysis - AtliQ Hardware

---

## 🏢 Project Overview

**AtliQ Hardwares** is a global computer hardware manufacturer that sells products through major retail platforms, including  **Amazon**, **Croma**, and **Best Buy** etc.  

Initially, the company managed its operations using Excel. However, as sales expanded, Excel files became large and unmanageable — causing performance issues and disrupting business workflows. To overcome these challenges, AtliQ migrated to a **MySQL database**  and formed a **data analytics team** to generate insights and automate reporting for decision-making.

Currently, the data team receives multiple ad-hoc analysis requests from stakeholders to help them understand **sales trends**, **market performance**, **product demand**, and **forecast accuracy**. This project focuses on building a **centralized SQL-based solution** using Joins, Views and Stored Procedures to deliver **quick, data-driven insights** that empower strategic business decisions.

---

## 🎯 Objectives

The main goals of this project are to:

- 📊 **Perform ad-hoc business analysis** using SQL queries.  
- 🔁 **Automate repetitive analysis tasks** with stored procedures.  
- ⚙️ **Create reusable SQL queries and views** for faster report generation.  
- 🧩 **Support product owners and decision-makers** with accurate, data-driven insights.

---

## 🗄️ Dataset

![Database Schema](Ad-Hoc%20Analysis/Images/dataset.jpg)

---

## 🧾 Ad-Hoc Request 1 — Croma India Product Sales Summary (FY 2021)

**📌 Business Request:**  
As a **Product Owner**, I need a **monthly summary report** showing **sales figures for each product (based on product code)** for the **Croma India** customer during **FY 2021**.  

**🎯 Purpose:**  
To monitor individual product performance and perform further analysis in Excel.

**🧠 Approach:**
- Extract sales data for Croma India (`customer_name = 'Croma'` and `market = 'India'`).
- Filter the data for the fiscal year 2021.
- Group by product code and month.
- Calculate total sales and units sold for each product per month.

**✅ Output:**

🔍 SQL Query Used
🔗 [*View SQL Query*](Ad-Hoc%20Analysis/Queries/query%201)

![Query Output Table](https://raw.githubusercontent.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/main/Ad-Hoc%20Analysis/Images/request1%20-%20result.jpg)

---

## 🧾 Ad-Hoc Request 2 — Gross Monthly Total Sales Report for Croma

**📌 Business Request:**  
As a **Product Owner**, I need an **aggregate monthly gross sales report** for **Croma India** so that I can track how much sales this particular customer is generating for **AtliQ Hardwares** and manage our relationship accordingly.

**🎯 Purpose:**  
To measure the overall monthly revenue contribution of the Croma India customer and evaluate customer performance trends.

**🧠 Approach:**
- Extract sales data where `customer_name = 'Croma'` and `market = 'India'`.
- Aggregate sales at the **monthly level**.
- Calculate the **total gross sales** for each month in the dataset.
- Use the **fact_sales_monthly** and **dim_date** tables for month and year grouping.

**✅ Output:**

🔍 SQL Query Used
🔗 [*View SQL Query*](Ad-Hoc%20Analysis/Queries/query%202)

![Query Output Tablee](https://raw.githubusercontent.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/main/Ad-Hoc%20Analysis/Images/request%202%20-%20result.jpg)


📜 Stored Procedure Query Used
🔗 [*View Stored Procedure Query*](Ad-Hoc%20Analysis/Queries/query%202%20sp)

![Stored Procedure input](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%202%20-%20sp%20window.jpg)

![Stored Procedure Result](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%202%20-%20sp%20result.jpg)

---

## 🧾 Ad-Hoc Request 3 — Market Badge Stored Procedure

**📌 Business Request:**  
As a **Product Owner**, I want to create a **stored procedure** that determines the **market badge** based on the **total sold quantity**.  
If the total sold quantity exceeds **5 million units**, the market is considered **Gold**; otherwise, it is **Silver**.

**🎯 Purpose:**  
To easily classify markets based on their performance and identify top-performing regions for strategic planning.

**🧠 Approach:**
- Aggregate sales data by market to calculate the **total sold quantity**.
- Use a **CASE** statement in the stored procedure to assign:
  - `'Gold'` → if total sold quantity > 5,000,000  
  - `'Silver'` → otherwise
- Return a result set with **market name**, **total quantity sold**, and **assigned badge**.
- Make it reusable by implementing the logic in a stored procedure.

**✅ Output:**

📜 Stored Procedure Query Used
🔗 [*View Market Badge Procedure*](Ad-Hoc%20Analysis/Queries/query%203)

![Stored Procedure input](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%203%20-%20sp%20window.jpg)

![Stored Procedure Result](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%203%20-%20sp%20result.jpg)

---

## 🧾 Ad-Hoc Request 4 — Top Markets, Products, and Customers by Net Sales

**📌 Business Request:**  
As a **Product Owner**, I want a **report** showing the **top markets, products, and customers by net sales** for a given **financial year**.  

**🎯 Purpose:**  
To gain a holistic view of **AtliQ's financial performance** and identify the highest revenue-generating markets, products, and customers for strategic decision-making.

**🧠 Approach:**
- Aggregate sales data by **market**, **product**, and **customer**.  
- Calculate **net sales** using appropriate measures (e.g., `sold_quantity * net_price`).  
- Rank each entity (market, product, customer) based on total net sales.  
- Filter the results for the specified **fiscal year**.  
- Provide the top-performing entries using `ORDER BY` and `LIMIT`.

**✅ Output:**

🔍 SQL Query Used
🔗 [*View Net Sales Query*](Ad-Hoc%20Analysis/Queries/query%204%20ns%20table)

![Query Output Tablee](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%204%20-%20ns%20table.jpg)


📜 Stored Procedure Query Used
🔗[*View Top N Markets Procedure*](Ad-Hoc%20Analysis/Queries/query%204%20market)

![Stored Procedure Result](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%204%20-%20market.jpg)

📜 Stored Procedure Query Used
🔗[*View Top N Products Procedure*](Ad-Hoc%20Analysis/Queries/query%204%20product)

![Stored Procedure Result](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%204%20-%20product.jpg)

📜 Stored Procedure Query Used
🔗[*View Top N Customers Procedure*](Ad-Hoc%20Analysis/Queries/query%204%20customer)

![Stored Procedure Result](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%204%20-%20customer.jpg)

---

## 🧾 Ad-Hoc Request 5 — Net Sales % Share (Global)

**📌 Business Request:**  
As a **Product Owner**, I want to see a **bar chart report** for **FY 2021** showing the **top 10 markets by % Net Sales**.

**🎯 Purpose:**  
To visualize which markets contribute the most to the company’s global net sales and identify high-performing regions for strategic focus.

**🧠 Approach:**
- Calculate **total net sales** for all markets for FY 2021.  
- Compute each market’s **% share of global net sales** using:  
  \[
  \text{Net Sales % Share} = \frac{\text{Market Net Sales}}{\text{Global Net Sales}} \times 100
  \]
- Rank markets by % share and select the **top 10**.  
- Visualize results using a **bar chart** in **Power BI** or **Excel** for better comparison.

**✅ Output:**

🔍 SQL Query Used
🔗 [*View Net Sales % Query*](Ad-Hoc%20Analysis/Queries/query%205)

![Query Output Tablee](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%205%20-%20result.jpg)

![Bar Chart](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%205%20-%20chart.jpg)

---

## 🧾 Ad-Hoc Request 6 — Top N Products by Quantity Sold (Per Division)

**📌 Business Request:**  
As a **Product Owner**, I want to get the **Top N products** in each **division** based on their **quantity sold** for a given **financial year**.

**🎯 Purpose:**  
To analyze which products are performing best within each division and identify high-demand products for better production and marketing planning.

**🧠 Approach:**
- Aggregate total **quantity sold** for each product within every division.  
- Use **window functions** such as `RANK()` or `DENSE_RANK()` to rank products by quantity sold within each division.  
- Filter to show only the **Top N** products per division.  
- Allow flexibility to specify both **financial year** and **N value** as input parameters (e.g., in a stored procedure).

**✅ Output:**

📜 Stored Procedure Query Used
🔗 [*View Top N Products By Division Procedure*](Ad-Hoc%20Analysis/Queries/query%206)

![Stored Procedure input](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%206%20-%20%20st%20window.jpg)

![Stored Procedure Result](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%206%20-%20result.jpg)

---

## 🧾 Ad-Hoc Request 7 — Forecast Accuracy for All Customers

**📌 Business Request:**  
As a **Product Owner**, I need an **aggregate forecast accuracy report** for **all customers** for a given **fiscal year**, so that I can track how accurate our forecasts are compared to actual sales.

**🎯 Purpose:**  
To evaluate the reliability of sales forecasts, identify gaps between forecasted and actual sales, and improve future forecasting methods.

**🧠 Approach:**
- Extract **forecast** and **actual sales** data for all customers in the given fiscal year.  
- Calculate:
  - **Total Sold Quantity**  
  - **Total Forecast Quantity**  
  - **Net Error** = `Forecast Quantity - Sold Quantity`  
  - **Absolute Error** = `ABS(Forecast Quantity - Sold Quantity)`  
  - **Forecast Accuracy %** = `100 - (Absolute Error / Forecast Quantity * 100)`  
- Group the results by **Customer Code**, **Customer Name**, and **Market**.  
- Rank or filter results to identify customers with the highest or lowest forecast accuracy.

**✅ Output:**

🔍 SQL Query Used
🔗 [*View Sales and Forecast Query*](Ad-Hoc%20Analysis/Queries/query%207%20est_table)

![Query Output Tablee](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%207%20-%20est%20table.jpg)


📜 Stored Procedure Query Used
🔗[*View Forecast Accuracy Procedure*](Ad-Hoc%20Analysis/Queries/query%207%20sp)

![Stored Procedure input](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%207%20-%20%20st%20window.jpg)

![Stored Procedure Result](https://github.com/Baalaji-21/Ad-Hoc-Analysis---AtliQ-Hardware/blob/main/Ad-Hoc%20Analysis/Images/request%207%20-%20result.jpg)

---

## 🏁 Conclusion

This SQL project provided hands-on experience in tackling **real-world ad-hoc business problems** and converting them into **actionable insights**.  

Each analysis addressed a unique business scenario — from evaluating sales and product performance to measuring forecast accuracy and market share — using powerful SQL techniques like **CTEs, joins, stored procedures, and aggregations**.

---

## 💡 Key Takeaways

Through this project, I have:

- 🧩 Learned to design **structured, reusable SQL queries** for analytical purposes  
- 🔗 Gained confidence in applying **joins, subqueries, and stored procedures** to solve complex data challenges  
- 📊 Strengthened my ability to **translate business requirements into data insights**  

---






