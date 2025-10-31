# Project: {{title}}

## 📝 Properties
```yaml
project-status: Planning
project-type: Development
client: 
project-value: 
project-start: 
project-end: 
project-manager: 
epics: []
hours-budgeted: 
hours-spent: 0
```

## 🎯 Project Overview
**Objective:** 
**Scope:** 
**Success Criteria:** 

## 👥 Stakeholders
- **Client:** [[]]
- **Project Manager:** 
- **Team Members:** 
- **Key Contacts:** 

## 💰 Financial Details
- **Total Value:** $
- **Payment Schedule:** 
- **Budget Breakdown:**
  - Development: $
  - Design: $
  - Testing: $
  - Other: $

## 📅 Timeline
- **Start Date:** 
- **End Date:** 
- **Key Milestones:**
  - Milestone 1: [Date]
  - Milestone 2: [Date]
  - Milestone 3: [Date]

## 🎭 Related Epics
```dataview
LIST
FROM "01-Epics"
WHERE contains(project, this.file.name)
```

## ⏱️ Time Tracking
```dataview
TABLE WITHOUT ID
  date as "Date",
  hours as "Hours",
  activity as "Activity",
  rate as "Rate",
  (hours * rate) as "Value"
FROM "08-Time-Logs"
WHERE project = this.file.name
```

**Total Hours:** `= sum(this.hours-spent)`
**Remaining Budget:** `= this.hours-budgeted - this.hours-spent` hours

## 📊 Project Health
- **Status:** {{project-status}}
- **Budget Utilization:** X%
- **Timeline:** On track / Behind / Ahead
- **Scope Changes:** X
- **Risk Level:** Low / Medium / High

## 🚧 Risks & Issues
| Risk/Issue | Impact | Probability | Mitigation | Owner |
|------------|--------|-------------|------------|-------|
|            |        |             |            |       |

## 📝 Project Notes
*Key decisions, changes, learnings*

## 📋 Deliverables
- [ ] Deliverable 1
- [ ] Deliverable 2
- [ ] Deliverable 3

---
*Created: `= date(today)`*
