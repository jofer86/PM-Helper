# Sports Team Manager - Technical Architecture

## 🛠️ Technology Stack

### Core Framework
- **Backend**: Ruby on Rails 7.1+
- **Frontend**: Rails with Hotwire (Turbo + Stimulus)
- **Database**: PostgreSQL 15+
- **Styling**: Tailwind CSS
- **Authentication**: Devise gem
- **Authorization**: Pundit gem

### Key Gems & Libraries
```ruby
# Gemfile essentials
gem 'rails', '~> 7.1'
gem 'pg', '~> 1.1'
gem 'devise'                    # Authentication
gem 'pundit'                    # Authorization
gem 'image_processing', '~> 1.2' # Image uploads
gem 'turbo-rails'               # Hotwire Turbo
gem 'stimulus-rails'            # Hotwire Stimulus
gem 'tailwindcss-rails'         # Styling
gem 'redis', '~> 4.0'          # Caching & ActionCable
gem 'sidekiq'                   # Background jobs
gem 'mail'                      # Email notifications
gem 'i18n'                      # Spanish localization
```

## 🏗️ Application Architecture

### MVC Structure
```
app/
├── models/
│   ├── user.rb
│   ├── team.rb
│   ├── player.rb
│   ├── announcement.rb
│   ├── message.rb
│   └── schedule.rb
├── controllers/
│   ├── application_controller.rb
│   ├── teams_controller.rb
│   ├── players_controller.rb
│   ├── announcements_controller.rb
│   └── messages_controller.rb
└── views/
    ├── layouts/
    ├── teams/
    ├── players/
    └── shared/
```

### Database Schema (Initial)
```ruby
# db/migrate/001_create_users.rb
class CreateUsers < ActiveRecord::Migration[7.1]
  def change
    create_table :users do |t|
      t.string :email,              null: false, default: ""
      t.string :first_name,         null: false
      t.string :last_name,          null: false
      t.string :phone
      t.string :role,               default: 'manager'
      t.timestamps
    end
    add_index :users, :email, unique: true
  end
end

# db/migrate/002_create_teams.rb
class CreateTeams < ActiveRecord::Migration[7.1]
  def change
    create_table :teams do |t|
      t.string :name,               null: false
      t.string :sport,              null: false
      t.string :age_category,       null: false
      t.string :season,             null: false
      t.text :description
      t.string :invite_code,        null: false
      t.references :manager, null: false, foreign_key: { to_table: :users }
      t.timestamps
    end
    add_index :teams, :invite_code, unique: true
  end
end

# db/migrate/003_create_players.rb
class CreatePlayers < ActiveRecord::Migration[7.1]
  def change
    create_table :players do |t|
      t.string :first_name,         null: false
      t.string :last_name,          null: false
      t.date :date_of_birth,        null: false
      t.string :position
      t.integer :jersey_number
      t.string :parent_email
      t.string :parent_phone
      t.string :emergency_contact
      t.string :emergency_phone
      t.text :medical_notes
      t.boolean :active,            default: true
      t.references :team, null: false, foreign_key: true
      t.timestamps
    end
    add_index :players, [:team_id, :jersey_number], unique: true
  end
end
```

## 🔐 Authentication & Authorization

### User Roles (Pundit Policies)
```ruby
# app/policies/application_policy.rb
class ApplicationPolicy
  attr_reader :user, :record

  def initialize(user, record)
    @user = user
    @record = record
  end

  def manager?
    user&.role == 'manager'
  end

  def parent?
    user&.role == 'parent'
  end

  def player?
    user&.role == 'player'
  end
end

# app/policies/team_policy.rb
class TeamPolicy < ApplicationPolicy
  def show?
    user.teams.include?(record) || manager_of_team?
  end

  def update?
    manager_of_team?
  end

  private

  def manager_of_team?
    record.manager == user
  end
end
```

## 📱 Frontend Architecture (Hotwire)

### Turbo Frames for Dynamic Updates
```erb
<!-- app/views/teams/show.html.erb -->
<%= turbo_frame_tag "team_#{@team.id}" do %>
  <div class="team-dashboard">
    <%= render 'team_info', team: @team %>
    
    <%= turbo_frame_tag "players_list" do %>
      <%= render 'players/list', players: @team.players %>
    <% end %>
    
    <%= turbo_frame_tag "announcements" do %>
      <%= render 'announcements/recent', announcements: @team.recent_announcements %>
    <% end %>
  </div>
<% end %>
```

### Stimulus Controllers for Interactivity
```javascript
// app/javascript/controllers/player_form_controller.js
import { Controller } from "@hotwire/stimulus"

export default class extends Controller {
  static targets = ["form", "errors"]
  
  connect() {
    console.log("Player form controller connected")
  }
  
  submit(event) {
    event.preventDefault()
    
    fetch(this.formTarget.action, {
      method: "POST",
      body: new FormData(this.formTarget),
      headers: {
        "X-CSRF-Token": document.querySelector("[name='csrf-token']").content
      }
    })
    .then(response => response.text())
    .then(html => {
      if (html.includes("error")) {
        this.errorsTarget.innerHTML = html
      } else {
        // Success - update players list
        document.querySelector("#players_list").innerHTML = html
      }
    })
  }
}
```

## 🌐 Internationalization (Spanish Support)

### Locale Configuration
```ruby
# config/application.rb
config.i18n.default_locale = :es
config.i18n.available_locales = [:es, :en]

# config/locales/es.yml
es:
  activerecord:
    models:
      team: "Equipo"
      player: "Jugador"
      user: "Usuario"
    attributes:
      team:
        name: "Nombre del equipo"
        sport: "Deporte"
        age_category: "Categoría de edad"
      player:
        first_name: "Nombre"
        last_name: "Apellido"
        position: "Posición"
        jersey_number: "Número de camiseta"
```

## 📧 Email & Notifications

### ActionMailer Setup
```ruby
# app/mailers/team_mailer.rb
class TeamMailer < ApplicationMailer
  default from: 'noreply@sportsteammanager.mx'

  def welcome_manager(team)
    @team = team
    @manager = team.manager
    mail(to: @manager.email, subject: 'Bienvenido a Sports Team Manager')
  end

  def player_added(player)
    @player = player
    @team = player.team
    mail(to: @player.parent_email, subject: "#{@player.first_name} agregado al equipo #{@team.name}")
  end

  def announcement(announcement, recipient)
    @announcement = announcement
    @team = announcement.team
    @recipient = recipient
    mail(to: recipient.email, subject: "Anuncio: #{@announcement.title}")
  end
end
```

## 🚀 Deployment Architecture

### Production Stack
- **Hosting**: Heroku or Railway (for rapid deployment)
- **Database**: Heroku Postgres or Railway PostgreSQL
- **Redis**: Heroku Redis (for ActionCable and Sidekiq)
- **File Storage**: AWS S3 or Cloudinary (for player photos)
- **Email**: SendGrid or Mailgun
- **Monitoring**: Rollbar or Bugsnag

### Environment Configuration
```ruby
# config/environments/production.rb
Rails.application.configure do
  config.force_ssl = true
  config.active_storage.variant_processor = :mini_magick
  
  # ActionCable for real-time messaging
  config.action_cable.allowed_request_origins = ['https://sportsteammanager.mx']
  
  # Email configuration
  config.action_mailer.delivery_method = :sendgrid
  config.action_mailer.default_url_options = { host: 'sportsteammanager.mx' }
end
```

## 📊 Performance Considerations

### Database Optimization
```ruby
# app/models/team.rb
class Team < ApplicationRecord
  belongs_to :manager, class_name: 'User'
  has_many :players, -> { where(active: true) }, dependent: :destroy
  has_many :announcements, dependent: :destroy
  
  # Efficient queries
  scope :with_players, -> { includes(:players) }
  scope :recent, -> { order(created_at: :desc) }
  
  validates :name, presence: true, length: { maximum: 100 }
  validates :invite_code, presence: true, uniqueness: true
  
  before_create :generate_invite_code
  
  private
  
  def generate_invite_code
    self.invite_code = SecureRandom.alphanumeric(8).upcase
  end
end
```

### Caching Strategy
```ruby
# app/controllers/teams_controller.rb
class TeamsController < ApplicationController
  before_action :authenticate_user!
  before_action :set_team
  
  def show
    @players = Rails.cache.fetch("team_#{@team.id}_players", expires_in: 5.minutes) do
      @team.players.includes(:team).to_a
    end
    
    @recent_announcements = @team.announcements.recent.limit(5)
  end
  
  private
  
  def set_team
    @team = current_user.teams.find(params[:id])
  end
end
```

---
**Created**: 2025-10-31  
**Tech Lead**: TBD  
**Framework**: Ruby on Rails 7.1+  
**Target Deployment**: Heroku/Railway

## Related Documents
- [[Sports Team Manager - Product Overview]]
- [[Sprint 1 - Foundation MVP]]
- [[Story - Team Manager Registration]]
