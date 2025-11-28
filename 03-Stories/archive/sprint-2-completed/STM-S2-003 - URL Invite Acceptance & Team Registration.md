# Story: STM-S2-003 - URL Invite Acceptance & Team Registration

## 📝 Properties
```yaml
story-id: STM-S2-003
story-status: ✅ COMPLETED
story-priority: High
story-points: 3
epic: User Role Management System
sprint: Sprint 2 - Communication & Roles
assignee: Development Team
completed-date: 2025-11-08
labels: [url-invites, registration, team-assignment, kiro-implemented]
kiro-spec: url-invite-acceptance (12 tasks completed)
```

## 👤 User Story
**As a** person receiving an invite code
**I want** to use a URL to register for a specific team
**So that** I can easily join the team and select my appropriate role during signup

## ✅ Acceptance Criteria
- [ ] Given I have an invite code, when I visit `/invite/{code}`, then I should be redirected to the signup page
- [ ] Given I access the signup via invite URL, when I register, then I should be automatically assigned to the specific team
- [ ] Given I'm on the invite signup page, when I see role options, then I should see only roles the manager can invite (player, parent, etc.)
- [ ] Given I complete registration via invite, when successful, then the invite code should be consumed (if single-use)
- [ ] Given I use an invalid/expired code, when I access the URL, then I should see an appropriate error message
- [ ] Given I'm already registered, when I use an invite URL, then I should be redirected appropriately

## 📋 Tasks
- [ ] Create `/invite/{code}` route handler
- [ ] Build team-specific registration flow
- [ ] Implement role selection during signup
- [ ] Add automatic team assignment logic
- [ ] Handle invite code consumption
- [ ] Create error handling for invalid/expired codes
- [ ] Add redirect logic for existing users
- [ ] Test end-to-end invite flow

## 🔍 Definition of Done
- [ ] URL invite acceptance works correctly
- [ ] Team assignment happens automatically
- [ ] Role selection is properly restricted
- [ ] Invite code consumption works
- [ ] Error handling covers all edge cases
- [ ] Mobile-friendly registration flow
- [ ] Integration tests pass

## 📝 Notes
- URL should work on mobile devices for easy sharing
- Consider what happens if user is already logged in
- Need to handle team capacity limits if applicable

## 🔗 Related Items
- **Epic:** [[User Role Management System]]
- **Dependencies:** STM-S2-002 (Manager Code-Based Invite System)
- **Blocked by:** STM-S2-001, STM-S2-002
- **Related:** User registration system

## 🕒 Time Tracking
| Date | Hours | Activity |
|------|-------|----------|
|      |       |          |

**Total Hours:** 

---
*Created: 2025-11-03*
