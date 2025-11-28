# Story: STM-S2-002 - Manager Code-Based Invite System

## 📝 Properties
```yaml
story-id: STM-S2-002
story-status: Ready
story-priority: High
story-points: 3
epic: User Role Management System
sprint: Sprint 2 - Communication & Roles
assignee: Development Team
labels: [invites, manager, no-email]
```

## 👤 User Story
**As a** team manager
**I want** to invite users via generated codes instead of email
**So that** I can easily share invites through any communication method and don't rely on email delivery

## ✅ Acceptance Criteria
- [ ] Given I am a manager, when I access invite management, then I can generate unique invite codes
- [ ] Given I generate an invite code, when creating it, then I can specify the role (player, parent, etc.)
- [ ] Given an invite code is created, when I view it, then it should have an expiration date
- [ ] Given I have active invites, when I access invite management, then I can view and manage all my invite codes
- [ ] Given an invite code, when configured, then it should be single-use or multi-use based on my selection
- [ ] Given I want to share an invite, when I copy the code, then it should be easily shareable via text/chat

## 📋 Tasks
- [ ] Create invite code generation system
- [ ] Implement invite code management interface
- [ ] Add role specification for invite codes
- [ ] Set up expiration date handling
- [ ] Create single-use vs multi-use configuration
- [ ] Build manager invite dashboard
- [ ] Add invite code validation logic

## 🔍 Definition of Done
- [ ] Managers can generate unique invite codes
- [ ] Role specification works for all available roles
- [ ] Expiration dates are enforced
- [ ] Invite management interface is functional
- [ ] Single/multi-use configuration works
- [ ] Code reviewed and tested

## 📝 Notes
- No email dependency - codes should be shareable via any method
- Consider code format for easy sharing (avoid confusing characters)
- Need to handle expired code cleanup

## 🔗 Related Items
- **Epic:** [[User Role Management System]]
- **Dependencies:** STM-S2-001 (Admin Role Controls)
- **Blocked by:** None
- **Related:** STM-S2-003 (URL Invite Acceptance)

## 🕒 Time Tracking
| Date | Hours | Activity |
|------|-------|----------|
|      |       |          |

**Total Hours:** 

---
*Created: 2025-11-03*
