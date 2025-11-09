# 💡 DAX Measures — Azure FinOps Dashboard

This file documents all the DAX measures used in the Azure FinOps Dashboard project.

---

## 🧾 Cost Analysis

### Total Cost
```DAX
TotalCost = SUM('Usage'[BillingPreTaxTotal])

```

### Total Daily Spend
```DAX
Total Daily Spend (All Services) = 
CALCULATE(
    SUM(Usage[BillingPreTaxTotal]),
    ALL(Meter[MeterCategory])
)

```
### Total Resources
```DAX
TotalResources = DISTINCTCOUNT('Usage'[MeterId])

```

### Cost Per Resource
```DAX
CostPerResource = DIVIDE( [TotalCost], [TotalResources], 0 )

```

### %Share of Total Cost
```DAX
%Share of Total Cost = 
DIVIDE([TotalCost], CALCULATE([TotalCost], ALL(Usage)), 0)

```



