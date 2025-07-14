# Olympic_Games_Analysis_Dashboard

# 🏅 Olympic Games Dashboard – Power BI Project

Welcome to the **Olympic Games Analytics Dashboard** project! This project leverages **Power BI** to provide visual insights into Olympic history, participation, and medal distribution across years, countries, genders, and sports. Built using cleaned datasets and visual storytelling, this dashboard helps uncover patterns in global athletic performance.

---

## 📊 Project Overview

This Power BI dashboard analyzes historical Olympic data, providing visualizations and KPIs on:

- 🥇 Total medals won by country
- 👩‍🦰👨‍🦱 Medals by gender
- ❄️☀️ Performance in Winter vs Summer Olympics
- 📅 Medals by year
- 🏃‍♂️ Athletes by sport, gender, and age band
- 🌍 Country-wise athlete participation

---

## 📂 Dataset Details

This dashboard is powered by the following datasets:

### 🔹 `athlete_events`
Contains detailed Olympic event data (partially anonymized in your file):
- Event Name
- Athlete ID
- Year
- Gender
- Age
- Height
- Medal (Gold, Silver, Bronze)

### 🔹 `country_definitions`
Contains country-related metadata:
- NOC Code
- Country Name
- Notes / Comments

### 🔹 `Table_1` (Cleaned athlete + medal data)
- Age, Age Band
- Event, Games, City
- Height
- Medal counts (Gold_Medals, Silver_Medals, Bronze_Medals)

### 🔹 `Table_2` (Country mapping)
- NOC (National Olympic Committee)
- Region
- Notes

---

## 🧠 Tools & Technologies Used

- **Power BI Desktop**
- **Power Query Editor** (for data transformation)
- **DAX** (for measures and calculated fields)
- **Data Modeling** (star schema: fact + dimension tables)

---

## 🧮 Key DAX Measures Used

Here are a few core DAX calculations used in this dashboard:

```dax
Total Medals = COUNTROWS('Table_1')

Gold Medals = CALCULATE(COUNT('Table_1'[Gold_Medals]), NOT(ISBLANK('Table_1'[Gold_Medals])))

Silver Medals = CALCULATE(COUNT('Table_1'[Silver_Medals]), NOT(ISBLANK('Table_1'[Silver_Medals])))

Bronze Medals = CALCULATE(COUNT('Table_1'[Bronze_Medals]), NOT(ISBLANK('Table_1'[Bronze_Medals])))

Medals by Gender = CALCULATE([Total Medals], ALLEXCEPT('Table_1', 'Table_1'[Gender]))
