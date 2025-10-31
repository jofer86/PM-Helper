# 🎯 Job Management Dashboard

## 🚀 Active Sprints
```dataview
TABLE WITHOUT ID
  file.link as "Sprint",
  sprint-status as "Status",
  sprint-start as "Start",
  sprint-end as "End",
  length(stories) as "Stories"
FROM "02-Sprints"
WHERE sprint-status = "Active"
SORT sprint-start DESC
```

## 📋 Current Sprint Board
```dataview
TASK
FROM "02-Sprints" OR "03-Stories"
WHERE sprint-current = true
GROUP BY status
```

## 🎭 Epics Overview
```dataview
TABLE WITHOUT ID
  file.link as "Epic",
  epic-status as "Status",
  epic-priority as "Priority",
  length(stories) as "Stories",
  epic-value as "Business Value"
FROM "01-Epics"
WHERE epic-status != "Done"
SORT epic-priority ASC, epic-value DESC
```

## 📊 Velocity & Metrics
```dataview
TABLE WITHOUT ID
  file.link as "Sprint",
  planned-points as "Planned",
  completed-points as "Completed",
  round((completed-points / planned-points) * 100, 1) + "%" as "Completion"
FROM "02-Sprints"
WHERE sprint-status = "Completed"
SORT sprint-start DESC
LIMIT 5
```

## 🎯 Product Management
- **[[11-Product-Management/Product Roadmap|Product Roadmap]]** - Strategic direction
- **[[11-Product-Management/Risk Register|Risk Register]]** - Risk monitoring
- **[[11-Product-Management/Decision Log|Decision Log]]** - Key decisions
- **[[11-Product-Management/Stakeholder Updates|Stakeholder Updates]]** - Communication

## 🔥 Today's Focus
- [ ] Daily Standup
- [ ] Review blocked items
- [ ] Update story progress
- [ ] Check high-priority risks

## 📅 Upcoming Rituals
```dataview
LIST
FROM "05-Rituals"
WHERE ritual-date >= date(today)
SORT ritual-date ASC
LIMIT 3
```

## ⚠️ High Priority Risks
```dataview
TABLE WITHOUT ID
  risk as "Risk",
  impact as "Impact",
  mitigation as "Mitigation"
FROM "11-Product-Management/Risk Register"
WHERE priority = "High"
LIMIT 3
```

---
*Last updated: `= date(today)`*
*System maintained by: Q (Product Manager)*
