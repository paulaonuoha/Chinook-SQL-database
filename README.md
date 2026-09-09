# 🎵 Chinook Database Analysis Project

https://roadmap.sh/projects/querying-sql-python

## 📖 Overview

A data analysis project that combines **Python** and **SQL** to analyze the Chinook digital music store database. Demonstrates real-world business intelligence by connecting to SQLite, writing complex queries, and visualizing insights.

## 🎯 Business Questions Answered

| # | Question | Key Metrics |
|---|----------|-------------|
| 1 | **10 best-selling tracks?** | Purchases, Revenue, Artist |
| 2 | **Top revenue country?** | Total Revenue, Invoices, Avg Value |
| 3 | **Best sales employee?** | Revenue, Customers, Sales Count |

## 🛠️ Technologies

- **Python 3.7+** - Main language
- **SQLite3** - Database engine
- **Pandas** - Data manipulation
- **Matplotlib/Seaborn** - Visualization
- **Jupyter** - Interactive notebook

## 📦 Quick Start

### 1. Install Dependencies
```bash
pip install pandas matplotlib seaborn jupyter
```

### 2. Clone & Run
```bash
git clone https://github.com/paulaonuoha/Chinook-SQL-database.git
cd chinook-analysis
jupyter notebook chinook_analysis.ipynb
```

### 3. Requirements File
Create `requirements.txt`:
```txt
pandas>=2.0.0
matplotlib>=3.5.0
seaborn>=0.12.0
jupyter>=1.0.0
```

## 🗄️ Database Schema

```
Artist → Album → Track → InvoiceLine → Invoice
Employee → Customer → Invoice
Track → Genre, MediaType
```

**Key Tables:** Artist, Album, Track, Customer, Employee, Invoice, InvoiceLine, Genre

## 📊 Sample Queries

### Best-Selling Tracks
```sql
SELECT t.Name, ar.Name AS Artist, COUNT(il.InvoiceLineId) AS Purchases
FROM Track t
JOIN Album a ON t.AlbumId = a.AlbumId
JOIN Artist ar ON a.ArtistId = ar.ArtistId
JOIN InvoiceLine il ON t.TrackId = il.TrackId
GROUP BY t.TrackId
ORDER BY Purchases DESC
LIMIT 10;
```

### Revenue by Country
```sql
SELECT BillingCountry, SUM(Total) AS Revenue
FROM Invoice
GROUP BY BillingCountry
ORDER BY Revenue DESC;
```

### Top Sales Employee
```sql
SELECT e.FirstName || ' ' || e.LastName AS Employee,
       SUM(i.Total) AS Revenue
FROM Employee e
JOIN Customer c ON e.EmployeeId = c.SupportRepId
JOIN Invoice i ON c.CustomerId = i.CustomerId
GROUP BY e.EmployeeId
ORDER BY Revenue DESC;
```

## 📈 Visualizations Created

1. **Bar Chart** - Top 10 best-selling tracks
2. **Bar Chart** - Revenue by country
3. **Bar Chart** - Employee performance
4. **Bar Chart** - Genre revenue
5. **Line Chart** - Monthly revenue trends

## 🎓 Key Learnings

### SQL Skills
- SELECT, JOIN, GROUP BY, ORDER BY
- Aggregate functions (COUNT, SUM, AVG)
- Subqueries and CTEs
- Date functions

### Python Skills
- sqlite3 database connection
- Pandas DataFrame manipulation
- Data visualization with Matplotlib
- Exporting results to CSV

## 📤 Export Results

The analysis automatically exports:
- `best_selling_tracks.csv`
- `revenue_by_country.csv`
- `top_employees.csv`
- `genre_sales.csv`
- `monthly_revenue.csv`
- `customer_lifetime_value.csv`

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request



## 🌟 Support

⭐ Star this repo if you found it helpful!

---

**Made with ❤️ by Paula**
