To add an avatar attachment to your User model in Rails 7, you can use the Active Storage framework. Here's how you can set it up:




1. Active Storage Setup: Make sure that Active Storage is set up in your Rails application. If it's not, you can install it with the command:
```
bin/rails active_storage:install
```
This will generate a migration file. You can then run:

```
bin/rails db:migrate
```

2. Model Setup: In your User model (app/models/user.rb), you need to specify that each User has an attached avatar. The User model should look like this:
```ruby
class User < ApplicationRecord
  # Other associations, validations etc.

  has_one_attached :avatar
end
```

3. Controller Setup: In your UsersController (or RegistrationsController if you're using Devise), you need to allow the avatar parameter. For a UsersController it would look something like:
```ruby
class UsersController < ApplicationController
  # Other methods like show, index, etc.

  def user_params
    params.require(:user).permit(:email, :password, :avatar)
  end
end
```

4. Form Setup: Now, you need to set up your form to accept file uploads. You can do this in your form view (app/views/users/_form.html.erb or app/views/devise/registrations/edit.html.erb if you're using Devise). Here's a simplified example:
```ruby
<%= form_for @user do |f| %>
  <!-- Other fields like email, password etc. -->

  <%= f.label :avatar %>
  <%= f.file_field :avatar %>

  <%= f.submit %>
<% end %>
```

5. Displaying the Avatar: Finally, you can display the avatar anywhere in your views using the image_tag helper:
```ruby
<%= image_tag(@user.avatar) if @user.avatar.attached? %>
```



---

Also - Delete that Avatar:

1. Controller Method
In your UsersController, add a method delete_avatar:

```ruby
class UsersController < ApplicationController
  # ...

  def delete_avatar
    @user = User.find(params[:id])
    @user.avatar.purge
    redirect_to @user, notice: 'Avatar was successfully deleted.'
  end

  # ...
end
```
2. Add Route
Add a new route for the delete_avatar action in your routes file (config/routes.rb):

```ruby
resources :users do
  member do
    delete :delete_avatar
  end
end
```
This will create a route that you can use with a DELETE request, like: /users/:id/delete_avatar












