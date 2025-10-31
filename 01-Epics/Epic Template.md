# Epic: {{title}}

## 📝 Properties
```yaml
epic-id: EP-{{date:YYYY-MM-DD}}-001
epic-status: Backlog
epic-priority: Medium
epic-value: High
epic-owner: 
epic-start: 
epic-end: 
stories: []
```

## 🎯 Epic Goal
*What business value does this epic deliver?*

## 📋 Acceptance Criteria
- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## 📊 Success Metrics
- Metric 1: Target value
- Metric 2: Target value

## 🔗 Related Stories
```dataview
LIST
FROM "03-Stories"
WHERE contains(epic, this.file.name)
```

## 📝 Notes
*Additional context, assumptions, constraints*

## 🔄 Status Updates
| Date | Status | Notes |
|------|--------|-------|
|      |        |       |

---
*Created: `= date(today)`*
