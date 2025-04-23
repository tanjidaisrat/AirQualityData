```markdown
# 🌍 Air Pollution & Health Analytics Using SQLite and Python  
🔗 [Open in Google Colab](https://colab.research.google.com/drive/11PSL0qJv6Snq4LiU4qAVSfvCpa89Z5pl?usp=sharing)

## 📌 Overview
This project analyzes the relationship between air quality and public health in urban environments using a structured data pipeline built with **SQLite** and **Python** in **Google Colab**. It involves building a relational database, cleaning and transforming raw CSV data, performing SQL-based analysis, and visualizing pollution trends and city-wise air quality.

---

## 🎯 Objectives
- Design a clean and scalable SQL database from air quality datasets
- Conduct city-wise and time-based air pollution analysis
- Visualize the most polluted cities and pollution patterns over years
- Showcase real-world data handling and analytics skills for recruiters

---

## 🛠️ Tools & Technologies
- **Languages**: Python, SQL (SQLite)
- **Tools**: Google Colab, ipython-sql, PrettyTable
- **Libraries**: Pandas, Matplotlib

---

## 🧱 Database Schema

| Table              | Description                                                  |
|-------------------|--------------------------------------------------------------|
| `cities`          | Stores unique city names with auto-incremented ID            |
| `air_quality`     | Pollution, temperature, humidity data linked by city_id      |
| `health_indicators` *(optional)* | Mortality and life expectancy per city per year |

```sql
CREATE TABLE IF NOT EXISTS cities (
    city_id INTEGER PRIMARY KEY AUTOINCREMENT,
    city_name TEXT NOT NULL
);
CREATE TABLE IF NOT EXISTS air_quality (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    city_id INTEGER,
    date TEXT,
    co REAL,
    no2 REAL,
    pm10 REAL,
    temperature REAL,
    humidity REAL,
    FOREIGN KEY(city_id) REFERENCES cities(city_id)
);
```

---

## 🔄 ETL Process
- Uploaded and inspected CSV data
- Cleaned column names and handled missing values
- Added city metadata for relational mapping
- Inserted structured data into SQLite using `to_sql()`
- Verified referential integrity and column alignment

---

## 🔍 Analysis Examples

### 🔝 Top 10 Most Polluted Cities (PM10)
```sql
SELECT c.city_name, AVG(a.pm10) AS avg_pm10
FROM air_quality a
JOIN cities c ON a.city_id = c.city_id
GROUP BY c.city_name
ORDER BY avg_pm10 DESC
LIMIT 10;
```

### 📆 Year-wise Trend (Delhi)
```sql
SELECT SUBSTR(date, 1, 4) AS year, AVG(pm10) AS avg_pm10
FROM air_quality a
JOIN cities c ON a.city_id = c.city_id
WHERE c.city_name = 'Delhi'
GROUP BY year
ORDER BY year;
```

### 🌡️ Environmental Summary
```sql
SELECT ROUND(AVG(temperature), 2) AS avg_temp, 
       ROUND(AVG(humidity), 2) AS avg_humidity,
       ROUND(AVG(pm10), 2) AS avg_pm10
FROM air_quality;
```

---

## 📊 Visualization

- Used `Matplotlib` to display:
  - Bar chart of **Top 10 polluted cities**
  - Line plot of **yearly PM10 trend**
- Custom-styled plots with labeled axes, rotated ticks, and compact layout

```python
plt.bar(top_cities_df['city_name'], top_cities_df['avg_pm10'], color='tomato')
plt.title('Top 10 Most Polluted Cities by PM10')
```

---

## 🧠 Key Skills Demonstrated

- SQL database design and normalization
- Real-world data cleaning and transformation
- Writing performant SQL queries with joins and aggregation
- Data storytelling through effective visualizations
- Integration of Python, SQL, and Jupyter/Colab

---

## 📁 Dataset Summary
- **File Used**: `AirQuality 2.csv`  
- **Size**: < 3MB  
- **Features**: Date, CO, NO₂, PM10, Temperature, Humidity, City

---

## 🚀 Why This Matters to Recruiters
✅ Real-world dataset  
✅ Full data pipeline (ingestion → transformation → analysis → visualization)  
✅ Cloud-native (Google Colab) and scalable (SQL-based)  
✅ Demonstrates both **technical depth** and **analytical thinking**

---

## 📬 Let's Connect
📧 Email: [tanjidaisratr@gmail.com]  
🔗 LinkedIn: [Your LinkedIn Profile]  
🐍 GitHub: [https://github.com/tanjidaisrat]

---
