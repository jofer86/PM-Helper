# 📋 Product Backlog

## 🔥 High Priority Stories
```dataview
TABLE WITHOUT ID
  file.link as "Story",
  story-points as "Points",
  epic as "Epic",
  story-status as "Status"
FROM "03-Stories"
WHERE story-priority = "High" AND story-status != "Done"
SORT story-priority ASC
```

## 📊 Medium Priority Stories
```dataview
TABLE WITHOUT ID
  file.link as "Story",
  story-points as "Points",
  epic as "Epic",
  story-status as "Status"
FROM "03-Stories"
WHERE story-priority = "Medium" AND story-status != "Done"
SORT story-priority ASC
```

## 📝 Low Priority Stories
```dataview
TABLE WITHOUT ID
  file.link as "Story",
  story-points as "Points",
  epic as "Epic",
  story-status as "Status"
FROM "03-Stories"
WHERE story-priority = "Low" AND story-status != "Done"
SORT story-priority ASC
```

## 📈 Backlog Health
```dataview
TABLE WITHOUT ID
  story-status as "Status",
  length(rows) as "Count"
FROM "03-Stories"
GROUP BY story-status
```

## 🎯 Next Sprint Candidates
*Stories ready for sprint planning*
```dataview
LIST
FROM "03-Stories"
WHERE story-status = "Ready" AND !sprint
SORT story-priority ASC
LIMIT 10
```

## 📝 Backlog Refinement Notes
### {{date:YYYY-MM-DD}}
- Refined stories:
- Estimated stories:
- New stories added:
- Stories removed:

---
*Last updated: `= date(today)`*
