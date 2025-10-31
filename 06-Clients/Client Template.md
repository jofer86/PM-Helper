# Client: {{title}}

## 📝 Properties
```yaml
client-status: Active
client-type: Corporate
contact-person: 
email: 
phone: 
rate: 
payment-terms: 
projects: []
```

## 📞 Contact Information
- **Primary Contact:** 
- **Email:** 
- **Phone:** 
- **Address:** 
- **Time Zone:** 

## 💼 Business Details
- **Industry:** 
- **Company Size:** 
- **Decision Makers:** 
- **Budget Range:** 
- **Preferred Communication:** 

## 💰 Financial Information
- **Hourly Rate:** $
- **Project Rate:** $
- **Payment Terms:** 
- **Invoice Frequency:** 
- **Payment Method:** 

## 📊 Project History
```dataview
TABLE WITHOUT ID
  file.link as "Project",
  project-status as "Status",
  project-value as "Value",
  project-start as "Start",
  project-end as "End"
FROM "07-Projects"
WHERE client = this.file.name
SORT project-start DESC
```

## 📝 Communication Log
| Date | Type | Summary | Follow-up |
|------|------|---------|-----------|
|      |      |         |           |

## 🎯 Relationship Notes
- **Strengths:** 
- **Challenges:** 
- **Opportunities:** 
- **Preferences:** 

## 📋 Action Items
- [ ] 
- [ ] 
- [ ] 

---
*Last updated: `= date(today)`*
