# DAX Measures

The report documents eight DAX measures created for the FMCG analysis.

## 1. Total Gross Sales

```DAX
Total Gross Sales =
SUM('fmcg_sales_marketing_profitability_2023_2025'[Gross_Sales_USD])
```

Adds gross sales before discount.

## 2. Total Net Revenue

```DAX
Total Net Revenue =
SUM('fmcg_sales_marketing_profitability_2023_2025'[Net_Revenue_USD])
```

Adds revenue after discount.

## 3. Total Profit

```DAX
Total Profit =
SUM('fmcg_sales_marketing_profitability_2023_2025'[Profit_USD])
```

Adds total profit.

## 4. Total Units Sold

```DAX
Total units sold =
SUM('fmcg_sales_marketing_profitability_2023_2025'[Units_Sold])
```

Adds all units sold.

## 5. Average Order Value

```DAX
Average Order Value =
DIVIDE(
    [Total Net Revenue],
    DISTINCTCOUNT('fmcg_sales_marketing_profitability_2023_2025'[Order_ID]),
    0
)
```

Calculates average net revenue per order.

## 6. Revenue Share %

```DAX
Revenue Share % =
DIVIDE(
    [Total Net Revenue],
    CALCULATE(
        [Total Net Revenue],
        ALL('fmcg_sales_marketing_profitability_2023_2025'[Sales_Channel])
    ),
    0
)
```

Calculates each sales channel's share of total net revenue.

## 7. Marketing ROI

```DAX
Marketing ROI =
DIVIDE(
    [Total Profit],
    SUM('fmcg_sales_marketing_profitability_2023_2025'[Marketing_Spend_USD]),
    0
)
```

Calculates profit earned for each $1 of marketing spend.

## 8. Logistics Cost %

```DAX
Logistics Cost % =
DIVIDE(
    SUM('fmcg_sales_marketing_profitability_2023_2025'[Logistics_Cost_USD]),
    [Total Net Revenue],
    0
)
```

Calculates logistics cost as a percentage of net revenue.

All division-based measures use `DIVIDE()` with `0` as the alternate result.
