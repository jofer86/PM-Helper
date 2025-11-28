# Story: STM-S2.5-003 - Parent-First Underage Player Flow

## 📝 Properties
```yaml
story-id: STM-S2.5-003
story-status: Ready
story-priority: Medium
story-points: 4
epic: User Role Management System
sprint: Sprint 2.5 - Polish & Bug Fix
assignee: Development Team
labels: [parent-child, underage, workflow]
```

## 👤 User Story
**As a** manager or super admin
**I want** to ensure parents register before their underage children
**So that** proper guardian consent and contact information is established

## ✅ Acceptance Criteria
- [ ] Given I want to invite an underage player, when creating the invite, then I should first invite the parent
- [ ] Given I am creating a player invite, when I specify the player is underage, then the system should prompt for parent information
- [ ] Given a parent has registered, when I create an underage player invite, then I can link it to the existing parent account
- [ ] Given an underage player invite is redeemed, when they register, then they should be automatically linked to their parent
- [ ] Given I try to invite an underage player without a parent, when submitting, then I should see a validation error
- [ ] Given a parent account exists, when viewing player invites, then I can see which parent they will be linked to

## 📋 Tasks
- [ ] Add age verification to player invite creation
- [ ] Implement parent-child relationship in data model
- [ ] Create parent selection/linking interface
- [ ] Add validation for underage player invites
- [ ] Implement automatic parent-child linking on registration
- [ ] Create parent information display in invite management
- [ ] Add age calculation and validation logic
- [ ] Update invite creation workflow for underage players

## 🔍 Definition of Done
- [ ] Age verification works correctly
- [ ] Parent-child relationships are properly established
- [ ] Validation prevents orphaned underage player invites
- [ ] Parent linking works automatically
- [ ] Interface clearly shows parent-child connections
- [ ] All age-related business rules enforced
- [ ] Mobile experience is user-friendly

## 📝 Notes
- Consider legal age requirements (typically 18 years)
- May need to store parent consent information
- Should handle cases where parent info changes

## 🔗 Related Items
- **Epic:** [[User Role Management System]]
- **Dependencies:** STM-S2.5-001, STM-S2.5-002
- **Blocked by:** None
- **Related:** Player registration system

## 🕒 Time Tracking
| Date | Hours | Activity |
|------|-------|----------|
|      |       |          |

**Total Hours:** 

---
*Created: 2025-11-09*
