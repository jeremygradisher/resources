# Resources

Things that I commonly need for software development...

<center><img src="https://github.com/jeremygradisher/resources/blob/main/assets/231webdev-logo.png" alt="231WebDev Logo" style="max-width: 80%;" /></center>

# Ruby on Rails Resources:

## Create Ruby on Rails app locally:
```
Use rbenv to set Ruby version:
$ rbenv shell 3.1.4

Check ruby version:
$ ruby -v

Create new Rails app, name it and tell it to use postgresql
$ rails new test123 --database=postgresql

Start the development server:
$ rails s

Address where app is running:
http://localhost:3000

Change the port on localhost:
$ rails s -p 3003

New localhost:
http://localhost:3003

```

## Rails 7 bin/dev wrapper to launch and manage the web server
Explanation: https://www.nickhammond.com/learning-to-love-bin-slash-dev-in-rails-7/

Rails 7 introduced a new way to deal with assets via import maps and they also introduced a new way to run your app locally, the new bin/dev file. It’s not installed by default(yet) unless you create a new app with the -css option or it’s installed later on when you run the css:install command.

To get the new css/jss bundling configured with a new app you just need to specify what CSS framework you’d like to utilize if any, these options come from the cssbundling-rails gem.

```
1. Let's create our brand new Rails application. We will use Sass as a CSS pre-processor to create our design system, esbuild to bundle our single line of JavaScript, and a Postgresql database to be able to deploy our app on Heroku at the end of the tutorial.

```
$ rails new quote-editor --css=sass --javascript=esbuild --database=postgresql
```

2. As this tutorial was written at the time of Rails 7.0.0 let's make sure we use the version of turbo-rails that was used at the time to avoid unexpected issues. Let's update our Gemfile by locking the turbo-rails version:

```
# Gemfile
gem "turbo-rails", "~> 1.0"
```

3. We can now run bundle install to install the correct version of the gem.
```
$ bundle install
```

4. Now that our application is ready, let's type the bin/setup command to install the dependencies 
and create the database:
```
$ bin/setup
```

5. We can now run the rails server, and the scripts that precompile the CSS and the JavaScript code with the bin/dev command:
```
$ bin/dev
```

6. We can now go to http://localhost:3000, and we should see the Rails boot screen.
```

# Ruby Versions:

## check Ruby version:
```
$ ruby -v
```

## Installing Ruby versions with rbenv
```
$ rbenv install 2.6.3
$ rbenv install 3.1.2
$ rbenv install 3.1.3
```

## rbenv versions
Lists all Ruby versions known to rbenv, and shows an asterisk next to the currently active version.
```
$ rbenv versions
  1.8.7-p352
  1.9.2-p290
* 1.9.3-p327 (set by /Users/sam/.rbenv/version)
  jruby-1.7.1
  rbx-1.2.4
  ree-1.8.7-2011.03
```

## rbenv version
Displays the currently active Ruby version, along with information on how it was set.
```
$ rbenv version
1.9.3-p327 (set by /Users/sam/.rbenv/version)
```

## Set Ruby version rbenv
Select a Ruby version for your project using <strong>rbenv local 3.1.2</strong>, for example. Then, proceed to install gems as you normally would
```
$ rbenv global 3.1.2   # set the default Ruby version for this machine
# or:
$ rbenv local 3.1.2    # set the Ruby version for this directory

Use rbenv to set Ruby version:
$ rbenv shell 3.1.4
```

## info on build failures: 
### https://github.com/rbenv/ruby-build/discussions/categories/build-failures

## More on rbenv:
### https://github.com/rbenv/rbenv

## Set Ruby Version with RVM
### Do not run both rbenv and RVM - You probably want just rbenv
```
See what Ruby versions are available:
$ rvm list

ubuntu - add the version you want:
$ rvm install "ruby-3.1.2"
$ rvm install "ruby-3.1.3"

change ruby default (eventually)
$ rvm --default use 3.1.2
$ rvm --default use 3.1.3
```
*having problems? update RVM
```
$ rvm get stable
```


## Turbo Rails Stuff
Turbo Rails Tutorial
Learn how to leverage the power of the [turbo-rails](https://github.com/hotwired/turbo-rails) library now included by default in Rails 7 to write reactive single-page applications without having to write a single line of custom JavaScript.

[Quote Editor Tutorial](https://github.com/jeremygradisher/quote-editor) - this has an extensive wiki with info:[Quote Editor Wiki](https://github.com/jeremygradisher/quote-editor/wiki)

---

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

Set-up React Developer Tools Chrome extension:<br>
https://youtu.be/fXRB6wgeKOo

---

# Github Resources - Git Resources

## Git resources:
```
Set username and email for Github:
$ git config --global user.name jeremygradisher
$ git config --global user.email jeremygradisher@gmail.com

Save Git credentials:
$ git config credential.helper store

Create a remote connection pointing back to a repository:
$ git remote add origin https://github.com/jeremygradisher/resources.git

Show the remote branch you are pushing and pulling from:
$ git remote -v

If you need to add a remote:
$ git remote add origin https://github.com/jeremygradisher/resources.git

If you need to remove a remote:
$ git remote set-url --delete origin https://github.com/jeremygradisher/resources.git
```

## Add gitignore:

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
.env
```
https://github.com/github/gitignore - A collection of useful .gitignore templates

---

# Heroku Information:
```
Create a heroku app by using:
$ npm install -g heroku
$ heroku login -i
$ heroku create

Rename the app to something you like by using 
$ heroku rename nameofyourchoice

Ensure your latest changes are committed using git status, if not, make a commit

Deploy your app to production:
$ git push heroku master -a appname
$ heroku run rake db:migrate -a appname

Watch Heroku logs in real time:
$ heroku logs --tail -a statusplan2

Run rails console on Heroku:
$ heroku run rails console -a status-plan

$ heroku config -a appname
$ heroku restart appname
```


## Heroku database back-up stuff:
```
Heroku backups stuff:

https://devcenter.heroku.com/articles/heroku-postgres-backups


Using Heroku CLI
If you have Heroku CLI installed on your machine, then open your terminal/command prompt and run the following command. heroku config:get DATABASE_URL -a <your_heroku_app_name>
When you run the above command, you will get your database URL in the following format.


heroku config:get DATABASE_URL -a statusplan2

*find databse color:
$ heroku config -a statusplan2



Scheduling backups
In addition to manually triggered backups, you can schedule regular automatic backups. These will run daily against the specified database.

heroku pg:backups:schedule DATABASE_URL --at '20:00 America/Detroit' --app statusplan2

*gave me this message: Scheduling automatic daily backups of postgresql-lively-75872 at 20:00 America/Detroit... done
```
---


# AWS Cloud9 IDE for Ruby on Rails development

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

## Get Middleman to Run with AWS Cloud9:
This is what you need in your run config for your live preview:
```
middleman -p $PORT
```
Then Preview Running Application.

---
# Random code

Show . files on Mac / Show files that start with . on Mac OSX Ventura<br>
share hidden files on Mac
```
command + shift + .
```
---
# Share the knowledge. Let's build!

