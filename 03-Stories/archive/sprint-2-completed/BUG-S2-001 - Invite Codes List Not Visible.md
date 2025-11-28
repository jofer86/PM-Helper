# Bug: BUG-S2-001 - Invite Codes List Not Visible

## 📝 Properties
```yaml
story-id: BUG-S2-001
story-status: Open
story-priority: High
story-points: 1
epic: Manager Code-Based Invite System
sprint: Sprint 2 - Communication & Roles
assignee: Development Team
labels: [bug, ui, invite-codes, manager-interface]
```

## 🐛 Bug Description
**Issue**: Manager cannot see the list of invitation codes they have created
**Impact**: Managers cannot view, manage, or copy URLs for existing invitation codes
**Severity**: High (blocks core functionality)

## 🔍 Expected Behavior
- Manager should see a list of all invitation codes they have created
- Each code should display with a copyable URL
- List should show code status, expiration, and usage statistics

## 🚫 Actual Behavior
- Invite codes list is not visible to managers
- Cannot access existing codes for sharing or management
- URL copying functionality not accessible

## 📋 Steps to Reproduce
1. Login as a manager
2. Navigate to team management
3. Go to invitation codes section
4. Observe that list is not visible/accessible

## 🔧 Potential Root Causes
- View rendering issue in index template
- Route configuration problem
- Authorization policy blocking access
- JavaScript/CSS hiding elements

## ✅ Acceptance Criteria for Fix
- [ ] Manager can see complete list of their invitation codes
- [ ] Each code displays with copyable URL
- [ ] List shows proper status indicators
- [ ] Copy functionality works for URLs
- [ ] Mobile responsive display

## 🔗 Related Items
- **Parent Story:** STM-S2-002 (Manager Code-Based Invite System)
- **Affects:** Task 3.2 (Manager invite codes index view)

---
*Created: 2025-11-05*
*Reported by: QA Testing*
