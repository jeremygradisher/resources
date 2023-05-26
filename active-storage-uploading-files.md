active-storage-uploading-files.md

https://guides.rubyonrails.org/active_storage_overview.html

1. Image analysis and transformations also require the image_processing gem. <br>
Uncomment it in your Gemfile, or add it if necessary:<br>
(Uncommented line 53).
```
# Use Active Storage variants [https://guides.rubyonrails.org/active_storage_overview.html#transforming-images]
gem "image_processing", "~> 1.2"
```
* run ```bundle install```


2. Setup - Active Storage uses three tables in your application’s database named active_storage_blobs, active_storage_variant_records and active_storage_attachments. After creating a new application (or upgrading your application to Rails 5.2), run ```bin/rails active_storage:install``` to generate a migration that creates these tables. Use ```bin/rails db:migrate``` to run the migration.



3. I did end up needing to add these manually:
Set the following key-value pairs (replace XXX with your actual credentials):

AWS_ACCESS_KEY_ID: XXX<br>
AWS_SECRET_ACCESS_KEY: XXX<br>
AWS_REGION: XXX<br>
AWS_BUCKET: XXX<br>

4. Tell Active Storage which service to use by setting Rails.application.config.active_storage.service. Because each environment will likely use a different service, it is recommended to do this on a per-environment basis. To use the disk service from the previous example in the development environment, you would add the following to config/environments/development.rb:
```
# Store files locally.
config.active_storage.service = :local
```

To use the S3 service in production, you add the following to config/environments/production.rb:
```
# Store files on Amazon S3.
config.active_storage.service = :amazon
```

To use the test service when testing, you add the following to config/environments/test.rb:
```
# Store uploaded files on the local file system in a temporary directory.
config.active_storage.service = :test
```

5. Add the aws-sdk-s3 gem to your Gemfile:
```
gem "aws-sdk-s3", require: false
```
* run ```bundle install```

Further info on AWS integration: https://docs.aws.amazon.com/sdk-for-ruby/v3/developer-guide/setup-config.html

6. See if you have the credentials file in your home directory:
```
EDITOR="code --wait" rails credentials:edit
```
amend the file save it and close it.

You can double check with ```rails console``` and:
puts Rails.application.credentials.dig(:aws, :access_key_id)
puts Rails.application.credentials.dig(:aws, :secret_access_key)

7. Make sure config/storage.yml has what you need:
```
amazon:
   service: S3
   access_key_id: <%= Rails.application.credentials.dig(:aws, :access_key_id) %>
   secret_access_key: <%= Rails.application.credentials.dig(:aws, :secret_access_key) %>
   region: us-east-1
   bucket: affyexdeviseusersbucket
```

https://guides.rubyonrails.org/active_storage_overview.html#attaching-files-to-records

8. To add an avatar attachment to your User model in Rails 7, you can use the Active Storage framework. Here's how you can set it up:

Active Storage Setup: Make sure that Active Storage is set up in your Rails application. If it's not, you can install it with the command:
```
bin/rails active_storage:install
```
This will generate a migration file. You can then run:

```
bin/rails db:migrate
```

9. Model Setup: In your User model (app/models/user.rb), you need to specify that each User has an attached avatar. The User model should look like this:
```ruby
class User < ApplicationRecord
  # Other associations, validations etc.

  has_one_attached :avatar
end
```

10. Controller Setup: In your UsersController (or RegistrationsController if you're using Devise), you need to allow the avatar parameter. For a UsersController it would look something like:
```ruby
class UsersController < ApplicationController
  # Other methods like show, index, etc.

  def user_params
    params.require(:user).permit(:email, :password, :avatar)
  end
end
```

11. Form Setup: Now, you need to set up your form to accept file uploads. You can do this in your form view (app/views/users/_form.html.erb or app/views/devise/registrations/edit.html.erb if you're using Devise). Here's a simplified example:
```ruby
<%= form_for @user do |f| %>
  <!-- Other fields like email, password etc. -->

  <%= f.label :avatar %>
  <%= f.file_field :avatar %>

  <%= f.submit %>
<% end %>
```

12. Displaying the Avatar: Finally, you can display the avatar anywhere in your views using the image_tag helper:
```ruby
<%= image_tag(@user.avatar) if @user.avatar.attached? %>
```


13. 











