📊 Task 7 – Basic Sales Summary using SQLite and Python
📌 Project Title

Basic Sales Summary from a Tiny SQLite Database using Python

🎯 Objective

The objective of this project is to:

Create a small SQLite database

Insert sample sales data

Execute SQL queries inside Python

Calculate total quantity and total revenue

Display the results

Visualize revenue using a bar chart

🛠 Technologies Used

Python

SQLite (sqlite3 module – built-in)

Pandas

Matplotlib

Google Colab / Jupyter Notebook

📂 Database Details
Database Name:
sales_data.db
Table Name:
sales
Table Structure:
Column Name	Data Type	Description
product	TEXT	Product name
quantity	INTEGER	Quantity sold
price	REAL	Price per unit
🧩 Step-by-Step Implementation
✅ Step 1: Import Required Libraries
import sqlite3
import pandas as pd
import matplotlib.pyplot as plt
Explanation:

sqlite3 → Connects Python to SQLite database

pandas → Handles data in table format

matplotlib → Creates charts

✅ Step 2: Create and Connect to Database
conn = sqlite3.connect("sales_data.db")
Explanation:

Creates a database file named sales_data.db

If file already exists, it connects to it

✅ Step 3: Create Sales Table
conn.execute("""
CREATE TABLE IF NOT EXISTS sales (
    product TEXT,
    quantity INTEGER,
    price REAL
)
""")
Explanation:

Creates a table named sales

IF NOT EXISTS prevents error if table already exists

✅ Step 4: Insert Sample Data
conn.execute("INSERT INTO sales VALUES ('Pen', 10, 5)")
conn.execute("INSERT INTO sales VALUES ('Pencil', 20, 2)")
conn.execute("INSERT INTO sales VALUES ('Notebook', 15, 30)")
conn.execute("INSERT INTO sales VALUES ('Pen', 5, 5)")

conn.commit()
Explanation:

Adds sample records

commit() saves data permanently

✅ Step 5: Execute SQL Query
query = """
SELECT product,
       SUM(quantity) AS total_quantity,
       SUM(quantity * price) AS revenue
FROM sales
GROUP BY product
"""

df = pd.read_sql_query(query, conn)

print(df)
Explanation:

SUM(quantity) → Calculates total quantity sold

SUM(quantity * price) → Calculates total revenue

GROUP BY product → Groups same products together

read_sql_query() → Loads SQL result into pandas DataFrame

✅ Step 6: Create Bar Chart
df.plot(kind='bar', x='product', y='revenue')

plt.title("Revenue by Product")
plt.xlabel("Product")
plt.ylabel("Revenue")
plt.show()
Explanation:

Creates a bar chart

X-axis → Product

Y-axis → Revenue

📊 Sample Output
product	total_quantity	revenue
Notebook	15	450
Pen	15	75
Pencil	20	40

Bar chart displays revenue comparison visually.

💡 Interview Questions & Answers
1. How did you connect Python to database?

Using:

sqlite3.connect("sales_data.db")
2. What does GROUP BY do?

It groups rows with same product name and performs aggregation.

3. How did you calculate revenue?

Using:

SUM(quantity * price)
4. How did you visualize results?

Using matplotlib bar chart.

5. What does pandas do?

It stores SQL output in a structured DataFrame for easy analysis.

🎯 Conclusion

This project demonstrates:

Basic SQL queries

Database connection using Python

Aggregation using GROUP BY

Data visualization using matplotlib

Integration of SQL and Python for data analysis

This is a beginner-level project that helps understand how databases and Python work together in real-world data analysis.
