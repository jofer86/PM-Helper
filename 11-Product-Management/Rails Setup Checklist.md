# Rails Setup Checklist - Sports Team Manager

## 🚀 Initial Setup (Day 1)

### 1. Create Rails Application
```bash
# Create new Rails app with PostgreSQL
rails new sports_team_manager -d postgresql --css tailwind

cd sports_team_manager

# Add essential gems to Gemfile
bundle add devise pundit image_processing sidekiq redis
bundle install
```

### 2. Database Configuration
```bash
# Configure database
rails db:create
rails db:migrate

# Generate Devise configuration
rails generate devise:install
rails generate devise User
```

### 3. Essential Generators
```bash
# Generate core models
rails generate model Team name:string sport:string age_category:string season:string description:text invite_code:string manager:references
rails generate model Player first_name:string last_name:string date_of_birth:date position:string jersey_number:integer parent_email:string parent_phone:string emergency_contact:string emergency_phone:string medical_notes:text active:boolean team:references
rails generate model Announcement title:string content:text priority:string category:string team:references user:references

# Generate controllers
rails generate controller Teams index show new create edit update
rails generate controller Players index show new create edit update destroy
rails generate controller Announcements index show new create

# Generate Pundit policies
rails generate pundit:install
rails generate pundit:policy Team
rails generate pundit:policy Player
rails generate pundit:policy Announcement
```

## 🔧 Configuration Files

### 1. Application Configuration
```ruby
# config/application.rb
config.i18n.default_locale = :es
config.i18n.available_locales = [:es, :en]
config.time_zone = 'Mexico City'
```

### 2. Routes Configuration
```ruby
# config/routes.rb
Rails.application.routes.draw do
  devise_for :users
  root 'teams#index'
  
  resources :teams do
    resources :players, except: [:show]
    resources :announcements, except: [:show]
  end
  
  # API routes for mobile
  namespace :api do
    namespace :v1 do
      resources :teams, only: [:index, :show]
      resources :announcements, only: [:index, :show]
    end
  end
end
```

### 3. Tailwind Configuration
```javascript
// tailwind.config.js
module.exports = {
  content: [
    './app/views/**/*.html.erb',
    './app/helpers/**/*.rb',
    './app/assets/stylesheets/**/*.css',
    './app/javascript/**/*.js'
  ],
  theme: {
    extend: {
      colors: {
        'team-blue': '#1e40af',
        'team-green': '#059669',
        'team-red': '#dc2626'
      },
      spacing: {
        '18': '4.5rem',   // 72px equivalent
        '22': '5.5rem',   // 88px equivalent  
        '26': '6.5rem',   // 104px equivalent
      },
      fontSize: {
        'xs': ['0.75rem', { lineHeight: '1rem' }],
        'sm': ['0.875rem', { lineHeight: '1.25rem' }],
        'base': ['1rem', { lineHeight: '1.5rem' }],
        'lg': ['1.125rem', { lineHeight: '1.75rem' }],
        'xl': ['1.25rem', { lineHeight: '1.75rem' }],
      }
    }
  }
}
```

## 📱 Hotwire Setup

### 1. Stimulus Controllers
```bash
# Generate Stimulus controllers
rails generate stimulus player_form
rails generate stimulus announcement_form
rails generate stimulus team_dashboard
```

### 2. Turbo Frame Templates
```erb
<!-- app/views/shared/_turbo_frame_layout.html.erb -->
<%= turbo_frame_tag dom_id(record) do %>
  <%= yield %>
<% end %>
```

## 🔐 Security & Authentication

### 1. Devise Configuration
```ruby
# config/initializers/devise.rb
Devise.setup do |config|
  config.mailer_sender = 'noreply@sportsteammanager.mx'
  config.authentication_keys = [:email]
  config.case_insensitive_keys = [:email]
  config.strip_whitespace_keys = [:email]
  config.skip_session_storage = [:http_auth]
  config.stretches = Rails.env.test? ? 1 : 12
  config.reconfirmable = true
  config.expire_all_remember_me_on_sign_out = true
  config.password_length = 6..128
  config.email_regexp = /\A[^@\s]+@[^@\s]+\z/
  config.reset_password_within = 6.hours
  config.sign_out_via = :delete
end
```

### 2. Pundit Application Policy
```ruby
# app/policies/application_policy.rb
class ApplicationPolicy
  attr_reader :user, :record

  def initialize(user, record)
    @user = user
    @record = record
  end

  def index?
    false
  end

  def show?
    false
  end

  def create?
    false
  end

  def new?
    create?
  end

  def update?
    false
  end

  def edit?
    update?
  end

  def destroy?
    false
  end

  class Scope
    def initialize(user, scope)
      @user = user
      @scope = scope
    end

    def resolve
      raise NotImplementedError
    end

    private

    attr_reader :user, :scope
  end
end
```

## 📧 Email Configuration

### 1. ActionMailer Setup
```ruby
# config/environments/development.rb
config.action_mailer.delivery_method = :letter_opener
config.action_mailer.perform_deliveries = true
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }

# config/environments/production.rb
config.action_mailer.delivery_method = :sendgrid
config.action_mailer.default_url_options = { host: 'sportsteammanager.mx' }
```

### 2. Mailer Generators
```bash
# Generate mailers
rails generate mailer TeamMailer welcome_manager player_added announcement
rails generate mailer UserMailer welcome_email password_reset
```

## 🧪 Testing Setup

### 1. RSpec Configuration
```ruby
# Add to Gemfile (development, test group)
gem 'rspec-rails'
gem 'factory_bot_rails'
gem 'faker'
gem 'capybara'
gem 'selenium-webdriver'

# Generate RSpec configuration
rails generate rspec:install
```

### 2. Factory Bot Setup
```ruby
# spec/factories/users.rb
FactoryBot.define do
  factory :user do
    first_name { Faker::Name.first_name }
    last_name { Faker::Name.last_name }
    email { Faker::Internet.email }
    password { 'password123' }
    role { 'manager' }
  end
end

# spec/factories/teams.rb
FactoryBot.define do
  factory :team do
    name { Faker::Team.name }
    sport { 'Fútbol' }
    age_category { 'Juvenil' }
    season { '2025' }
    association :manager, factory: :user
  end
end
```

## 🚀 Deployment Preparation

### 1. Heroku Setup
```bash
# Install Heroku CLI and create app
heroku create sports-team-manager-mx
heroku addons:create heroku-postgresql:mini
heroku addons:create heroku-redis:mini
heroku addons:create sendgrid:starter

# Set environment variables
heroku config:set RAILS_MASTER_KEY=$(cat config/master.key)
```

### 2. Production Gems
```ruby
# Add to Gemfile production group
gem 'rails_12factor'
gem 'pg'
gem 'redis'
gem 'sidekiq'
```

## ✅ Sprint 1 Ready Checklist

- [ ] Rails application created and configured
- [ ] PostgreSQL database setup
- [ ] Devise authentication working
- [ ] Pundit authorization configured
- [ ] Core models generated and migrated
- [ ] Tailwind CSS styling setup
- [ ] Hotwire (Turbo + Stimulus) configured
- [ ] Spanish localization files created
- [ ] Email system configured
- [ ] Basic testing framework setup
- [ ] Deployment pipeline ready

---
**Created**: 2025-10-31  
**Framework**: Ruby on Rails 7.1+  
**Estimated Setup Time**: 4-6 hours  
**Ready for**: Sprint 1 Development

## Next Steps
1. Complete Rails setup using this checklist
2. Begin STM-001-01 (Team Registration) development
3. Set up continuous integration
4. Start daily development standups
