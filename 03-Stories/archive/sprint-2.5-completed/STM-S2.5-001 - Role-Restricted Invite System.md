# Story: STM-S2.5-001 - Role-Restricted Invite System

## 📝 Properties
```yaml
story-id: STM-S2.5-001
story-status: ✅ COMPLETED
story-priority: High
story-points: 5
epic: User Role Management System
sprint: Sprint 2.5 - Polish & Bug Fix
assignee: Development Team
completed-date: 2025-11-11
labels: [invites, role-restrictions, security, kiro-implemented]
kiro-spec: role-restricted-invites (26 tasks completed)
```

## 👤 User Story
**As a** system administrator
**I want** to restrict invitation capabilities based on user roles
**So that** managers can only invite players and parents, while super admins can invite any role including managers

## ✅ Acceptance Criteria
- [ ] Given I am a manager, when I create an invite, then I can only select "player" or "parent" roles
- [ ] Given I am a super admin, when I create an invite, then I can select any role (manager, player, parent)
- [ ] Given I am a super admin inviting a player, when creating the invite, then I can assign a specific team
- [ ] Given I am inviting an underage player, when creating the invite, then the system should require parent registration first
- [ ] Given an invite is created, when the user redeems it, then they are automatically assigned the pre-selected role
- [ ] Given a user accesses signup without a valid invite, when they try to register, then they should be blocked
- [ ] Given a manager tries to invite a manager role, when submitting the form, then they should see an error message

## 📋 Tasks
- [ ] Update invite creation form with role restrictions
- [ ] Add role validation based on current user permissions
- [ ] Implement team assignment for player invites
- [ ] Add parent-first requirement for underage players
- [ ] Block direct signup access without valid invites
- [ ] Update invite model with role and team assignment
- [ ] Create role-based invite validation logic
- [ ] Add error handling for unauthorized role invitations

## 🔍 Definition of Done
- [ ] Role restrictions properly enforced in invite creation
- [ ] Team assignment works for player invites
- [ ] Parent-first flow implemented for underage players
- [ ] Signup blocked without valid invites
- [ ] All role validation tests pass
- [ ] Error messages are user-friendly
- [ ] Code reviewed and tested

## 📝 Notes
- Super admins can only be created via console (no invite system)
- Managers cannot invite other managers
- Player invites should include team assignment capability
- Consider age verification for parent requirement

## 🔗 Related Items
- **Epic:** [[User Role Management System]]
- **Dependencies:** STM-S2-002, STM-S2-003
- **Blocked by:** None
- **Related:** STM-S2.5-002 (Locked Signup Process)

## 🕒 Time Tracking
| Date | Hours | Activity |
|------|-------|----------|
|      |       |          |

**Total Hours:** 

---
*Created: 2025-11-09*
