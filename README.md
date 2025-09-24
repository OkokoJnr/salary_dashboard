
---

# Excel Salary Dashboard

![1\_Salary\_Dashboard.png](/0_Resources/Images/1_Salary_Dashboard_Final_Dashboard.gif)

## Introduction

This data-jobs salary dashboard helps job seekers explore salaries across roles, countries, and work types, ensuring fair compensation and informed career choices.
It recreates the learning project described in the brief using dynamic Excel techniques, with clean formulas, filtered dropdowns, and ready-to-use visuals.

### Dashboard File

My final dashboard is in **[doc\Salary\_Dashboard.xlsx](Salary_Dashboard.xlsx)**.

### Excel Skills Used

* **📉 Charts**
* **🧮 Formulas & Functions (dynamic arrays)**
* **❎ Data Validation (dropdowns)**

---

## Data Jobs Dataset

The dataset contains job_title_short, job_title, job_location, job_via, job_schedule_type, job_work_from_home, search_location, job_posted_date, job_no_degree_mention, job_health_insurance, job_country, salary_rate, salary_year_avg, salary_hour_avg, company_name, and job_skills.

## Key columns
* **👨‍💼 Job titles**
* **💰 Salaries (annual)**
* **📍 Locations (countries)**
* **🛠️ Schedule types / skills (as applicable)**

> The median calculations and unique lists recalculate automatically in **Excel 365 / 2021+** (dynamic arrays enabled).

---

## Dashboard Build

### 📉 Charts

#### 📊 Data Science Job Salaries — Bar Chart

<img src="/0_Resources/Images/1_Salary_Dashboard_Chart1.png" width="850" height="550" alt="Salary Dashboard Chart1">

* 🛠️ **Excel Features:** Clustered **Bar Chart** with formatted salary axis; layout optimised for readability.
* 🎨 **Design Choice:** Horizontal bars for quick comparison of median salaries by role.
* 📉 **Data Organisation:** The Top-10 median table on the **dashboard** sheet (A9\:B18) feeds the chart.
* 💡 **Insights Gained:** Senior and engineering roles typically out-earn entry/analyst roles within the sample.


#### 🗺️ Country Median Salaries — Filled Map

![1\_Salary\_Dashboard\_Chart2.png](/0_Resources/Images/1_Salary_Dashboard_Country_Map.gif)

* 🛠️ **Excel Features:** Use Excel’s **Filled Map** with the pre-built **country median** table on `calc!K2:L` (Country, MedianSalary).
* 🎨 **Design Choice:** Colour gradient to distinguish salary bands across regions.
* 📊 **Data Representation:** Median salary per country (where data exists).
* 👁️ **Visual Enhancement:** Immediate grasp of geographic disparities.
* 💡 **Insights Gained:** Highlights higher/lower salary regions at a glance.

> Insert in Excel: **Insert → Maps → Filled Map**, (filtered out blanks before charting for a cleaner result).

---

## 🧮 Formulas & Functions

### 💰 Median Salary by Job Title (filtered by selections)

```excel
=MEDIAN(
IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))* 
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
)
)
```

* 🔍 **Multi-criteria filtering:** Job title, country, and schedule type; excludes blanks/zeros.
* 📊 **Array logic:** `MEDIAN` + `IF` across structured table columns.
* 🎯 **Purpose:** Feeds the Top-10 medians displayed on the dashboard.

🍽️ **Background Table**
![1\_Salary\_Dashboard\_Screenshot1.png](/0_Resources/Images/1_Salary_Dashboard_Screenshot1.png)

📉 **Dashboard Implementation** <img src="/0_Resources/Images/1_Salary_Dashboard_Job_Title.png" width="400" height="500" alt="Salary Dashboard Title">

---

### ⏰ Filtered List of Job Schedule Types

```excel
=FILTER(J2#,(NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#))))*(J2#<>0))
```

* 🔍 **Unique list generation:** Excludes values containing “and” or commas; omits zeros/blanks.
* **🎯 Purpose:** Provides a clean, validated list for dropdowns and reporting.

🍽️ **Background Table**
![1\_Salary\_Dashboard\_Screenshot2.png](/0_Resources/Images/1_Salary_Dashboard_Screenshot2.png)

📉 **Dashboard Implementation** <img src="/0_Resources/Images/1_Salary_Dashboard_Type.png" width="350" height="500" alt="Salary Dashboard Type">

---

## ❎ Data Validation

### 🔍 Filtered Dropdowns

Implement the filtered lists as **Data Validation** sources for `Job Title`, `Country`, and `Type` on the **dashboard** sheet to:

* 🎯 Restrict input to validated values
* 🚫 Prevent inconsistent entries
* 👥 Improve usability and consistency

<img src="/0_Resources/Images/1_Salary_Dashboard_Data_Validation.gif" width="425" height="400" alt="Salary Dashboard Data Validation">

---

## Getting Started

1. **Open** **[1\_Salary\_Dashboard.xlsx](1_Salary_Dashboard.xlsx)**.

2. Go to **jobs** and paste your full dataset under the existing headers:

   ```
   job_id, job_title_short, job_country, job_schedule_type, salary_year_avg
   ```

3. Go to **dashboard** and use the dropdowns in:

   * **B2** (Job Title)
   * **B3** (Country)
   * **B4** (Type)

4. The **Top-10** table and **bar chart** update automatically (dynamic arrays).


> **Excel version:** Best with **Microsoft 365 / Excel 2021+**. Older versions may require PivotTables and helper columns.

---

## Troubleshooting

* If lists don’t appear, ensure **Formulas → Calculation Options = Automatic** and your Excel supports **dynamic arrays**.
* Confirm `salary_year_avg` are **numeric** (no currency symbols or text).
* For an “**All**” option in filters, add “All” to each dropdown’s source and wrap conditions with:

  ```excel
  IF(selected="All", TRUE, your_condition_here)
  ```

---

## Project Structure

```
.
├─ doc/Salary_Dashboard.xlsx     # Working dashboard (jobs, calc, dashboard)
├─ README.md                    # This file
└─ 0_Resources/
   └─ Images/
      ├─ Salary_Dashboard_Final_Dashboard.gif
      ├─ Salary_Dashboard_Job_Title.png
      ├─ Salary_Dashboard_Type.png
      └─ Salary_Dashboard_Country_Map.gif
```

---

## Acknowledgements (Source)

This project **recreates and acknowledges** the original *Excel Salary Dashboard* concept from a learning project Luke Barousse.
**Credit:** Original concept and instructional framing by the **Luke Barousse**

