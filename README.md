# Resources

Things that I commonly need for software development...

<center><img src="https://github.com/jeremygradisher/resources/blob/main/assets/231webdev-logo.png" alt="231WebDev Logo" style="max-width: 80%;" /></center>

# Ruby on Rails Resources:

## Create Ruby on Rails app locally:
```
$ rails new test123 --database=postgresql

$ rails s

$ localhost:3000
```

## Create rails app AWS Cloud9

```
1. Login to aws - create new environment - stick with Ubuntu


2. $ rails new crmquickstart

3. $ cd crmquickstart

4. Check Ruby version:
$ ruby --version

See what Ruby versions are available:
$ rvm list

ubuntu - add the version you want:
$ rvm install "ruby-3.1.2"
$ rvm install "ruby-3.1.3"

change ruby default (eventually)
$ rvm --default use 3.1.2
$ rvm --default use 3.1.3

*having problems? update RVM
$ rvm get stable

5. Change gemfile

6. add gem 'pg'
https://www.digitalocean.com/community/tutorials/how-to-use-postgresql-with-your-ruby-on-rails-application-on-ubuntu-18-04

Step 1 – Installing PostgreSQL
sudo apt update
sudo apt install postgresql postgresql-contrib libpq-dev

Step 2 – Creating a New Database Role
sudo -u postgres createuser -s ubuntu -P
set the user and password to ubuntu

Step 3 - quick check to see if it's working
sudo -u postgres psql
get out with \q


bundle install



7. Adjust database.yml
--------------------------------------------
# PostgreSQL. Versions 8.2 and up are supported.
#
# Install the pg driver:
#   gem install pg
# On Mac OS X with macports:
#   gem install pg -- --with-pg-config=/opt/local/lib/postgresql84/bin/pg_config
# On Windows:
#   gem install pg
#       Choose the win32 build.
#       Install PostgreSQL and put its /bin directory on your path.
#
# Configure Using Gemfile
# gem 'pg'
#
development:
  adapter: postgresql
  encoding: unicode
  database: ubuntu
  pool: 5
  username: ubuntu
  password:

  # Connect on a TCP socket. Omitted by default since the client uses a
  # domain socket that doesn't need configuration. Windows does not have
  # domain sockets, so uncomment these lines.
  #host: localhost
  #port: 5432

  # Schema search path. The server defaults to $user,public
  #schema_search_path: myapp,sharedapp,public

  # Minimum log levels, in increasing order:
  #   debug5, debug4, debug3, debug2, debug1,
  #   log, notice, warning, error, fatal, and panic
  # The server defaults to notice.
  #min_messages: warning

# Warning: The database defined as "test" will be erased and
# re-generated from your development database when you run "rake".
# Do not set this db to the same as development or production.
test:
  adapter: postgresql
  encoding: unicode
  database: ubuntu
  pool: 5
  username: ubuntu
  password:
  
production:
  url: <%= ENV['DATABASE_URL'] %>
--------------------------------------------


8. create run config
    rails s -b 0.0.0.0

    rake db:create
    rake db:migrate

9. fix errors:

You must use Bundler 2 or greater with this lockfile.
$ gem update --system
$ gem install bundler
$ bundler update --bundler


```

## Installing Ruby versions with rbenv
```
$ rbenv install 2.6.3
$ rbenv install 3.1.2
$ rbenv install 3.1.3
```


```
rbenv global 3.1.2   # set the default Ruby version for this machine
# or:
rbenv local 3.1.2    # set the Ruby version for this directory
```

# React Resources:

## Create React app

```
$ npx create-react-app new-app

$ cd new-app

$ npm start

Start should have bumped you here:
http://localhost:3000/

Stop the app:
  ctrl c

Other notes:
  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

```

# Github Resources - Git Resources

Add gitignore:

```
Open Terminal.

Navigate to the location of your Git repository.

Create a .gitignore file for your repository.

$ touch .gitignore
If the command succeeds, there will be no output.
```

If you want to ignore a file that is already checked in, you must untrack the file before you add a rule to ignore it. From your terminal, untrack the file.
```
$ git rm --cached FILENAME
```

Potential additions to your .gitignore:
```
# Compiled source #
###################
*.com
*.class
*.dll
*.exe
*.o
*.so

# Packages #
############
# it's better to unpack these files and commit the raw source
# git has its own built in compression methods
*.7z
*.dmg
*.gz
*.iso
*.jar
*.rar
*.tar
*.zip

# Logs and databases #
######################
*.log
*.sql
*.sqlite

# OS generated files #
######################
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db
```
https://github.com/github/gitignore - A collection of useful .gitignore templates

Show . files on Mac / Show files that start with . on Mac OSX Ventura<br>
share hidden files on Mac
```
command + shift + .
```

