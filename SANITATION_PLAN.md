# 🧹 Brains Folder Sanitation Plan

**Created:** 2025-11-28  
**Objective:** Align brains folder tickets with current Sports-Man app state (V1.2.0)  
**Status:** Ready for Execution

---

## 📊 Current State Analysis

### ✅ Completed & In Production (V1.0.0 - V1.2.0)
Based on release registry and app documentation:

1. **STM-S2-003** - URL Invite Acceptance & Team Registration ✅ V1.0.0
2. **TECH-S2.5-001** - Comprehensive Logging Coverage ✅ V1.1.0
3. **STM-S2.5-001** - Role-Restricted Invite System ✅ V1.1.5
4. **ADMIN-S2.5-001** - Super Admin Dashboard ✅ V1.2.0
5. **STM-S2-001** - Admin Role Internal Access Controls ✅ (Part of V1.2.0)
6. **STM-S2-002** - Manager Code-Based Invite System ✅ (Part of V1.1.5)
7. **BUG-S2-001** - Invite Codes List Not Visible ✅ (Fixed)
8. **BUG-S2-002** - Manager Navigation Policy Block ✅ (Fixed)
9. **Story - Team Manager Registration** ✅ (Sprint 1)
10. **Story - Player Roster Management** ✅ (Sprint 1)
11. **Story - UI Design System & Layout Improvements** ✅ (Sprint 1)

### 🔄 Partially Completed
1. **STM-S4-001** - Playwright Test Framework Setup (RSpec used instead)
2. **STM-S4-002** - User Authentication & Role Testing (RSpec coverage exists)
3. **STM-S4-003** - Team Management Flow Testing (RSpec coverage exists)

### ❌ Not Implemented / Future Features
1. **Story - Basic Messaging System** - Not implemented
2. **Story - Team Announcement System** - Not implemented
3. **ADMIN-S2.5-002** - Team Manager Admin View - Not implemented
4. **ADMIN-S2.5-003** - Player Admin View - Not implemented
5. **ADMIN-S2.5-004** - Parent Admin View - Not implemented
6. **ADMIN-S2.5-005** - Organization Admin Dashboard - Not implemented
7. **STM-S2.5-002** - Locked Signup Process - Not implemented
8. **STM-S2.5-003** - Parent-First Underage Player Flow - Not implemented
9. **TECH-S2.5-002** - Complete i18n Coverage - Partial (needs verification)

---

## 🎯 Sanitation Actions

### Phase 1: Update Completed Tickets ✅

**Action:** Mark all completed stories with proper status and completion dates

#### Stories to Update:
1. **STM-S2-003** - URL Invite Acceptance & Team Registration
   - Status: ✅ COMPLETED
   - Completed: 2025-11-08
   - Release: V1.0.0

2. **STM-S2-001** - Admin Role Internal Access Controls
   - Status: ✅ COMPLETED
   - Completed: 2025-11-22
   - Release: V1.2.0

3. **STM-S2-002** - Manager Code-Based Invite System
   - Status: ✅ COMPLETED
   - Completed: 2025-11-11
   - Release: V1.1.5

4. **BUG-S2-001** - Invite Codes List Not Visible
   - Status: ✅ FIXED
   - Completed: 2025-11-06

5. **BUG-S2-002** - Manager Navigation Policy Block
   - Status: ✅ FIXED
   - Completed: 2025-11-06

6. **Story - Team Manager Registration**
   - Status: ✅ COMPLETED
   - Completed: 2025-11-01
   - Release: V1.0.0

7. **Story - Player Roster Management**
   - Status: ✅ COMPLETED
   - Completed: 2025-11-03
   - Release: V1.0.0

8. **Story - UI Design System & Layout Improvements**
   - Status: ✅ COMPLETED
   - Completed: 2025-11-01
   - Release: V1.0.0

### Phase 2: Update Testing Stories 🔄

**Action:** Clarify testing approach (RSpec vs Playwright)

#### Stories to Update:
1. **STM-S4-001** - Playwright Test Framework Setup
   - Status: ⚠️ SUPERSEDED
   - Note: "RSpec used as primary testing framework instead of Playwright"
   - Action: Archive or update to reflect RSpec implementation

2. **STM-S4-002** - User Authentication & Role Testing
   - Status: ✅ COMPLETED (via RSpec)
   - Note: "Implemented using RSpec instead of Playwright"

3. **STM-S4-003** - Team Management Flow Testing
   - Status: ✅ COMPLETED (via RSpec)
   - Note: "Implemented using RSpec instead of Playwright"

### Phase 3: Clarify Future Features 📋

**Action:** Move unimplemented features to backlog with clear status

#### Stories to Move/Update:
1. **Story - Basic Messaging System**
   - Status: 📋 BACKLOG
   - Priority: Medium
   - Target: Future Sprint

2. **Story - Team Announcement System**
   - Status: 📋 BACKLOG
   - Priority: High
   - Target: Future Sprint

3. **ADMIN-S2.5-002** - Team Manager Admin View
   - Status: 📋 READY FOR DEVELOPMENT
   - Priority: High
   - Target: V1.3.0
   - Note: "Foundation established in V1.2.0"

4. **ADMIN-S2.5-003** - Player Admin View
   - Status: 📋 READY FOR DEVELOPMENT
   - Priority: Medium
   - Target: V1.3.0

5. **ADMIN-S2.5-004** - Parent Admin View
   - Status: 📋 READY FOR DEVELOPMENT
   - Priority: Medium
   - Target: V1.3.0

6. **ADMIN-S2.5-005** - Organization Admin Dashboard
   - Status: 📋 READY FOR DEVELOPMENT
   - Priority: Low
   - Target: V1.4.0

7. **STM-S2.5-002** - Locked Signup Process
   - Status: 📋 BACKLOG
   - Priority: Medium
   - Target: TBD

8. **STM-S2.5-003** - Parent-First Underage Player Flow
   - Status: 📋 BACKLOG
   - Priority: Medium
   - Target: TBD

9. **TECH-S2.5-002** - Complete i18n Coverage
   - Status: 🔍 NEEDS VERIFICATION
   - Action: Verify current i18n coverage in app

### Phase 4: Archive Obsolete Items 🗄️

**Action:** Move completed items to archive folder

#### Create Archive Structure:
```
/Users/jorgerincon/brains/
├── 03-Stories/
│   └── archive/
│       ├── sprint-1-completed/
│       ├── sprint-2-completed/
│       └── sprint-2.5-completed/
```

#### Items to Archive:
- All ✅ COMPLETED stories from Sprint 1, 2, 2.5
- All ✅ FIXED bugs
- Keep only active/backlog items in main 03-Stories folder

### Phase 5: Update Sprint Documentation 📝

**Action:** Ensure sprint docs reflect actual completion status

#### Sprints to Review:
1. **Sprint 1 - Foundation MVP**
   - Verify all stories marked complete
   - Add completion date: 2025-11-01

2. **Sprint 2 - Communication & Roles**
   - Verify completed vs pending items
   - Add completion date: 2025-11-11

3. **Sprint 2.5 - Polish & Bug Fix**
   - Update with actual completed items
   - Add completion date: 2025-11-22

4. **Sprint 3 - Enhanced Management & Payments**
   - Status: NOT STARTED
   - Move to future planning

5. **Sprint 4 - Automation Testing Suite**
   - Status: PARTIALLY COMPLETED (RSpec)
   - Update to reflect RSpec implementation

---

## 🔧 Execution Steps

### Step 1: Backup Current State
```bash
cd /Users/jorgerincon/brains
git add .
git commit -m "Pre-sanitation backup - $(date +%Y-%m-%d)"
git push
```

### Step 2: Create Archive Structure
```bash
mkdir -p 03-Stories/archive/{sprint-1-completed,sprint-2-completed,sprint-2.5-completed}
```

### Step 3: Update Story Statuses
- Update each story file with correct status
- Add completion dates
- Add release version references
- Update acceptance criteria checkboxes

### Step 4: Move Completed Stories to Archive
```bash
# Move Sprint 1 completed stories
mv "03-Stories/Story - Team Manager Registration.md" "03-Stories/archive/sprint-1-completed/"
mv "03-Stories/Story - Player Roster Management.md" "03-Stories/archive/sprint-1-completed/"
mv "03-Stories/Story - UI Design System & Layout Improvements.md" "03-Stories/archive/sprint-1-completed/"

# Move Sprint 2 completed stories
mv "03-Stories/STM-S2-001 - Admin Role Internal Access Controls.md" "03-Stories/archive/sprint-2-completed/"
mv "03-Stories/STM-S2-002 - Manager Code-Based Invite System.md" "03-Stories/archive/sprint-2-completed/"
mv "03-Stories/STM-S2-003 - URL Invite Acceptance & Team Registration.md" "03-Stories/archive/sprint-2-completed/"
mv "03-Stories/BUG-S2-001 - Invite Codes List Not Visible.md" "03-Stories/archive/sprint-2-completed/"
mv "03-Stories/BUG-S2-002 - Manager Navigation Policy Block.md" "03-Stories/archive/sprint-2-completed/"

# Move Sprint 2.5 completed stories
mv "03-Stories/STM-S2.5-001 - Role-Restricted Invite System.md" "03-Stories/archive/sprint-2.5-completed/"
mv "03-Stories/TECH-S2.5-001 - Comprehensive Logging Coverage.md" "03-Stories/archive/sprint-2.5-completed/"
mv "03-Stories/ADMIN-S2.5-001 - Super Admin Dashboard.md" "03-Stories/archive/sprint-2.5-completed/"
```

### Step 5: Update Remaining Stories
- Update future feature stories with BACKLOG status
- Update admin dashboard stories with READY FOR DEVELOPMENT status
- Add target release versions

### Step 6: Update Sprint Documentation
- Mark completed sprints as DONE
- Update sprint summaries with actual deliverables
- Add retrospective notes if missing

### Step 7: Update Dashboard
- Update 00-Dashboard.md with current state
- Reflect V1.2.0 as current release
- Show clear backlog vs completed items

### Step 8: Commit Changes
```bash
git add .
git commit -m "Sanitation complete - Aligned with V1.2.0 production state"
git push
```

---

## 📈 Success Metrics

### Before Sanitation:
- 24 story files in 03-Stories/
- Mixed status (completed, in-progress, future)
- Unclear what's in production vs planned

### After Sanitation:
- ~9 active/backlog stories in 03-Stories/
- ~15 archived completed stories
- Clear separation: Production ✅ | Ready 📋 | Backlog 📋
- All stories have accurate status and dates
- Sprint docs reflect actual completion

---

## 🎯 Next Steps After Sanitation

1. **Plan V1.3.0 Release**
   - Focus: Role-specific admin dashboards
   - Stories: ADMIN-S2.5-002, 003, 004

2. **Backlog Refinement**
   - Prioritize messaging vs admin features
   - Estimate effort for remaining features

3. **Sprint Planning**
   - Create Sprint 5 plan for V1.3.0
   - Assign stories to sprint

4. **Documentation Update**
   - Update Product Roadmap
   - Update Release Registry format

---

**Ready to Execute:** ✅  
**Estimated Time:** 2-3 hours  
**Risk Level:** Low (backup created first)
