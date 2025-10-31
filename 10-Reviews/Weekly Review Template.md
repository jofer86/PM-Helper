# Weekly Review - Week of {{date:YYYY-MM-DD}}

## 📝 Properties
```yaml
week-start: {{date:YYYY-MM-DD}}
week-end: {{date+6d:YYYY-MM-DD}}
total-hours: 0
revenue: 0
completed-stories: 0
```

## 🎯 Week Objectives Review
**Planned Objectives:**
- [ ] Objective 1
- [ ] Objective 2
- [ ] Objective 3

**Achievement Rate:** X/Y (X%)

## 📊 Sprint Progress
```dataview
TABLE WITHOUT ID
  file.link as "Sprint",
  completed-points as "Points Completed",
  planned-points as "Points Planned",
  round((completed-points / planned-points) * 100, 1) + "%" as "Progress"
FROM "02-Sprints"
WHERE sprint-current = true
```

## ✅ Completed Stories
```dataview
LIST
FROM "03-Stories"
WHERE story-status = "Done" AND completion-date >= date({{date:YYYY-MM-DD}}) AND completion-date <= date({{date+6d:YYYY-MM-DD}})
```

## ⏱️ Time & Revenue Summary
- **Total Hours Worked:** 
- **Billable Hours:** 
- **Revenue Generated:** $
- **Average Hourly Rate:** $

## 👥 Client Interactions
| Client | Type | Outcome | Follow-up |
|--------|------|---------|-----------|
|        |      |         |           |

## 🎉 Wins & Achievements
- 
- 
- 

## 🚧 Challenges & Blockers
- 
- 
- 

## 📚 Learnings
- 
- 
- 

## 🎯 Next Week's Focus
- [ ] Priority 1
- [ ] Priority 2
- [ ] Priority 3

## 📋 Action Items
- [ ] Action 1 - Due: [Date]
- [ ] Action 2 - Due: [Date]
- [ ] Action 3 - Due: [Date]

## 📊 Health Check
- **Energy Level:** X/10
- **Work-Life Balance:** X/10
- **Client Satisfaction:** X/10
- **Progress Satisfaction:** X/10

---
*Reviewed: `= date(today)`*
