# Sprint 2: Communication & Roles

## 🎯 Sprint Overview
**Sprint Goal**: Implement user role system and enhanced communication features to complete core team management functionality

**Duration**: 2 weeks (Nov 4 - Nov 15, 2025)  
**Sprint Points**: 16 points  
**Team Capacity**: 80 hours (2 developers × 20 hours/week × 2 weeks)  
**Status**: 🚀 **ACTIVE** (Started Nov 3, 2025)

## 📋 Detailed Story Requirements

### STM-S2-001: Admin Role Internal Access Controls (2 points)
**Acceptance Criteria:**
- [x] Admin role is restricted to internal use only
- [x] Admin cannot be assigned to external users
- [x] Document additional permissions needed beyond basic CRUD
- [x] Admin role has system-wide access controls
- [x] Audit trail for admin actions

### STM-S2-002: Manager Code-Based Invite System (3 points)
**Acceptance Criteria:**
- [x] Manager can generate unique invite codes (no email required)
- [x] Invite codes have expiration dates
- [x] Manager can specify role for each invite code
- [x] Manager can view and manage active invite codes
- [x] Invite codes are single-use or multi-use (configurable)

### STM-S2-003: URL Invite Acceptance & Team Registration (3 points)
**Acceptance Criteria:**
- [x] URL format: `/invite/{code}` redirects to signup ✅ 2025-11-20
- [x] URL automatically assigns user to specific team ✅ 2025-11-20
- [x] Signup page shows available roles (player, parent, etc.) ✅ 2025-11-20
- [x] User selects role during registration process ✅ 2025-11-20
- [x] Successful signup consumes invite code ✅ 2025-11-20
- [x] Invalid/expired codes show appropriate error messages ✅ 2025-11-20

## 📋 Sprint Backlog

### Committed Stories
| Story ID | Title | Points | Priority | Assignee | Status |
|----------|-------|--------|----------|----------|--------|
| STM-S2-001 | Admin Role Internal Access Controls | 2 | High | Development Team | ✅ **COMPLETED** |
| STM-S2-002 | Manager Code-Based Invite System | 3 | High | Development Team | 🚧 **95% COMPLETE** |
| BUG-S2-001 | Invite Codes List Not Visible | 1 | High | Development Team | 🐛 **BUG FIX NEEDED** |
| BUG-S2-002 | Manager Navigation Policy Block | 1 | High | Development Team | 🐛 **BUG FIX NEEDED** |
| STM-S2-003 | URL Invite Acceptance & Team Registration | 3 | High | Development Team | 🚧 **IN PROGRESS** |
| STM-003-02 | Basic Messaging System | 5 | High | Development Team | 📋 **READY** |
| STM-002-01 | Practice Schedule Creation | 3 | Medium | Development Team | 📋 **READY** |

**Total Committed Points**: 16 (2 completed, 14 remaining)

### Moved to Backlog (Scope Adjustment)
| Story ID | Title | Points | Notes |
|----------|-------|--------|-------|
| STM-002-02 | Game Schedule Management | 3 | Moved to Sprint 3 due to role system complexity |

### Dependencies from Sprint 1
- [x] Team registration system completed
- [x] Player roster management functional  
- [x] Basic announcement system working
- [x] User authentication established

**Sprint 1 Status**: ✅ **COMPLETED** (All 16 points delivered)

## 🎯 Sprint Goals & Success Criteria

### Primary Goals
1. **Role Management**: Complete user role and permission system
2. **Direct Communication**: Enable manager-parent messaging
3. **Schedule Foundation**: Basic practice and game scheduling

### Success Criteria
- [ ] Managers can assign roles and invite parents/players
- [ ] Parents can message managers directly
- [ ] Managers can create practice schedules
- [ ] Game scheduling system functional
- [ ] All role permissions properly enforced
- [ ] Mobile messaging experience optimized

## 📅 Sprint Schedule

### Week 1 (Nov 4-8)
**Monday**: STM-S2-001 (Admin Role Controls)
- Define admin-only permissions and access controls
- Identify additional permission requirements
- Internal role validation system

**Tuesday-Wednesday**: STM-S2-002 (Manager Invite System)
- Code-based invitation generation (no email)
- Invite code management interface
- Code validation and expiration logic

**Thursday-Friday**: STM-S2-003 (URL Invite Flow) - Part 1
- URL invite acceptance handler
- Team-specific registration routing
- Multi-role signup page foundation

### Week 2 (Nov 11-15)
**Monday**: STM-S2-003 (URL Invite Flow) - Part 2
- Complete multi-role registration flow
- Team assignment upon signup
- Invite code consumption logic

**Tuesday-Wednesday**: STM-003-02 (Messaging System)
- Basic messaging infrastructure
- Real-time messaging setup
- Mobile messaging optimization

**Thursday**: STM-002-01 (Practice Scheduling)
- Practice schedule creation
- Basic calendar integration

**Friday**: Integration testing, bug fixes, sprint review prep

## 🔧 Technical Deliverables

### Role & Permission System
- [ ] Admin role internal-only access controls
- [ ] Permission requirements analysis and mapping
- [ ] Manager code-based invitation system (no email)
- [ ] URL invite acceptance and validation
- [ ] Team-specific registration flow
- [ ] Multi-role signup process (player, parent, etc.)
- [ ] Invite code generation and management
- [ ] Permission enforcement across all endpoints
- [ ] Audit logging for role changes

### Messaging System
- [ ] Real-time messaging (WebSocket/Server-Sent Events)
- [ ] Message storage and retrieval
- [ ] Notification system integration
- [ ] Mobile-optimized messaging interface
- [ ] Message search functionality

### Scheduling Foundation
- [ ] Practice schedule CRUD operations
- [ ] Game schedule management
- [ ] Basic calendar view
- [ ] Schedule notifications
- [ ] Mobile schedule display

## 🚧 Risks & Mitigation

### Technical Risks
- **Risk**: Real-time messaging complexity
  - **Mitigation**: Start with polling, upgrade to WebSocket if needed
- **Risk**: Permission system bugs
  - **Mitigation**: Comprehensive testing matrix, security review
- **Risk**: Mobile messaging UX challenges
  - **Mitigation**: Progressive enhancement, mobile-first design

### Integration Risks
- **Risk**: Role system conflicts with existing features
  - **Mitigation**: Thorough integration testing, rollback plan
- **Risk**: Notification system overload
  - **Mitigation**: Rate limiting, user preference controls

## 📊 Definition of Done (Sprint Level)

### Functionality
- [ ] All user stories meet acceptance criteria
- [ ] Role permissions enforced throughout system
- [ ] Messaging works in real-time
- [ ] Schedules display correctly on all devices
- [ ] All features tested with multiple user roles

### Quality
- [ ] Unit test coverage >90%
- [ ] Security testing completed
- [ ] Performance testing passed
- [ ] Mobile UX validated
- [ ] Spanish translations complete

## 🧪 Testing Strategy

### Role System Testing
- [ ] Admin role access restrictions
- [ ] Invite code generation and validation
- [ ] URL invite flow end-to-end
- [ ] Multi-role registration scenarios
- [ ] Team assignment accuracy
- [ ] Invite code expiration handling
- [ ] Permission matrix validation
- [ ] Cross-role access attempts

### Messaging Testing
- [ ] Real-time message delivery
- [ ] Notification reliability
- [ ] Mobile messaging experience
- [ ] Message history accuracy
- [ ] Search functionality

### Schedule Testing
- [ ] Schedule creation and editing
- [ ] Calendar display accuracy
- [ ] Notification timing
- [ ] Mobile schedule interaction

## 📈 Success Metrics

### Feature Adoption
- **Role Assignment**: >90% of managers invite at least one parent
- **Messaging Usage**: >70% of teams exchange messages
- **Schedule Creation**: >80% of teams create practice schedules
- **Mobile Engagement**: >65% of messaging on mobile devices

### Technical Performance
- **Message Delivery**: <2 second delivery time
- **Permission Checks**: <100ms response time
- **Schedule Loading**: <1.5 seconds for monthly view
- **System Uptime**: >99.5% during sprint

## 🎪 Sprint Ceremonies

### Daily Standups
**Time**: 9:00 AM daily  
**Focus**: Progress on messaging system, role implementation blockers

### Mid-Sprint Check-in
**Date**: November 8, 2:00 PM  
**Purpose**: Review messaging system progress, adjust scope if needed

### Sprint Review
**Date**: November 15, 2:00 PM  
**Demo Focus**: Role management, messaging, and scheduling features

### Sprint Retrospective
**Date**: November 15, 3:00 PM  
**Focus**: Communication system learnings, technical debt assessment

---
**Created**: 2025-10-30  
**Sprint Master**: TBD  
**Product Owner**: TBD  
**Development Team**: TBD

## Related Documents
- [[Sprint 1 - Foundation MVP]]
- [[Epic - Communication Foundation]]
- [[Sprint 3 - Beta Preparation]] (Next Sprint)
