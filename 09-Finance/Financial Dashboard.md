# 💰 Financial Dashboard

## 📊 Monthly Overview - {{date:MMMM YYYY}}

### Revenue Summary
```dataview
TABLE WITHOUT ID
  client as "Client",
  sum(hours * rate) as "Revenue",
  sum(hours) as "Hours"
FROM "08-Time-Logs"
WHERE date >= date({{date:YYYY-MM-01}}) AND date <= date({{date:YYYY-MM-31}})
GROUP BY client
```

**Total Monthly Revenue:** $
**Total Hours Worked:** 
**Average Hourly Rate:** $

## 🎯 Active Projects Revenue
```dataview
TABLE WITHOUT ID
  file.link as "Project",
  project-value as "Total Value",
  hours-spent * rate as "Earned",
  project-value - (hours-spent * rate) as "Remaining"
FROM "07-Projects"
WHERE project-status = "Active"
```

## 📈 Revenue Trends
| Month | Revenue | Hours | Avg Rate |
|-------|---------|-------|----------|
|       |         |       |          |

## 💳 Invoicing Status
```dataview
TABLE WITHOUT ID
  file.link as "Invoice",
  invoice-amount as "Amount",
  invoice-status as "Status",
  invoice-due as "Due Date"
FROM "09-Finance/Invoices"
WHERE invoice-status != "Paid"
SORT invoice-due ASC
```

## 📋 Outstanding Payments
- **Total Outstanding:** $
- **Overdue Amount:** $
- **Average Payment Time:** X days

## 🎯 Financial Goals
- **Monthly Target:** $
- **Current Progress:** X%
- **Quarterly Goal:** $
- **Annual Goal:** $

## 📊 Client Revenue Distribution
```dataview
TABLE WITHOUT ID
  client as "Client",
  round(sum(revenue) / total(sum(revenue)) * 100, 1) + "%" as "% of Revenue"
FROM "08-Time-Logs"
WHERE date >= date({{date:YYYY-01-01}})
GROUP BY client
SORT sum(revenue) DESC
```

## 💡 Financial Insights
- **Top Client:** 
- **Most Profitable Project:** 
- **Highest Rate:** $
- **Growth Rate:** X% MoM

---
*Updated: `= date(today)`*
