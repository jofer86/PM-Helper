# Sprint Planning - Sprint {{sprint-number}}

## 📝 Properties
```yaml
ritual-type: Sprint Planning
ritual-date: {{date:YYYY-MM-DD}}
sprint-number: 
duration: 2 hours
attendees: []
```

## 🎯 Sprint Goal
*What is the overarching objective for this sprint?*

## 📊 Team Capacity
- **Available days:** 
- **Team velocity:** points (based on last 3 sprints)
- **Planned capacity:** points

## 📋 Story Selection Process

### Stories Considered
```dataview
TABLE WITHOUT ID
  file.link as "Story",
  story-points as "Points",
  story-priority as "Priority",
  "✅" as "Selected"
FROM "03-Stories"
WHERE story-status = "Ready"
SORT story-priority ASC
```

### Selected Stories
- [ ] Story 1 - X points
- [ ] Story 2 - X points
- [ ] Story 3 - X points

**Total Committed Points:** 

## 🔍 Story Breakdown
*For each selected story, identify tasks and dependencies*

### Story 1: [Title]
- [ ] Task 1 (X hours)
- [ ] Task 2 (X hours)
- Dependencies: 

### Story 2: [Title]
- [ ] Task 1 (X hours)
- [ ] Task 2 (X hours)
- Dependencies: 

## ⚠️ Risks & Assumptions
- Risk 1: Mitigation plan
- Risk 2: Mitigation plan
- Assumption 1: Validation needed
- Assumption 2: Validation needed

## 📅 Key Dates
- **Sprint Start:** 
- **Sprint Review:** 
- **Sprint Retrospective:** 
- **Next Planning:** 

## ✅ Planning Outcomes
- [ ] Sprint goal defined
- [ ] Stories selected and estimated
- [ ] Tasks identified
- [ ] Capacity confirmed
- [ ] Risks documented
- [ ] Sprint backlog created

---
*Planning completed: `= date(today)`*
