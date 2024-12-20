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
bin/rails assets:precompile
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
bin/rails assets:precompile
```

### To add Bootstrap from scratch use --css=bootstrap
```
rails new app-name --css=bootstrap --javascript=esbuild --database=postgresql
```
-c, [--css=CSS] # Choose CSS processor [options: tailwind, bootstrap, bulma, postcss, sass... check https://github.com/rails/cssbundling-rails]

---

## Rails generate scaffold Article:

1. In your case, the ModelName would be Article and the fields would be title of type string and article of type text. Therefore, your command would look like this:
```
bin/rails generate scaffold Article title:string article:text
```

2. apply the migration:
```
bin/rails db:migrate
```

3. Add to the Routes:
```
resources :articles
```


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

## HTTP Basic Authentication

1. Controller
Add this to the controller that manages the page you want to protect.

```
class YourController < ApplicationController
  http_basic_authenticate_with name: "foo", password: "bar", only: [:your_protected_action]
  
  def your_protected_action
    # Your action code here
  end
end
```
Replace "foo" and "bar" with the username and password you want to use.

2. Also, I see this on the Factory:
```
class ApplicationController < ActionController::Base

  unless Rails.env.development? || Rails.env.test?
    http_basic_authenticate_with name: ENV['HTTP_BASIC_AUTH_NAME'], password: ENV['HTTP_BASIC_AUTH_PASSWORD']
  end

end
```
You would need a .env file with the credentials in it for local, protected by .gitingore.<br>
The contents of your .env file might look like this:

```
HTTP_BASIC_AUTH_NAME=myusername
HTTP_BASIC_AUTH_PASSWORD=mypassword
```

For production we can add that to the envelope easy in the Heroku dashboard.

---

## Postmark setup:
### Send an email with the Postmark Rails Gem
### Learn more -> https://postmarkapp.com/developer/integration/official-libraries#rails-gem


1. Add postmark-rails to your Gemfile and run bundle install.
```
gem 'postmark-rails'
```

2. Login to https://postmarkapp.com and create a new server. Then get the postmark_api_token.

3. run ```bin/rails secret```, then run ```EDITOR="code --wait" bin/rails credentials:edit``` and add:
```
postmark_api_token: "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
```
Hit save (Cmd + S) and x out of the file. Be sure you see: File encrypted and saved.

4. Add the api to heroku manually (Doing this also - Not sure if I actually need this)
```
postmark_api_token:
```

5. Add this to your config/application.rb file:
```
config.action_mailer.delivery_method = :postmark
config.action_mailer.postmark_settings = { :api_token => Rails.application.credentials.postmark_api_token }
```

6. add this to config/environments/production.rb:
```
Rails.application.routes.default_url_options[:host] = 'affyex-devise-users.herokuapp.com'
```

7. Doing this, usure if necessarry currently:
The Heroku environment needs to have the same Postmark API token as your local environment. In Heroku, under your application settings, there is a section called "Config Vars". Add a new Config Var with the key as RAILS_MASTER_KEY and the value as the master key from your local config/master.key file.

8. I had to change this line in config/initializers/devise.rb:
```
config.mailer_sender = 'gradisher@affygility.com'
```

---

## Sidekiq setup:
1. add gem to Gemfile:
```ruby
gem 'sidekiq'
```
* run ```bundle install```

2. within app/config/application.rb, add:
```ruby
config.active_job.queue_adapter = :sidekiq
```

3. add this to config/routes.rb:
```ruby
  require 'sidekiq/web'

  Sidekiq::Web.use(Rack::Auth::Basic) do |user, password|
    [user, password] == [ENV['HTTP_BASIC_AUTH_NAME'], ENV['HTTP_BASIC_AUTH_PASSWORD']]
  end

  mount Sidekiq::Web => '/sidekiq'
```   

4. Create ```Procfile``` in root directory and add:
``` 
worker: bundle exec sidekiq
```

5. On heroku, add the dyno (worker) to the app.
```
heroku ps:scale worker=1
```
https://github.com/sidekiq/sidekiq/wiki/Getting-Started


---

## Create a Mailer:

1. Create a mailer:
```
bin/rails generate mailer UserMailer
```

2. Add this to app/mailers/user_mailer.rb:
```ruby
class UserMailer < ApplicationMailer
  default from: 'no-reply@affygility.com'

  def welcome_email
    @user = params[:user]
    @url  = 'http://affyex-devise-users.herokuapp.com/users/sign_in'
    mail(to: @user.email, subject: 'Welcome to AffyEx')
  end
end
```

3. Create a file called welcome_email.html.erb in app/views/user_mailer/. This will be the template used for the email, formatted in HTML:
```ruby
<!DOCTYPE html>
<html>
  <head>
    <meta content='text/html; charset=UTF-8' http-equiv='Content-Type' />
  </head>
  <body>
    <h1>Welcome to the AffyEx!, <%= @user.email %></h1>
    <p>
    You have successfully signed up to AffyEx,
    your username is: <%= @user.email %>.<br>
    To login to the site, just follow this link: <%= @url %>.
    </p>
    <p>Thanks for joining and have a great day!</p>
  </body>
</html>
```

4. Add this to app/views/user_mailer/welcome_email.text.erb:
```
Welcome to AffyEx, <%= @user.email %>
===============================================
You have successfully signed up to AffyEx,
your username is: <%= @user.email %>.

To login to the site, just follow this link: <%= @url %>.

Thanks for joining and have a great day!
```

5. To send a welcome email after a user signs up, you'll want to override Devise's RegistrationsController. Here's how you can do that:

* Create a new file in your controllers directory. The path should be app/controllers/users/confirmations_controller.rb.

In this file, add the following code:

```ruby
class Users::ConfirmationsController < Devise::ConfirmationsController
  def show
    super do |resource|
      if resource.errors.empty?
        UserMailer.with(user: resource).welcome_email.deliver_later
      end
    end
  end
end
```
The super keyword calls the original show method from Devise::ConfirmationsController, and the block (do |resource| ... end) is executed after the user is confirmed. The resource.errors.empty? check ensures that the user was successfully confirmed before sending the email.

* Now you need to tell Devise to use your new controller. In your routes.rb file, modify the Devise routes to look like this:

```ruby
devise_for :users, controllers: { confirmations: 'users/confirmations' }
```
This will ensure that the welcome email is only sent after a user has successfully confirmed their account.

* Finally, make sure you have a UserMailer with a welcome_email method and a corresponding view. The mailer might look something like this:

```ruby
class UserMailer < ApplicationMailer
  def welcome_email
    @user = params[:user]
    mail(to: @user.email, subject: 'Welcome to Our Website!')
  end
end
```

---

## Permissions using Pundit:

Static Page Policy:
```ruby
  class PagePolicy
    attr_reader :user, :page
  
    def initialize(user, page)
      @user = user
      @page = page
    end
  
    def show?
      user.present?
    end

    def special_page?
      ['Affygility', 'Admin'].include?(user&.role)
    end
  
    def affygility?
      user&.role == 'Affygility'
    end

    def admin?
      user&.role == 'Admin'
    end

    def downloader?
      user&.role == 'Downloader'
    end

    def viewer?
      user&.role == 'Viewer'
    end
  end
  
```


## Then in the Group controller:
```ruby
class GroupsController < ApplicationController
  before_action :authorize_group, only: [:new, :create]

  # ... other controller methods ...

  private

  def authorize_group
    authorize :group
  end
end

```

## In your views, to conditionally display links or other elements based on this policy:
```ruby
<% if policy(:group).new? %>
  <%= link_to 'Create Group', new_group_path %>
<% end %>

```

## More complex example:
```ruby
<li class="sidebar-item">
    <% if policy(:account).index? || policy(:group).index? || policy(:user).index? %>
        <a data-bs-target="#agu" data-bs-toggle="collapse" class="sidebar-link collapsed">
            <i class="align-middle" data-feather="users"></i> <span class="align-middle">Account/Group/Users</span>
        </a>
        <ul id="agu" class="sidebar-dropdown list-unstyled collapse " data-bs-parent="#sidebar">
            <% if policy(:account).index? %>
                <li class="sidebar-item"><a class="sidebar-link" href="/accounts">Accounts</a></li>
            <% end %>
            
            <% if policy(:group).index? %>
                <li class="sidebar-item"><a class="sidebar-link" href="/groups">Groups</a></li>
            <% end %>

            <% if policy(:user).index? %>
                <li class="sidebar-item"><a class="sidebar-link" href="/users">Users</a></li>
            <% end %>
        </ul>
    <% end %>
</li>
```

## Pundit - Conditional Rendering:

```ruby
<% if policy(Note.new).show? %>
  <th>Notes</th>
<% end %>
```
*conditionally rendered based on whether the user has the permission to show notes. This is determined by policy(Note.new).show?.




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
$ git push heroku main -a appname
$ git push <remote> <local branch>:<remote branch>
$ heroku run rails db:migrate -a appname

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
heroku run bin/rails db:migrate -a affyex-devise-users
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
heroku run bin/rails console -a affyex-devise-users  
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

## AWS IAM User and S3 Bucket Setup

1. Create IAM user and grab the keys. Click Users in the left hand navigation. Add Users button in upper right hand corner.

2. Within User details, create a User name and select Provide user access to the AWS Management Console - which will give us an access point to make changes or address issues. In this instance I selected "I want to create an IAM user"

3. Go ahead and create without attaching a policy. We will come back to that.

4. Create the S3 bucket - Click create bucket. Name it. AWS Region matters - Currently deselecting the Block all public access setting.

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

11. Click back into the user and create the access keys that you need - choose just the cli - it's under Security Credentials - Access keys - Create Access key:<br>
Now we have what we need:

user:<br>
Access Key ID:<br>
Secret Access Key:<br>
bucket:

Remember that I have these for access as well:<br>
Console sign-in URL:<br>
User name:<br>
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

## Pushing to different remotes:

Show different remotes:
```
git remote -v
```
* that will get ypu something like this:
```
demo    https://git.heroku.com/the-showroom-demo.git (fetch)
demo    https://git.heroku.com/the-showroom-demo.git (push)
dev     https://git.heroku.com/the-showroom-dev.git (fetch)
dev     https://git.heroku.com/the-showroom-dev.git (push)
fake    https://git.heroku.com/the-showroom-fake.git (fetch)
fake    https://git.heroku.com/the-showroom-fake.git (push)
origin  https://github.com/Affygility/the-showroom.git (fetch)
origin  https://github.com/Affygility/the-showroom.git (push)
production      https://git.heroku.com/the-showroom.git (fetch)
production      https://git.heroku.com/the-showroom.git (push)
```

### Push to production
```
git push production main
```
* This will push the main branch to the production remote

### Push to demo remote
```
git push demo main
```
* This will push the main branch to the demo remote

### Push to dev remote from dev branch
```
git push dev dev:main
```
* This will push the dev branch to the dev remote<br>
* the first "dev" is the remote, the second "dev" is the branch you are pushing from and the :main is the branch you are pushing to on the remote.
---

## For reference: 

```
git push <remote> <local branch>:<remote branch>
```

---

## wordpress-plugin-update.txt


https://developer.wordpress.org/plugins/wordpress-org/ towards the bottom give you a lot of links...

https://developer.wordpress.org/plugins/wordpress-org/how-to-use-subversion/


1. First create a local directory on your machine to house a copy of the SVN repository:<br>
    $ mkdir my-local-dir-jan

2. Next, check out the pre-built repository<br>
    $ svn co https://plugins.svn.wordpress.org/remove-wp-branding my-local-dir-jan

* if this doesn't work you may need:<br>
$ brew install svn

A    my-local-dir/assets<br>
A    my-local-dir/assets/banner-772x250.png<br>
A    my-local-dir/assets/banner-772x250.psd<br>
A    my-local-dir/assets/icon-128x128.png<br>
A    my-local-dir/assets/icon-256x256.png<br>
A    my-local-dir/assets/icon.png<br>
A    my-local-dir/assets/screenshot-1.jpg<br>
A    my-local-dir/assets/screenshot-2.jpg<br>
A    my-local-dir/assets/screenshot-3.jpg<br>
A    my-local-dir/branches<br>
A    my-local-dir/tags<br>
A    my-local-dir/trunk<br>
A    my-local-dir/trunk/readme.txt<br>
A    my-local-dir/trunk/remove-wp-branding.php<br>
A    my-local-dir/trunk/uninstall.php<br>
Checked out revision 2045463.


3. move into the correct directory<br>
$ cd my-local-dir

4. Add/change the files you need. Then check to see if what you have is different:<br>
my-local-dir/$ svn stat

5. you can check the diff as well if you would like:<br>
Let’s see what exactly has changed in that file, so we can check it over and make sure things look right.<br>
my-local-dir/$ svn diff

6. If it all looks good then it’s time to check in those changes to the central repository.<br>
my-local-dir/$ svn ci -m "Changed tested up to 6.2.2"

*it asked for a user account and password here. There is something else in the notes in case you get an error.

If the commit fails because of ‘Access forbidden’ and you know you have commit access, add your username and password to the check-in command.

my-local-dir/$ svn ci -m 'Adding first version of my plugin' --username your_username --password your_password


$ svn ci -m 'Updating to 6.6.1' --username your_username --password your_password --no-auth-cache

7. Tag the New Version: The svn copy command is used to create a snapshot of the current state of the trunk directory and save it as a tag.<br>
$ svn copy https://plugins.svn.wordpress.org/remove-wp-branding/trunk https://plugins.svn.wordpress.org/remove-wp-branding/tags/1.1.6 -m "Tagging version 1.1.6"

---

# Create a file

```bash
touch test/helpers/factory_helper_test.rb
```


---

# Share the knowledge. Let's build!!!
