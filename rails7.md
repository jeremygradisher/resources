## Notes on Rails 7

### Asking Chat-GPT-4 about this:
When i create a Ruby on Rails 7 application, I do it like this:
```
rails new app-name --css=bootstrap --javascript=esbuild --database=postgresql
```

How would you describe this?

### Chat-GPT-4's response descripbing Rails 7:
The command you've shared is used to generate a new Ruby on Rails (RoR) application with specific options.

1. ```rails new app-name```: This is the basic command to create a new Rails application. app-name is the name of your new application.

2. ```--css=bootstrap```: This option tells Rails to use Bootstrap as the CSS framework for the application. Bootstrap is a popular CSS framework used for designing responsive and mobile-first websites.

3. ```--javascript=esbuild```: This option instructs Rails to use esbuild for handling JavaScript in the application. esbuild is a fast JavaScript bundler and minifier.

4. ```--database=postgresql```: This option sets PostgreSQL as the database for the application. PostgreSQL is a powerful, open-source object-relational database system.

So, to put it all together, this command will create a new Ruby on Rails 7 application with the specified name, using Bootstrap for the CSS framework, esbuild for JavaScript bundling and minification, and PostgreSQL as the database.

### Asking Chat-GPT-4: Doesn't this have something to do with import maps?

Yes, you're correct. With Rails 7, the default JavaScript bundler has been switched from Webpacker to esbuild, which is used in conjunction with import maps. Import maps are a new standard that allows you to use JavaScript modules in a simpler and more performant way.

When you specify ```--javascript=esbuild``` in your Rails 7 new application command, it sets up esbuild and import maps for you. With import maps, you can import JavaScript modules directly using their names, instead of specifying their full paths or relying on node_modules.

So in the context of your command, using ```--javascript=esbuild``` not only enables faster JavaScript bundling with esbuild but also facilitates the use of import maps, simplifying the way you include and manage JavaScript dependencies in your Rails 7 application.

---

## Notes about Rails 7:

Rails 7 introduced a new way to deal with assets via import maps and they also introduced a new way to run your app locally, the new bin/dev file. It’s not installed by default(yet) unless you create a new app with the -css option or it’s installed later on when you run the css:install command.

Explanation: https://www.nickhammond.com/learning-to-love-bin-slash-dev-in-rails-7/

## Additional Notes about Rails 7:

Yes, there are several important things you should know about Rails 7. First, it requires Ruby 2.7.0+ to run, but Ruby 3.0+ is preferred. This is a significant update since previous versions of Rails were compatible with older Ruby versions​1​.

Next, the asset pipeline library, Sprockets, is no longer a default dependency in Rails 7. If your application still needs to use Sprockets, you'll have to add sprockets-rails to your Gemfile manually​1​.

There were also several changes to Active Record, the ORM layer in Rails. For example, transaction blocks now rollback when they return earlier than expected. This helps to avoid committing incomplete transactions, which was a problem in previous versions​1​. Also, when merging conditions on the same column, the latter condition now consistently replaces the earlier condition​1​.

There have been several removals and deprecations in Rails 7 in different areas like Active Model, Active Support, and Active Job​1​.

I also found that Rails 7 has made improvements to Webhooks, offering a standardized way to register and verify them. However, I wasn't able to gather more details about other notable features in Rails 7 due to time limitations.

It's important to check the official Rails 7.0 Release Notes and other reliable resources to get comprehensive information about the changes and new features in Rails 7.