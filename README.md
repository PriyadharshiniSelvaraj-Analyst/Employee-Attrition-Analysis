# 📊 Employee Attrition Analysis & Insights | HR Analytics Dashboard

> *Tools:* Microsoft Excel | Power BI | Power Query | DAX | Star Schema Data Modeling  
> *Domain:* Human Resources | Workforce Analytics | Talent Retention  
> *Author:* Priyadharshini S. ([LinkedIn](https://www.linkedin.com/in/priyadharshini-selvaraj-09a030235/))

![Power BI](https://img.shields.io/badge/Tool-Power%20BI-yellow) ![Excel](https://img.shields.io/badge/Tool-Excel-green) ![Domain](https://img.shields.io/badge/Domain-HR%20Analytics-blue) ![Focus](https://img.shields.io/badge/Focus-Data%20Analytics-orange) ![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

<div align="center">

<img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=700&size=35&duration=3000&pause=1000&color=00F5D4&center=true&vCenter=true&width=650&height=80&lines=HR+Analytics+%26+Attrition+Dashboard;Data-Driven+Workforce+Insights;Power+BI+%2B+Excel+Star+Schema" alt="Typing SVG" />

<p align="center">
  <b>An end-to-end Business Intelligence solution designed to diagnose attrition drivers, evaluate workforce demographics, and optimize talent retention strategies.</b>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Microsoft%20Excel-1D6F42?style=for-the-badge&logo=microsoft-excel&logoColor=white" alt="Excel" />
  <img src="https://img.shields.io/badge/Power%20Query-0078D4?style=for-the-badge&logo=powerquery&logoColor=white" alt="Power Query" />
  <img src="https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black" alt="Power BI" />
  <img src="https://img.shields.io/badge/DAX-2EA043?style=for-the-badge&logo=databricks&logoColor=white" alt="DAX" />
  <img src="https://img.shields.io/badge/Data%20Modeling-0052CC?style=for-the-badge&logo=postgresql&logoColor=white" alt="Data Modeling" />
</p>

</div>

---

## 📌 Table of Contents
- [Executive Summary](#-executive-summary)
- [Key Business Metrics & KPIs](#-key-business-metrics--kpis)
- [System Architecture & Analytical Workflow](#-system-architecture--analytical-workflow)
- [Data Modeling & Star Schema Architecture](#-data-modeling--star-schema-architecture)
- [Complete Implementation Code Package](#-complete-implementation-code-package)
  - [DAX Measures Script](#1-dax-measures-script)
  - [Power Query M-Code](#2-power-query-m-code-data-transformation)
- [Key Insights & Analytical Findings](#-key-insights--analytical-findings)
- [Strategic HR Recommendations](#-strategic-hr-recommendations)
- [Project Repository Structure](#-project-repository-structure)
- [How to Run / Deployment Steps](#-how-to-run--deployment-steps)
- [Author & Contact](#-author--contact)

---

## 📋 Executive Summary

From a *Senior Data Analyst* perspective, employee turnover represents a significant operational friction point—inducing recruitment overheads, loss of institutional knowledge, and diminished team productivity.

This project delivers an enterprise-grade *HR Analytics & Attrition Dashboard* built on a comprehensive dataset of *15,000 employee records. Using **Microsoft Excel* and *Power Query* for ingestion, schema normalisation, and data hygiene, the dataset was modeled in *Power BI* using an optimized *Star Schema. Through complex **DAX measures*, time intelligence, interactive filtering, and dynamic KPI tracking, this project pinpoints exact attrition vectors across departments, compensation tiers, tenure bands, and performance metrics.

---

## 📈 Key Business Metrics & KPIs

| Metric | Value | Business Context & Relevance |
| :--- | :---: | :--- |
| *Total Headcount* | 15,000 | Baseline active and historical employee base analyzed. |
| *Active Employees* | 12,630 | Retained headcount generating current business value. |
| *Total Attrition* | 2,370 | Total voluntary and involuntary employee exits. |
| *Attrition Rate* | 15.80% | Primary organizational churn benchmark. |
| *Avg. Monthly Income* | $6,503 | Overall compensation benchmark across all roles. |
| *Avg. Years at Company*| 7.01 yrs| Average organization tenure across active and churned staff. |
| *Avg. Satisfaction Score*| 2.72 / 4.0 | Measure of employee engagement and job satisfaction. |

---

## 🏗️ System Architecture & Analytical Workflow

text

┌────────────────────────┐
│   Raw HR Data Source   │ (Excel Dataset: 15,000 Records)
└───────────┬────────────┘
            │
            ▼
┌────────────────────────┐
│ MS Excel / Power Query │ (Data Hygiene, Schema Cleaning, Type Casting, Unpivoting)
└───────────┬────────────┘
            │
            ▼
┌────────────────────────┐
│  Star Schema Modeling  │ (Fact_Attrition linked to Dim_Employee, Dim_Department, Dim_Date)
└───────────┬────────────┘
            │
            ▼
┌────────────────────────┐
│   Power BI DAX Engine  │ (Dynamic Measures, Time Intelligence, Conditional Indicators)
└───────────┬────────────┘
            │
            ▼
┌────────────────────────┐
│ Executive Dashboards   │ (Interactive Visual Views, Attrition Heatmaps, Strategic Recommendations)
└────────────────────────┘


---

## 📐 Data Modeling & Star Schema Architecture

To optimize query performance, minimize memory overhead, and ensure seamless drill-down capabilities, the data model was structured using a *Star Schema design* in Power BI Desktop:

text

         ┌──────────────────────────────┐
         │        Dim_Department        │
         ├──────────────────────────────┤
         │ Department_Key (PK)          │
         │ Department_Name              │
         │ Job_Role                     │
         └──────────────┬───────────────┘
                        │
                        │ (1:N)
                        ▼

┌─────────────────┐  (1:N)  ┌──────────────────────────────────┐  (N:1)  ┌─────────────────┐
│  Dim_Employee   ├────────►│          Fact_Attrition          │◄────────┤    Dim_Date     │
├─────────────────┤         ├──────────────────────────────────┤         ├─────────────────┤
│ Employee_ID(PK) │         │ Attrition_ID (PK)                │         │ Date_Key (PK)   │
│ Age, Gender     │         │ Employee_ID (FK)                 │         │ Date, Year      │
│ MaritalStatus   │         │ Department_Key (FK)              │         │ Quarter, Month  │
│ EducationLevel  │         │ Date_Key (FK)                    │         │ Fiscal_Period   │
└─────────────────┘         │ Attrition_Status (Yes/No)        │         └─────────────────┘
                            │ MonthlyIncome, Overtime, Distance│
                            │ PerformanceRating, Satisfaction  │
                            └──────────────────────────────────┘


---

## 💻 Complete Implementation Code Package

### 1. DAX Measures Script

dax
// ==========================================
// A. CORE HEADCOUNT & ATTRITION MEASURES
// ==========================================

// Total Employee Count
Total Employees = COUNTROWS('Fact_Attrition')

// Total Attrition Count
Total Attrition = 
CALCULATE(
    COUNTROWS('Fact_Attrition'),
    'Fact_Attrition'[Attrition_Status] = "Yes"
)

// Attrition Rate %
Attrition Rate = 
DIVIDE(
    [Total Attrition],
    [Total Employees],
    0
)

// Active Employees Count
Active Employees = 
CALCULATE(
    COUNTROWS('Fact_Attrition'),
    'Fact_Attrition'[Attrition_Status] = "No"
)


// ==========================================
// B. ADVANCED ANALYTICAL & CONDITIONAL DAX
// ==========================================

// Dynamic Attrition Risk Classification
Attrition Risk Level = 
SWITCH(
    TRUE(),
    [Attrition Rate] >= 0.20, "High Risk (>20%)",
    [Attrition Rate] >= 0.12, "Medium Risk (12-20%)",
    "Low Risk (<12%)"
)

// Average Monthly Income of Attrited Workforce
Avg Income Attrited = 
CALCULATE(
    AVERAGE('Fact_Attrition'[MonthlyIncome]),
    'Fact_Attrition'[Attrition_Status] = "Yes"
)

// Average Tenure for Retained Employees
Avg Tenure Active (Years) = 
CALCULATE(
    AVERAGE('Fact_Attrition'[YearsAtCompany]),
    'Fact_Attrition'[Attrition_Status] = "No"
)


// ==========================================
// C. TIME INTELLIGENCE & PERIOD ANALYSIS
// ==========================================

// Year-to-Date Attrition Count
Attrition YTD = 
TOTALYTD([Total Attrition], 'Dim_Date'[Date])

// Previous Year Attrition Benchmark
Attrition Previous Year = 
CALCULATE(
    [Total Attrition],
    SAMEPERIODLASTYEAR('Dim_Date'[Date])
)


---

### 2. Power Query M-Code (Data Transformation)

powerquery
let
    // Step 1: Load Source File
    Source = Excel.Workbook(File.Contents("C:\Data\HR_Employee_Attrition_Raw.xlsx"), null, true),
    RawData_Sheet = Source{[Item="HR_Data",Kind="Sheet"]}[Data],

    // Step 2: Elevate Header Row
    PromotedHeaders = Table.PromoteHeaders(RawData_Sheet, [PromoteAllScalars=true]),

    // Step 3: Explicit Data Type Casting
    TypedColumns = Table.TransformColumnTypes(PromotedHeaders, {
        {"Employee_ID", Int64.Type},
        {"Age", Int64.Type},
        {"MonthlyIncome", Currency.Type},
        {"YearsAtCompany", Int64.Type},
        {"Attrition_Status", type text},
        {"OverTime", type text},
        {"Department", type text},
        {"JobRole", type text}
    }),

    // Step 4: Text Hygiene and Space Trimming
    CleanedText = Table.TransformColumns(TypedColumns, {
        {"Department", Text.Trim, type text},
        {"Attrition_Status", Text.Trim, type text},
        {"OverTime", Text.Trim, type text}
    }),

    // Step 5: Replace Null Numeric Values
    ReplacedNulls = Table.ReplaceValue(CleanedText, null, 0, Replacer.ReplaceValue, {"YearsAtCompany", "MonthlyIncome"})
in
    ReplacedNulls


---

## 🔍 Key Insights & Analytical Findings

### 1. 💼 Overtime vs. Attrition Correlation
* *Insight:* Staff working frequent *Overtime* suffer an attrition rate of *28.4%, compared to **10.2%* for employees without overtime demands.
* *Driver:* Work-life imbalance and workload strain represent major triggers for voluntary exit among mid-level operational roles.

### 2. 💵 Compensation & Pay Bracket Volatility
* *Insight:* Over *52%* of total organizational churn occurs in the lowest salary bracket ($2,000 – $4,500/month).
* *Driver:* Elevated vulnerability to market poaching for minor compensation gains.

### 3. 🏢 Departmental Risk Profiling
* *Insight:* *Sales* (20.6% attrition rate) and *Research & Development* (14.8% attrition rate) record the highest absolute turnover.
* *Driver:* High pressure and commission targets in Sales; highly competitive market recruitment in R&D roles.

### 4. ⏳ Early Tenure Career Bottlenecks
* *Insight:* *38%* of total turnover occurs within the first *3 years* of service.
* *Driver:* Early career misalignment, onboarding gaps, and perceived lack of rapid career development options.

---

## 💡 Strategic HR Recommendations

1. ⚖️ *Overtime Workload Governance:* Institute strict overtime limits and automated monitoring alerts when departmental overtime exceeds safety operational targets.
2. 💰 *Entry-Level Compensation Calibration:* Re-evaluate compensation bands for high-risk, entry-level positions to align with competitive market medians.
3. 🚀 *Structured Early Career Development:* Establish 12-month and 24-month career progression pathways to safeguard retention during early employment years.
4. 📝 *Targeted Stay Interviews:* Conduct proactive quarterly stay interviews for high-performing staff within high-churn departments (Sales & R&D).

---

## 📁 Project Repository Structure

text
├── 📂 Data
│   ├── HR_Employee_Attrition_Raw.xlsx       # Raw source dataset (15,000 rows)
│   └── HR_Employee_Attrition_Cleaned.csv    # Cleaned, structured dataset
├── 📂 PowerBI
│   └── HR_Analytics_Attrition_Dashboard.pbix # Full Power BI Report File
├── 📂 Documentation
│   ├── Data_Dictionary.md                   # Field definitions & data dictionary
│   └── Model_Schema.png                     # Visual star schema reference
└── README.md                                # Unified technical documentation


---

## 🛠️ How to Run / Deployment Steps

1. *Clone the Repository:*
   bash
   git clone https://github.com/your-username/HR-Employee-Attrition-Analysis.git
   
2. *Review Data Pipeline in Excel / Power Query:*
   * Open Data/HR_Employee_Attrition_Raw.xlsx to review baseline formulas and data formatting.
3. *Open Power BI Dashboard:*
   * Open PowerBI/HR_Analytics_Attrition_Dashboard.pbix in *Power BI Desktop*.
   * Update data source file paths if required and hit *Refresh*.
4. *Interact with Analytics:*
   * Leverage dynamic slicers for Department, Income Bracket, Tenure, and Overtime Status.

---

## 👩‍💻 Author & Contact

*Priyadharshini S.*  
Aspiring Data Analyst | Excel, Power BI, DAX & Data Modeling

* 💼 *LinkedIn:* [Priyadharshini Selvaraj](https://www.linkedin.com/in/priyadharshini-selvaraj-09a030235/)
* 📧 *Contact:* Open for Data Analytics roles, collaborations, and project inquiries.

---

## 📚 Tags

#PowerBI #Excel #EmployeeAttrition #HRAnalytics #DataAnalysis #DAX #PowerQuery #DataVisualization #StarSchema #BusinessIntelligence #PeopleAnalytics #DataModeling #WorkforceAnalytics #HRDashboard
