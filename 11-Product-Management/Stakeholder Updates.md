# 📢 Stakeholder Updates

## 📝 Properties
```yaml
update-date: {{date:YYYY-MM-DD}}
stakeholders: []
update-type: Weekly
```

## 🎯 Executive Summary
*High-level progress and key decisions*

## 📊 Sprint Progress
```dataview
TABLE WITHOUT ID
  file.link as "Sprint",
  sprint-status as "Status",
  completed-points as "Completed",
  planned-points as "Planned",
  round((completed-points / planned-points) * 100, 1) + "%" as "Progress"
FROM "02-Sprints"
WHERE sprint-current = true OR sprint-status = "Completed"
SORT sprint-start DESC
LIMIT 3
```

## 🎉 Key Achievements
- Achievement 1
- Achievement 2
- Achievement 3

## 🚧 Challenges & Risks
| Challenge | Impact | Mitigation | Owner |
|-----------|--------|------------|-------|
|           |        |            |       |

## 📅 Upcoming Milestones
- Milestone 1: [Date]
- Milestone 2: [Date]
- Milestone 3: [Date]

## 💰 Budget & Resource Status
- **Budget Utilization:** X%
- **Resource Allocation:** 
- **Timeline Status:** On track / Behind / Ahead

## 🎯 Next Period Focus
- Priority 1
- Priority 2
- Priority 3

## 📋 Decisions Needed
- [ ] Decision 1 - Due: [Date]
- [ ] Decision 2 - Due: [Date]

## 📞 Stakeholder Feedback
*Key feedback and action items from stakeholders*

---
*Next Update: {{date+7d:YYYY-MM-DD}}*
