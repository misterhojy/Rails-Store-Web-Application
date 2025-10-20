# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Rails 7.2.2 store application using SQLite3 as the database. The application uses Hotwire (Turbo and Stimulus) for modern JavaScript interactions and follows standard Rails conventions.

## Architecture

**Technology Stack:**
- Rails 7.2.2
- SQLite3 database
- Hotwire (Turbo Rails + Stimulus)
- Import maps for JavaScript
- Puma web server
- Sprockets for asset pipeline

**Models:**
- `Product` - Currently has `name:string` with presence validation (app/models/product.rb:2)

**Routes:**
Note: There's an inconsistency in config/routes.rb - the create action routes to `product#create` (line 17) instead of `products#create` (singular vs plural controller name). The update route also has an incomplete `put "/product"` definition (line 23).

## Development Commands

**Setup:**
```bash
bin/setup                    # Initial setup
bin/rails db:create          # Create database
bin/rails db:migrate         # Run migrations
bin/rails db:seed            # Seed database
```

**Running the application:**
```bash
bin/rails server             # Start server on http://localhost:3000
bin/dev                      # Start with assets watching (if using foreman)
```

**Database:**
```bash
bin/rails db:migrate                        # Run pending migrations
bin/rails db:rollback                       # Rollback last migration
bin/rails db:migrate:status                 # Check migration status
bin/rails db:reset                          # Drop, create, migrate, seed
bin/rails g migration MigrationName         # Generate new migration
```

**Models & Generators:**
```bash
bin/rails g model ModelName field:type      # Generate model with migration
bin/rails g controller ControllerName       # Generate controller
bin/rails g scaffold ModelName field:type   # Generate full scaffold
```

**Console:**
```bash
bin/rails console            # Start Rails console
bin/rails console --sandbox  # Console that rolls back changes on exit
```

**Testing:**
```bash
bin/rails test                              # Run all tests
bin/rails test test/models/product_test.rb  # Run specific test file
bin/rails test test/models/product_test.rb:5 # Run test at specific line
```

**Code Quality:**
```bash
bin/rubocop                  # Run RuboCop linter (Omakase Ruby styling)
bin/rubocop -a               # Auto-correct offenses
bin/brakeman                 # Run security vulnerability scanner
```

**Asset Management:**
```bash
bin/rails assets:precompile  # Precompile assets
bin/rails assets:clobber     # Remove compiled assets
```

## Database Schema

Current schema (db/schema.rb):
- `products` table: id, name (string), created_at, updated_at

## Testing Structure

- `test/models/` - Model tests
- `test/controllers/` - Controller tests
- `test/integration/` - Integration tests
- `test/system/` - System tests using Capybara and Selenium
- `test/fixtures/` - Test data fixtures

Use `test/test_helper.rb` for shared test configuration.
