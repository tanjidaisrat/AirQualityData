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
