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

1. Let's create our brand new Rails application. We will use Sass as a CSS pre-processor to create our design system, esbuild to bundle our single line of JavaScript, and a Postgresql database to be able to deploy our app on Heroku at the end of the tutorial.

```
rails new app-name --css=sass --javascript=esbuild --database=postgresql

or with bootstrap:
rails new app-name --css=bootstrap --javascript=esbuild --database=postgresql
```

2. We can now run bundle install to install the correct version of the gem.
```
bundle install
```

3. Now that our application is ready, let's type the bin/setup command to install the dependencies 
and create the database:
```
bin/setup
```

4. We can now run the rails server, and the scripts that precompile the CSS and the JavaScript code with the bin/dev command:
```
bin/dev
```

5. We can now go to http://localhost:3000, and we should see the Rails boot screen.

### If you cloned this, Precompile javascript/css:
```
rails assets:precompile
```

## Run Rails Tests
```
bin/rails test:system
```

More on testing here: https://github.com/jeremygradisher/testing-playground

## Seed the db from fixtures
```
bin/rails db:seed
```

## Add Bootstrap to existing Rails 7 application:
1. bundle add cssbundling-rails
```
bin/rails css:install:bootstrap
```

2. bundle add jsbundling-rails
```
bin/rails javascript:install:esbuild
```

3. Precompile your build assets:
```
rails assets:precompile
```

### To add Bootstrap from scratch use --css=bootstrap
```
rails new app-name --css=bootstrap --javascript=esbuild --database=postgresql
```
-c, [--css=CSS] # Choose CSS processor [options: tailwind, bootstrap, bulma, postcss, sass... check https://github.com/rails/cssbundling-rails]


---

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

## Create a page in a ruby on rails app:
1. Generate a controller: 
```
rails generate controller Contacts index
```

2. Make sure the controller and the view both exist.


3. Define the route: In the config/routes.rb file, add a route that maps the URL /contacts to the Contacts#index action. You can do this by adding the following line:
```
get '/contacts', to: 'contacts#index'
or
resources :contacts, only: [:index]
```
This will create the route /contacts that maps to the Contacts#index action, and restrict it to only the index action.

That's it! You should now be able to access your Contacts page by visiting the URL /contacts in your application.

## Make a page your root route

To use a Welcome page as the root route in a Ruby on Rails application, 
you need to follow the steps below:

1. Create a new controller named "welcome" by running the following command in your terminal:
```
rails generate controller Welcome index
```

This command will generate a new controller named "Welcome" and a view named "index". The view is located in the app/views/welcome directory.

2. Open the config/routes.rb file and add the following line:

```ruby
root 'welcome#index'
```

3. In the app/views/welcome/index.html.erb file, you can add your Welcome page content.

4. Start your Rails server and navigate to http://localhost:3000/ in your browser. You should see your Welcome page as the root route of your application.

That's it! You have successfully set up your Welcome page as the root route in your Ruby on Rails application.

### Devise - functional basic user auth:
https://github.com/jeremygradisher/test-devise-basic

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

## Github Copilot

Intro video for Copilot: https://www.youtube.com/watch?v=Fi3AJZZregI

### You can ask it questions in the comments, and it will try to answer them. For example:
```
// q: What does SOLID stand for?
```
It will start to autocomplete the answer for you:
```
// a: Single responsibility, Open-closed, Liskov substitution, Interface segregation, Dependency inversion
```

### Use Tab to accept the suggestion. You can also ask it to explain the answer. 

You can get it to write code by creating a comment with an objective:
```html
<!-- a h2 with inline style making the heading blue -->
        <h2 style="color: blue;">Example</h2>

<!-- create a bulleted list-->
        <ul>
            <li>Example</li>
            <li>Example</li>
            <li>Example</li>
        </ul>
```
* Create the comment with the objective, then hit enter. It will write the code for you.

You can hover over the grayed out code to select from multiple options:
https://youtu.be/Fi3AJZZregI?t=609<br>
By hovering over the grayed out code, you can push ctrl+enter to open a copilot menu with multiple options for the code.

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

Check the status of your app:
$ heroku info

Add a remote to an existing app:
$ heroku git:remote -a appname
```

## Setup application on Heroku - Heroku app setup

1. Create new app through Heroku dashboard

2. Connect it to the git then manually deploy branch from the dashboard

3. This threw an error:
"Your bundle only supports platforms ["arm64-darwin-22"] but your local platform is x86_64-linux. Add the current platform to the lockfile with bundle lock --add-platform x86_64-linux and try again."

To resolve this issue, you can follow the instructions provided in the error message. Run the following command in your Rails application's directory on your local machine:
```
bundle lock --add-platform x86_64-linux
```

4. Ran that through the cli, and then pushed to github, then pushed to Heroku

* at this point launched app by pushing "Open app" button in upper right corner of heroku dashboard. App is running but fails if I try and push links.

5. Jump into the Heroku logs for clues:
```
heroku logs --tail -a affyex-devise-users
```

* I feel like the logs do not tell me much. I see something about Turbo streams. Pretty sure this is because there is no redis server currently setup in the Heroku dash. We also need to setup dynos.

6. Run migrations:
```
heroku run rake db:migrate -a affyex-devise-users
```

7. Getting Redis to work:
```
heroku addons:create heroku-redis:mini -a affyex-devise-users
```

8. Check that you have 2 Installed add-ons: Heroku-Postgres and Heroku Data for Redis

9. Restart the dynos and chack that all is working. Create a User.

10. Use Heroku Rails console to make your user an admin:

Open Heroku Rails console:
```
heroku run rails console -a affyex-devise-users  
```
* then within the console:
```
user = User.last
user.update(is_admin: !user.is_admin)
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

# AWS IAM User and S3 Bucket Setup

1. Create IAM user and grab the keys:
Click Users in the left hand navigation
 - Add Users button in upper right hand corner.

2. Within User details, create a User name and select Provide user access to the AWS Management Console - which will give us an access point to make changes or address issues. In this instance I selected "I want to create and IAM user"

3. Go ahead and create without attaching a policy. We will come back to that.

4. Create the S3 bucket - Click create bucket. Name it. AWS Region matters - Currently deselecting the Block all public access setting.

bucket:

Create and Connect policy to the User!:
5. Go back to services and click IAM hit users in the left nav and click into the user

6. hit policies in the left click get started (if necessary) 

7. click create policy - Use JSON

8. Attach policy to IAM user created
Here is a sample policy, replace the code with your s3 bucket name as needed below:
```
{
"Version": "2012-10-17",
"Statement": [
{
            "Effect": "Allow",
            "Action": "s3:*",
            "Resource": [
            "arn:aws:s3:::bucketname",
            "arn:aws:s3:::bucketname/*"
            ]
},
{
"Effect": "Allow",
"Action": "s3:ListAllMyBuckets",
"Resource": "arn:aws:s3:::*"
}
]
}
```
9. hit Next - name the policy
Policy name: test

10. go to users and attach the policy under permissions attach policy

11. Click back into the user and create the access keys that you need - choose just the cli:
Now we have what we need:

user:
Access Key ID:
Secret Access Key:
bucket:

Remember that I have these for access as well:
Console sign-in URL:
User name:
Console password:




---
# Command line stuff:
### Find out what is running on a particular port on macOS
```
sudo lsof -i :3000
```

### Kill the process running on a specific port on macOS
```
kill -9 <PID>
```

---
# Random code

Show . files on Mac / Show files that start with . on Mac OSX Ventura<br>
share hidden files on Mac
```
command + shift + .
```
Press Cmd + Shift + G to bring up the Go to Folder box and enter /private/var/folders.
```
Cmd + Shift + G
```

---
# Share the knowledge. Let's build!!!

