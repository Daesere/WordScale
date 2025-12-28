# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

---

## Development Environment Setup

This section covers setting up your development environment for Ruby on Rails development on Ubuntu (including WSL).

### Prerequisites

#### 1. Ubuntu/WSL Setup (Windows users only)

If you're on Windows, install WSL2 with Ubuntu:

```bash
# In PowerShell (as Administrator)
wsl --install -d Ubuntu
```

After installation, restart your computer and set up your Ubuntu username and password.

#### 2. Install VS Code

**On Windows:**
- Download and install VS Code from https://code.visualstudio.com/
- Install the "WSL" extension in VS Code
- Open your WSL workspace: `Ctrl+Shift+P` → "WSL: Open Folder in WSL"


#### 3. Install Ruby Development Dependencies

```bash
sudo apt update
sudo apt install -y git curl libssl-dev libreadline-dev zlib1g-dev \
  autoconf bison build-essential libyaml-dev libreadline-dev \
  libncurses5-dev libffi-dev libgdbm-dev
```

#### 4. Install rbenv (Ruby Version Manager)

```bash
# Install rbenv
curl -fsSL https://github.com/rbenv/rbenv-installer/raw/HEAD/bin/rbenv-installer | bash

# Configure your shell (for bash)
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc
```

#### 5. Install Ruby

```bash
# Install Ruby 3.3.6
rbenv install 3.3.6

# Set as global version
rbenv global 3.3.6

# Verify installation
ruby --version  # Should show: ruby 3.3.6
```

#### 6. Install Rails

```bash
# Install Rails gem
gem install rails

# Verify installation
rails --version  # Should show: Rails 8.1.1
```

#### 7. Install VS Code Extensions

Install these recommended extensions for Ruby on Rails development:

- **Ruby LSP** (`Shopify.ruby-lsp`) - Language server for Ruby
- **Ruby Extensions Pack** (`Shopify.ruby-extensions-pack`) - Collection of useful Ruby extensions
- **Rails** (`bung87.rails`) - Rails file navigation and snippets

Install via VS Code or command line:
```bash
code --install-extension Shopify.ruby-lsp
code --install-extension Shopify.ruby-extensions-pack
code --install-extension bung87.rails
```

### Project Setup

Once your development environment is ready:

```bash
# Clone the repository (if not already done)
cd /path/to/project

# Install project dependencies
bundle install

# Create and set up the database
bin/rails db:create
bin/rails db:migrate

# Seed the database (optional)
bin/rails db:seed

# Start the development server
bin/dev
```

### Running the Application

```bash
# Start the Rails server
bin/rails server
# Or use the shorthand
bin/rails s

# Visit http://localhost:3000 in your browser
```

### Running Tests

```bash
# Run all tests
bin/rails test

# Run specific test file
bin/rails test test/models/post_test.rb

# Run system tests
bin/rails test:system
```

### Common Commands

```bash
# Generate a new controller
bin/rails generate controller ControllerName action1 action2

# Generate a new model
bin/rails generate model ModelName field1:type field2:type

# Generate a scaffold (model + views + controller)
bin/rails generate scaffold ResourceName field1:type field2:type

# Run database migrations
bin/rails db:migrate

# Rollback last migration
bin/rails db:rollback

# Open Rails console
bin/rails console

# View routes
bin/rails routes
```

### Troubleshooting

**Ruby version issues:**
```bash
# Check current Ruby version
ruby --version

# List installed Ruby versions
rbenv versions

# Install specific Ruby version
rbenv install 3.3.6

# Set local project Ruby version
rbenv local 3.3.6
```

**Gem issues:**
```bash
# Update bundler
gem update --system
gem install bundler

# Clean and reinstall gems
bundle clean --force
bundle install
```

**Database issues:**
```bash
# Reset database
bin/rails db:reset

# Drop and recreate database
bin/rails db:drop db:create db:migrate
