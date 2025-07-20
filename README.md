# 📊 Loan Default Analysis using Power BI
An end-to-end data analysis project built using Power BI that explores patterns in loan defaults. The project includes data ingestion from SQL Server via Dataflow, transformation in Power Query, DAX-based analytics, and interactive report creation. The report is published to Power BI Service with scheduled and incremental refresh configured.


---

## 📌 Problem Statement

Financial institutions need to assess the risk of loan defaults effectively. This project helps in:
- Identifying patterns in loan defaults.
- Analyzing customer demographics and credit behavior.
- Forecasting and comparing Year-on-Year (YoY) loan performance.
- Creating data models and dashboards for decision-making.

---

## 📊 Data Source

- **Original Data**: Imported into **SQL Server**.
- **Connected via**: **Power BI Dataflow** (to simulate live/enterprise data environments).
- **File Format**: CSV (`Loan_default.csv`)
- **Size**: ~200,000 records
- **Columns include**: `LoanAmount`, `Income`, `Age`, `Employment Type`, `Education`, `Credit Score`, `Marital Status`, `Default`, etc.

---

## 🛠 Tools & Technologies

- **Power BI Desktop**
- **Power BI Service**
- **Power Query Editor**
- **DAX (Data Analysis Expressions)**
- **SQL Server (for staging the data)**
- **Power BI Dataflows**
- **On-premises Data Gateway (Standard Mode)**

---

## 📈 Key Visualizations & Insights

| Report Page | Insight | DAX Functions Used |
|-------------|--------|--------------------|
| **Loan Amount by Purpose** | Total loan distributed by loan types (e.g., car, personal) | `SUMX`, `FILTER`, `NOT`, `ISBLANK` |
| **Average Income by Employment** | Compares income across employment types | `CALCULATE`, `AVERAGE`, `ALLEXCEPT` |
| **Default Rate by Employment Type** | Tracks risk across job roles | `COUNTROWS`, `DIVIDE`, `FILTER`, `ALL` |
| **Average Loan by Age Group** | Age-based segmentation of loan amounts | `AVERAGE`, `AVERAGEX`, `VALUES` |
| **Default Rate by Year** | Tracks historical loan default patterns | `CALCULATE`, `ALLEXCEPT`, `DIVIDE` |
| **Median Loan by Credit Score** | Credit risk classification | `MEDIANX` |
| **YOY Loan & Default Measures** | Business trend analysis | Custom YOY DAX Measures |
| **Decomposition Tree** | Interactive root cause analysis | `SWITCH`, `CALCULATE` |
| **Donut & Column Charts** | Categorical comparison | `SUM`, `AVERAGEX`, `CALCULATE` |

---

## 🧠 DAX Highlights

- `YOY_Loan_Amount = CALCULATE([TotalLoan], SAMEPERIODLASTYEAR('Date'[Date]))`
- `DefaultRate = DIVIDE(COUNTROWS(Defaulted), COUNTROWS(TotalLoans))`
- `MedianLoan = MEDIANX(FILTER('Loans', NOT(ISBLANK([LoanAmount]))), [LoanAmount])`

📂 All major DAX measures are included in [`DAX-snippets/`](DAX-snippets/).

---

## 🔄 Dataflow & Gateway Setup

Detailed guide available at [`docs/Dataflow_Gateway_Setup.md`](docs/Dataflow_Gateway_Setup.md) which includes:
- Installing SQL Server and importing data
- Creating a Dataflow in Power BI Service
- Setting up a Standard Mode On-prem Gateway
- Scheduling automatic and incremental refresh

---

## 🚀 How to Use This Project

1. **Clone the repo**:

   ```bash
   git clone https://github.com/aniketnikam/loan-default-powerbi.git
   cd loan-default-powerbi

