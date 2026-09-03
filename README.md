# HR Analytics Dashboard | Excel Project
Headcount, Attrition & Compensation Insights | From Raw Employee Records to an Interactive HR Dashboard

---

## Table of Contents
- [Project Overview](#project-overview)
- [Tools and Technologies](#tools-and-technologies)
- [Dataset Overview](#dataset-overview)
- [Data Modeling (Power Query + DAX)](#data-modeling-power-query--dax)
- [Excel Dashboard](#excel-dashboard)
- [Key Insights](#key-insights)
- [Recommendations](#recommendations)
- [Future Work](#future-work)
- [Repository Structure](#repository-structure)

---

## Project Overview

This project analyzes workforce data for **311 employees** to uncover patterns in headcount, attrition, and compensation. Using Power Query and Power Pivot (DAX), raw employee records are turned into an interactive Excel dashboard giving real-time insight into who's active, who's leaving, and where — supporting faster, evidence-based HR decisions.

---

## Tools and Technologies

![Excel](https://img.shields.io/badge/Microsoft_Excel-217346?style=for-the-badge&logo=microsoft-excel&logoColor=white)
![Power Query](https://img.shields.io/badge/Power_Query-004B8D?style=for-the-badge)
![DAX](https://img.shields.io/badge/Power_Pivot%2FDAX-9A4993?style=for-the-badge)

---

## Dataset Overview

**Columns:**
```
Employee_Name, EmpID, MarriedID, MaritalStatusID, GenderID, EmpStatusID,
PerfScoreID, FromDiversityJobFairID, Salary, Termd, PositionID, State, DOB,
Sex, MaritalDesc, CitizenDesc, HispanicLatino, RaceDesc, DateofHire,
DateofTermination, TermReason, Department ID, ManagerID, RecruitmentSource,
EngagementSurvey, EmpSatisfaction, SpecialProjectsCount,
LastPerformanceReview_Date, DaysLateLast30, Absences
```

**Lookup tables:** Performance Score, State, Managers, Empstatus, Position, department

**Sample Preview:**

| Employee_Name | EmpID | Department ID | Salary | Termd | PerfScoreID |
|---|---|---|---|---|---|
| ... | ... | ... | ... | 0/1 | ... |

---

## Data Modeling (Power Query + DAX)

Rather than formula-driven worksheet columns, this workbook loads data straight into Excel's Data Model:

- **8 Power Query queries** (`Data`, `Date`, `department`, `Empstatus`, `Managers`, `Performance Score`, `Position`, `State`) import and shape the source tables before loading them to the model.
- **12 DAX measures** in Power Pivot drive every KPI card and chart on the dashboard:

| Measure | Purpose |
|---|---|
| `Employees` | Current headcount |
| `PY employees` | Prior-year headcount (for YoY comparison) |
| `YOY Empgrowth` | Year-over-year headcount growth |
| `Active` | Count of active employees |
| `Terminated` | Count of terminated employees |
| `Attrition Rate` | Terminated ÷ total headcount |
| `Sum of isTerminated` | Underlying terminated flag total |
| `Avg Salary` | Average salary |
| `Total Salary` | Total salary spend |
| `Avg Tenure` | Average years of tenure |
| `Average of Age` | Average employee age |
| `Avg Engagement` | Average engagement survey score |

> To view the DAX formula behind any measure: open `H_ANALYTICS.xlsx` → **Power Pivot tab → Manage** → select **Measures** in the grid.

- **13 PivotTables** feed **10 PivotCharts**, all connected to a Date-of-Hire timeline slicer.

---

## Excel Dashboard

The dashboard includes:
- KPI cards — Employees, Active, Attrition Rate, Avg Tenure, Avg Engagement, Total Salary, Avg Salary (with YoY trend arrow)
- Headcount by month (line/bar)
- Attrition by Department
- Top 5 Managers with Highest Attrition Rate
- Attrition by Performance Score
- Employee by Sex (donut)
- Performance by Sex

**Screenshot:**

![Visuals dashboard](images/visuals_dashboard.png)

---

## Key Insights

- Headcount stands at **311 employees**, up **0.3%** year-over-year, with **207 active** and **104 terminated**.
- Overall **attrition rate is 50.2%**, with average tenure of **10 years**.
- **Production** is both the largest department (209 employees) and the biggest driver of attrition (83 terminated) — far ahead of every other department.
- Average salary is **$69.0K** (**$21.47M** total salary spend); average engagement score is **4.11**.
- **Webster Butler** and **Amy Dunn** are the managers with the highest attrition rates (1.63 each), notably above the 1.13 company-wide average.
- Performance score correlates with attrition — employees furthest from "Fully Meets" show the largest attrition shares.

---

## Recommendations

- Prioritize retention initiatives in **Production**, since it accounts for the majority of both headcount and departures.
- Review management practices and workload for **Webster Butler** and **Amy Dunn's** teams given above-average attrition under their reports.
- Investigate the link between low performance scores and attrition to see whether it reflects a performance-management or an engagement issue.
- Track engagement score alongside attrition rate over time to catch early warning signs before termination.

---

## Future Work

- Automate data refresh from a live HR source instead of a static extract.
- Add a trend view of attrition rate over time (beyond the single YoY comparison).
- Rebuild the dashboard in Power BI for web-based, interactive sharing.

---

## Repository Structure

```
HR-Analytics-Dashboard-Excel/
├── README.md
├── HR_Analytics.xlsx
├── H_ANALYTICS.xlsx
└── images/
    └── visuals_dashboard.png
```
