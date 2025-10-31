# Sprint {{sprint-number}}: {{title}}

## 📝 Properties
```yaml
sprint-number: 
sprint-status: Planning
sprint-start: 
sprint-end: 
sprint-current: false
planned-points: 0
completed-points: 0
stories: []
```

## 🎯 Sprint Goal
*What will we accomplish this sprint?*

## 📋 Sprint Backlog
```dataview
TASK
FROM "03-Stories"
WHERE contains(sprint, this.file.name)
GROUP BY status
```

## 📊 Burndown
| Day | Remaining Points | Notes |
|-----|------------------|-------|
|     |                  |       |

## 🔄 Daily Updates
### Day 1 - {{date:YYYY-MM-DD}}
**Yesterday:** Sprint started
**Today:** 
**Blockers:** 

### Day 2 - 
**Yesterday:** 
**Today:** 
**Blockers:** 

## 📈 Sprint Metrics
- **Velocity:** {{completed-points}} points
- **Completion Rate:** {{completion-rate}}%
- **Stories Completed:** 
- **Stories Carried Over:** 

## 🎉 Sprint Review
*What was delivered?*

## 🔍 Sprint Retrospective
**What went well:**
- 

**What could improve:**
- 

**Action items:**
- [ ] 

---
*Created: `= date(today)`*
