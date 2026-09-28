# Copilot-Assisted DAX Development Notes

## 1. Month-over-Month Growth %

### Copilot suggestion

Copilot suggested:

```DAX
Month-over-Month Sales Growth % =
VAR CurrentMonthSales = [Total Sales]
VAR PreviousMonthSales =
    CALCULATE(
        [Total Sales],
        DATEADD(Dim_Date[date], -1, MONTH)
    )
RETURN
    IF(
        ISBLANK(PreviousMonthSales) || PreviousMonthSales = 0,
        BLANK(),
        DIVIDE(CurrentMonthSales - PreviousMonthSales, PreviousMonthSales)
    )
```

### What I used and what I corrected

My initial version was:

```DAX
Month-over-Month Growth % =
VAR CurrentSales = [Total Sales]
VAR PreviousSales =
    CALCULATE(
        [Total Sales],
        DATEADD(Dim_Date[date], -1, MONTH)
    )
RETURN
    DIVIDE(CurrentSales - PreviousSales, PreviousSales)
```

Copilot's version added an explicit check for a blank or zero previous-month value before performing the division. I reviewed this edge case and used the safer approach because it prevents an invalid percentage calculation when there is no previous-month sales value.

## 2. Running Total Sales

### Copilot suggestion

Copilot suggested:

```DAX
Running Total Sales =
CALCULATE(
    [Total Sales],
    FILTER(
        ALL(Dim_Date[date]),
        Dim_Date[date] <= MAX(Dim_Date[date])
    )
)
```

### What I used and what I corrected

I used the suggested formula because it matched the running-total requirement and the existing BrewMetrics model. I checked that it uses the existing [Total Sales] measure and the Dim_Date[date] column correctly.

The formula removes the current date filter and accumulates sales for all dates up to the current date.

## 3. City Sales Rank

### Copilot suggestion

Copilot suggested:

```DAX
City Sales Rank =
RANKX(
    ALL(Dim_City[city]),
    [Total Sales],
    ,
    DESC,
    Dense
)
```

### What I used and what I corrected

I used the suggested formula because it matched the requirement for a RANKX-based city ranking. I checked that it uses Dim_City[city] and the existing [Total Sales] measure.

The ranking sorts cities from highest sales to lowest sales. The Dense option means that cities with equal sales receive the same rank and the next rank does not skip a number.

## 4. Average Sales per Quantity

### Copilot suggestion

Copilot suggested:

```DAX
Average Sales per Quantity =
DIVIDE(
    [Total Sales],
    [Total Quantity],
    BLANK()
)
```

### What I used and what I corrected

My initial version was:

```DAX
Average Sales per Quantity =
DIVIDE(
    [Total Sales],
    [Total Quantity]
)
```

Copilot explicitly included BLANK() as the third argument of DIVIDE. I reviewed this edge case and kept the safer version because it clearly handles situations where total quantity is zero or blank.

This measure calculates the average sales amount generated per unit of quantity in the current filter context.