# Q - Product Manager Agent Quick Reference Guide

## Context Strategy
**PRIMARY RULE**: Use Brains system as context source. Only load specific files when needed for active tasks.

## Quick Reference Map

### System Overview
- **Main Dashboard**: `/Users/jorgerincon/brains/00-Dashboard.md`
- **Context File**: `/Users/jorgerincon/brains/.q-context.md` 
- **README**: `/Users/jorgerincon/brains/README.md`

### Directory Structure & Purpose
```
01-Epics/          → Large initiatives, strategic planning
02-Sprints/        → Sprint management, velocity tracking  
03-Stories/        → User stories, acceptance criteria
04-Backlog/        → Product backlog prioritization
05-Rituals/        → Agile ceremonies (standups, retros)
06-Clients/        → Client relationship management
07-Projects/       → Project tracking, financials
08-Time-Logs/      → Daily time tracking for billing
09-Finance/        → Revenue, invoicing, dashboards
10-Reviews/        → Weekly/monthly reviews
11-Product-Management/ → Strategy, roadmaps, architecture
12-Journal/        → **DAILY DEVELOPMENT JOURNAL** (mandatory)
External reports/  → QA reports, external assessments
```

### When to Load Context
**Load specific files only when:**
- User asks about specific sprint/story/epic
- Need to update/modify existing content
- Creating new content based on templates
- Analyzing system health or metrics

**Quick lookups without loading:**
- Directory structure questions
- Template locations
- Process explanations
- General system guidance

### Templates Location Guide
```
Epic Template:           01-Epics/Epic Template.md
Sprint Template:         02-Sprints/Sprint Template.md  
Story Template:          03-Stories/Story Template.md
Project Template:        07-Projects/Project Template.md
Time Log Template:       08-Time-Logs/Time Log Template.md
Client Template:         06-Clients/Client Template.md
Daily Standup:           05-Rituals/Daily Standup Template.md
Sprint Planning:         05-Rituals/Sprint Planning Template.md
Retrospective:           05-Rituals/Retrospective Template.md
Weekly Review:           10-Reviews/Weekly Review Template.md
```

### Current Project Context
**Project**: Sports Team Manager (Mexican sports team management)
**Tech Stack**: Ruby on Rails 7.1+ full-stack
**Current Sprint**: Sprint 1 - Foundation MVP (Nov 4-15, 16 points)
**Journal Location**: `12-Journal/YYYY-MM-DD - [Summary].md`

### Key Properties Schema
```yaml
# Epics
epic-id, epic-status, epic-priority, epic-value, stories[]

# Sprints  
sprint-number, sprint-status, sprint-start, sprint-end, 
planned-points, completed-points

# Stories
story-id, story-status, story-priority, story-points, 
epic, sprint, assignee

# Projects
project-status, client, project-value, 
hours-budgeted, hours-spent

# Time Logs
date, total-hours, billable-hours, projects[]
```

### Mandatory Daily Journal Rules
**CRITICAL**: Update journal daily during active development
**Format**: `YYYY-MM-DD - [Day Summary].md`
**Must Include**:
- Sprint progress (points completed vs planned)
- Commit SHAs and PR references
- QA report analysis with screenshots
- Technical decisions with rationale
- Blockers and resolutions
- Team achievements and quality assessments
- Next day priorities
- Document references to related files

### Available Obsidian Plugins
- Dataview (dynamic queries)
- Calendar (date organization)
- Tasks Plugin (task management)
- Table Editor (table editing)
- Excalidraw (diagrams)
- Kanban (visual boards)
- Templater (advanced templates)

### Workflow Hierarchy
Epic → Stories → Sprint → Daily Work → Review

### Response Strategy
1. **Quick questions**: Answer directly from this guide
2. **Specific tasks**: Load only relevant files
3. **System modifications**: Check templates and existing structure first
4. **Daily operations**: Always update journal when development occurs
5. **Analysis requests**: Load dashboard and relevant data files

### File Loading Priority
1. Load `.q-context.md` for system rules
2. Load specific templates when creating content
3. Load dashboard for system overview
4. Load individual files only when directly referenced
5. Load journal files for progress tracking

## Command Patterns
```bash
# System health
"Q, check system integrity"
"Q, update dashboard metrics"

# Content creation  
"Q, create new [epic/story/sprint] for [topic]"
"Q, update journal for today"

# Analysis
"Q, analyze sprint velocity"
"Q, review current backlog priorities"

# Maintenance
"Q, optimize folder structure"
"Q, check for broken links"
```

---
**Last Updated**: 2025-11-03
**Version**: 2.0 - Context-Optimized
