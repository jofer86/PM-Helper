# Feature Story: STM-S5-001 - Team Activity Calendar

## 📝 Properties
```yaml
story-id: STM-S5-001
story-status: 📋 BACKLOG
story-priority: High
story-points: 5
epic: Team Management System
sprint: Unassigned (Target: V1.4.0)
assignee: Unassigned
labels: [feature, calendar, scheduling, team-management, high-priority]
```

## 🎯 Feature Description

Implement a comprehensive team activity calendar system that allows managers and super admins to schedule trainings, games, and other team events. All team members (players and parents) automatically see scheduled events in a visual monthly calendar view.

## 👤 User Stories

### As a Team Manager
**I want to** schedule team activities (trainings, games, events)  
**So that** all team members know when and where activities are happening

### As a Player/Parent
**I want to** see all scheduled team activities in a calendar view  
**So that** I can plan my schedule and never miss team events

### As a Super Admin
**I want to** schedule activities for any team  
**So that** I can help manage team schedules across the platform

## 🎨 Feature Requirements

### Event Management (Manager/Super Admin Only)

#### Event Creation
- **Access**: From team view, "Calendar" or "Schedule" button
- **Event Types**: Training, Game, Meeting, Social Event, Other
- **Required Fields**:
  - Event title
  - Event type
  - Date and time (start/end)
  - Location (address or venue name)
  - Team (auto-selected from context)
- **Optional Fields**:
  - Description/notes
  - Opponent team (for games)
  - Required equipment
  - RSVP required (yes/no)
  - Reminder settings

#### Event Management
- **Edit Events**: Modify event details
- **Delete Events**: Remove events with confirmation
- **Duplicate Events**: Copy event for recurring activities
- **Bulk Operations**: Create multiple events at once

#### Event Notifications
- **Auto-notify**: All team members when event is created
- **Reminder**: Configurable reminders (24h, 1h before)
- **Changes**: Notify when event is modified or cancelled

---

### Calendar View (All Roles)

#### Monthly Calendar Display
- **Large Calendar**: Full month view with clear date grid
- **Event Indicators**: Visual markers for events on each date
- **Event Types**: Different colors/icons for event types
  - 🏃 Training: Blue
  - ⚽ Game: Green
  - 📋 Meeting: Yellow
  - 🎉 Social: Purple
  - 📌 Other: Gray

#### Calendar Features
- **Navigation**: Previous/Next month buttons
- **Today Button**: Jump to current date
- **Event Count**: Show number of events per day
- **Click to View**: Click date to see event details
- **Mobile Responsive**: Touch-friendly on mobile devices

#### Event Details View
- **Event Card**: Click event to see full details
- **Information Displayed**:
  - Event title and type
  - Date and time
  - Location with map link
  - Description
  - Attendee list (if RSVP enabled)
  - Manager contact info

#### List View (Alternative)
- **Upcoming Events**: List of next events
- **Past Events**: History of completed events
- **Filter by Type**: Show only specific event types
- **Search**: Find events by title or date

---

### Automatic Team Member Association

#### Event-Team Relationship
- **Team Binding**: Event is tied to specific team
- **Auto-visibility**: All team members see event automatically
- **Role-based Actions**:
  - Manager/Super Admin: Create, edit, delete
  - Players/Parents: View only, RSVP (if enabled)

#### Member Notifications
- **New Event**: Email/in-app notification to all team members
- **Event Changes**: Notify when event is modified
- **Reminders**: Automatic reminders before event
- **Cancellation**: Immediate notification if event cancelled

---

## 📋 Acceptance Criteria

### Event Creation (Manager/Super Admin)
- [ ] "Calendar" button visible in team view
- [ ] Event creation form with all required fields
- [ ] Event type selection (Training, Game, Meeting, etc.)
- [ ] Date/time picker for start and end times
- [ ] Location field with address input
- [ ] Event is automatically tied to current team
- [ ] All team members are automatically associated with event
- [ ] Success message confirms event creation
- [ ] Notifications sent to all team members

### Calendar Display (All Roles)
- [ ] Monthly calendar view shows current month
- [ ] Events displayed on correct dates
- [ ] Different colors/icons for event types
- [ ] Event count indicator on dates with multiple events
- [ ] Previous/Next month navigation works
- [ ] "Today" button jumps to current date
- [ ] Mobile-responsive design
- [ ] Touch-friendly on mobile devices

### Event Details
- [ ] Click on event opens detail view
- [ ] All event information displayed clearly
- [ ] Location shows with map link (Google Maps)
- [ ] Manager contact info visible
- [ ] Edit/Delete buttons for managers only
- [ ] RSVP button if enabled
- [ ] Close/back button to return to calendar

### Permissions
- [ ] Only managers and super admins can create events
- [ ] Only managers and super admins can edit/delete events
- [ ] Players and parents can view events only
- [ ] Proper authorization checks on all actions
- [ ] Audit logging for event creation/modification

### Notifications
- [ ] Email notification sent when event is created
- [ ] In-app notification for new events
- [ ] Reminder notifications before event
- [ ] Notification when event is modified
- [ ] Notification when event is cancelled

---

## 🏗️ Technical Implementation

### Database Schema
```ruby
# New Table: events
create_table :events do |t|
  t.references :team, null: false, foreign_key: true
  t.references :creator, null: false, foreign_key: { to_table: :users }
  t.string :title, null: false
  t.string :event_type, null: false # training, game, meeting, social, other
  t.text :description
  t.datetime :start_time, null: false
  t.datetime :end_time, null: false
  t.string :location, null: false
  t.string :opponent_team # for games
  t.text :required_equipment
  t.boolean :rsvp_required, default: false
  t.integer :reminder_hours, default: 24
  t.string :status, default: 'scheduled' # scheduled, completed, cancelled
  t.timestamps
end

# New Table: event_attendees (for RSVP tracking)
create_table :event_attendees do |t|
  t.references :event, null: false, foreign_key: true
  t.references :user, null: false, foreign_key: true
  t.string :rsvp_status # attending, not_attending, maybe, no_response
  t.text :notes
  t.timestamps
end

# Indexes
add_index :events, [:team_id, :start_time]
add_index :events, :event_type
add_index :event_attendees, [:event_id, :user_id], unique: true
```

### Models
```ruby
# app/models/event.rb
class Event < ApplicationRecord
  belongs_to :team
  belongs_to :creator, class_name: 'User'
  has_many :event_attendees, dependent: :destroy
  has_many :attendees, through: :event_attendees, source: :user
  
  enum event_type: {
    training: 'training',
    game: 'game',
    meeting: 'meeting',
    social: 'social',
    other: 'other'
  }
  
  enum status: {
    scheduled: 'scheduled',
    completed: 'completed',
    cancelled: 'cancelled'
  }
  
  validates :title, :event_type, :start_time, :end_time, :location, presence: true
  validate :end_time_after_start_time
  
  scope :upcoming, -> { where('start_time >= ?', Time.current).order(:start_time) }
  scope :past, -> { where('start_time < ?', Time.current).order(start_time: :desc) }
  scope :for_month, ->(date) { where(start_time: date.beginning_of_month..date.end_of_month) }
end

# app/models/event_attendee.rb
class EventAttendee < ApplicationRecord
  belongs_to :event
  belongs_to :user
  
  enum rsvp_status: {
    no_response: 'no_response',
    attending: 'attending',
    not_attending: 'not_attending',
    maybe: 'maybe'
  }
end
```

### Controllers
```ruby
# app/controllers/events_controller.rb
class EventsController < ApplicationController
  before_action :authenticate_user!
  before_action :set_team
  before_action :authorize_event_management, only: [:new, :create, :edit, :update, :destroy]
  
  def index
    @events = @team.events.for_month(params[:month] || Date.current)
    @calendar_date = params[:month]&.to_date || Date.current
  end
  
  def show
    @event = @team.events.find(params[:id])
  end
  
  def new
    @event = @team.events.build
  end
  
  def create
    @event = @team.events.build(event_params)
    @event.creator = current_user
    
    if @event.save
      EventNotificationService.notify_team_members(@event)
      redirect_to team_events_path(@team), notice: 'Event created successfully'
    else
      render :new
    end
  end
  
  def edit
    @event = @team.events.find(params[:id])
  end
  
  def update
    @event = @team.events.find(params[:id])
    
    if @event.update(event_params)
      EventNotificationService.notify_event_change(@event)
      redirect_to team_event_path(@team, @event), notice: 'Event updated'
    else
      render :edit
    end
  end
  
  def destroy
    @event = @team.events.find(params[:id])
    @event.update(status: 'cancelled')
    EventNotificationService.notify_event_cancellation(@event)
    redirect_to team_events_path(@team), notice: 'Event cancelled'
  end
  
  private
  
  def authorize_event_management
    authorize @team, :manage_events?
  end
end
```

### Services
```ruby
# app/services/event_notification_service.rb
class EventNotificationService
  def self.notify_team_members(event)
    event.team.members.each do |member|
      EventMailer.new_event(event, member).deliver_later
      # Create in-app notification
    end
  end
  
  def self.notify_event_change(event)
    event.team.members.each do |member|
      EventMailer.event_updated(event, member).deliver_later
    end
  end
  
  def self.notify_event_cancellation(event)
    event.team.members.each do |member|
      EventMailer.event_cancelled(event, member).deliver_later
    end
  end
end
```

### Routes
```ruby
resources :teams do
  resources :events do
    member do
      post :rsvp
    end
  end
end
```

---

## 🎨 UI/UX Design

### Calendar View Layout
```
┌─────────────────────────────────────────────────┐
│  Team Calendar - El equipo                      │
│  [< November 2025 >]  [Today]  [+ New Event]   │
├─────────────────────────────────────────────────┤
│  Sun   Mon   Tue   Wed   Thu   Fri   Sat       │
├─────────────────────────────────────────────────┤
│        1      2      3      4      5      6     │
│                     🏃                           │
│   7      8      9     10     11     12     13   │
│        ⚽                   🏃                   │
│  14     15     16     17     18     19     20   │
│                            🏃    ⚽              │
│  21     22     23     24     25     26     27   │
│        📋                                       │
│  28     29     30                               │
│        🏃                                       │
└─────────────────────────────────────────────────┘

Legend:
🏃 Training  ⚽ Game  📋 Meeting  🎉 Social  📌 Other
```

### Event Detail Card
```
┌─────────────────────────────────────────────────┐
│  ⚽ Game vs. Los Tigres                    [X]  │
├─────────────────────────────────────────────────┤
│  📅 Saturday, November 19, 2025                 │
│  🕐 3:00 PM - 5:00 PM                          │
│  📍 Campo Deportivo Central                     │
│      [View on Map]                              │
│                                                 │
│  📝 Description:                                │
│  Important league game. Please arrive 30       │
│  minutes early for warm-up.                    │
│                                                 │
│  ⚽ Required Equipment:                         │
│  - Uniform                                      │
│  - Cleats                                       │
│  - Water bottle                                 │
│                                                 │
│  👥 Attendance (if RSVP enabled):              │
│  ✅ 12 Attending  ❌ 2 Not Attending  ❓ 3 Maybe│
│                                                 │
│  [Edit Event]  [Delete Event]  [Close]         │
└─────────────────────────────────────────────────┘
```

### Screenshot Placeholder

**[SCREENSHOT PLACEHOLDER]**

*Please attach screenshot showing desired calendar UI design*

---

## 🔗 Related Items
- **Epic:** [[Team Management System]]
- **Related:** Team Communication, Team Member Management
- **Depends On:** BUG-S5-001 (Parent-Player relationships should be fixed first)

---

## 📝 Notes

### Implementation Priority
- **High Priority**: Essential for team coordination
- **User Request**: Directly requested feature
- **High Value**: Significantly improves team management
- **Target**: V1.4.0 (after V1.3.0 admin dashboards)

### Future Enhancements (V1.5.0+)
- Recurring events (weekly trainings)
- Event templates (save common event types)
- Weather integration (show weather for outdoor events)
- Attendance tracking and reports
- Export to Google Calendar / iCal
- SMS reminders (in addition to email)
- Carpool coordination
- Equipment checklist per event

### Technical Considerations
- Use timezone-aware datetime handling
- Consider calendar library (FullCalendar.js or similar)
- Optimize queries for calendar month view
- Cache calendar data for performance
- Handle event conflicts/overlaps
- Mobile-first responsive design

### Testing Requirements
- Test event creation by manager
- Test event visibility for all team members
- Test calendar navigation (prev/next month)
- Test event notifications
- Test RSVP functionality
- Test mobile responsiveness
- Test timezone handling
- Test permission boundaries

---

**Status**: 📋 BACKLOG  
**Priority**: High (Essential team coordination feature)  
**Target Release**: V1.4.0  
**Estimated Effort**: 5 points (4-5 days)

---

*This feature will significantly improve team coordination and communication. Should be prioritized after V1.3.0 admin dashboards are complete.*
