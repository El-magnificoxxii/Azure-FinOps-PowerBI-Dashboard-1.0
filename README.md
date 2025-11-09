# 💰 Azure FinOps Power BI Dashboard 1.0

## 📘 Overview
This project demonstrates the use of **Power BI** for analyzing and visualizing **Azure cost and usage data** 
The dashboard provides key insights into **service-level spending**, **cost efficiency**, and **regional usage patterns**, enabling organizations to make data-driven decisions around cloud optimization and governance.

> **Note:** The dataset used in this project is a *sample CSP daily rate usage file* created for demonstration.  
> All data points are fictional and do not reflect any real customers or organizations.

---

## 🎯 Objectives
The goal of this project is to:
- Show how **FinOps principles** can be applied to Azure cost data.
- Provide visibility into **spending patterns across services, regions, and customers**.
- Identify **high-cost areas** and opportunities for optimization.
- Demonstrate **Power BI modelling and DAX proficiency**.

---

## 🧠 Key Insights From the Dashboard
1. **Top Services by Spend:** Identifies which Azure services (e.g., Virtual Machines, VPN Gateway, Storage) contribute most to total costs.  
2. **Cost per Service:** Calculates cost efficiency by dividing total service cost by number of active resources.  
3. **Daily Cost Trend:** Tracks day-to-day fluctuations to reveal unusual cost spikes.  
4. **Regional Usage:** Highlights which Azure regions drive the most consumption.  
5. **Cost by Sub-Meter Category:** Breaks services (like VM series) into finer detail to analyze per-category performance.  
6. **Customer Spend Analysis:** Shows the top-spending customers for transparency and billing insight.

---

## 📊 Dashboard Features
| Feature | Description |
|----------|--------------|
| **Dynamic Filters** | Customer, Meter Region, Date Range, and Service Type slicers for interactive analysis |
| **Drill-down Capability** | Click on a service to see detailed cost by sub-meter category |
| **Responsive Layout** | Optimized for readability with grouped visuals and consistent formatting |
| **KPI Cards** | Summarizes key metrics like total cost, total usage, and total resources |

---

## 🧩 Data Model
- **Usage Table:** Contains core CSP usage data (meter category, meter subcategory, usage date, billing pretax cost, etc.)
- **Date Table:** Created for proper time intelligence calculations (charge start, charge end, usage date)
- **Relationships:** 
  - `Usage[UsageDate]` → `Date[Date]`
  - `Usage[ServiceName]` → used for drill-down into subcategories

---

## ⚙️ DAX Measures
A few sample DAX formulas used in this report:

```DAX
Total Cost = SUM(Usage[BillingPreTax])

Resource Count = DISTINCTCOUNT(Usage[MeterID])

Cost per Service = DIVIDE([Total Cost], [Resource Count], 0)

% of Total Cost =
DIVIDE(
    [Total Cost],
    CALCULATE([Total Cost], ALL(Usage)),
    0
)

% of Service Cost =
DIVIDE(
    [Total Cost],
    CALCULATE([Total Cost], ALLEXCEPT(Usage, Usage[ServiceName])),
    0
)
```
## 📊 Dashboard Overview
| Visual                        | Description                                                      |
| ----------------------------- | ---------------------------------------------------------------- |
| 💰 **Daily Cost Trend**       | Displays total daily spend to track spending patterns.           |
| 🧩 **Cost per Service**       | Shows each Azure service's contribution to total cost.           |
| 🧱 **Average Cost per Resource** | Breaks down resource type cost (e.g., VM series, storage tiers). |
| 🌍 **Usage by Region**        | Identifies regions with the highest consumption.                 |
| 👥 **Top 5 Customers**        | Highlights customers driving the highest cloud cost.             |


## 📸 Screenshots

![Azure FinOps Dashboard](dashboard/Azure.png)

## 📁 Download the Power BI file

[Click here to download the .pbix file](dashboard/Azure%20FinOps%20Dashboard.pbix)



## 🧰 Tools & Technologies

- Power BI Desktop
- Microsoft Azure Usage Data (CSV Export)
- DAX
- Power Query (Data Cleaning)



