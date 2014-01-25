[![Build Status](https://travis-ci.org/DamageStudios/ringmaster.png?branch=master)](https://travis-ci.org/DamageStudios/ringmaster)
[![Coverage Status](https://coveralls.io/repos/DamageStudios/ringmaster/badge.png?branch=master)](https://coveralls.io/r/DamageStudios/ringmaster)
[![Dependency Status](https://gemnasium.com/DamageStudios/ringmaster.png)](https://gemnasium.com/DamageStudios/ringmaster)
[![Code Climate](https://codeclimate.com/github/DamageStudios/ringmaster.png)](https://codeclimate.com/github/DamageStudios/ringmaster)

### Overview
Ringmaster is a tool for Release Management Risk Mitigation. It allows release engineers to take a deterministic approach to release management.
* [Ringmaster Overview](https://github.com/DamageStudios/ringmaster/blob/master/docs/Overview.md)
* [How to Contribute Code](https://github.com/DamageStudios/ringmaster/blob/master/docs/Contributing_Code.md)
* [ToDo List](https://github.com/DamageStudios/ringmaster/blob/master/docs/ToDo.md)

### Getting Started

#### Use RVM
We recommend using [rvm](https://rvm.io), the Ruby Version Manager, to create a project-specific gemset for the application.

#### Gems
Here are the gems used by the application: 
* [Devise](http://github.com/plataformatec/devise) - authentication and user management
* [figaro](https://github.com/laserlemon/figaro) - configuration framework
* [simple_form](http://simple-form.plataformatec.com.br/) - forms made easy
* [high_voltage](https://github.com/thoughtbot/high_voltage) - rails engine for static pages

These gems make development easier:
* [better_errors](https://github.com/charliesome/better_errors) - helps when things go wrong
* [quiet_assets](https://github.com/evrone/quiet_assets) - suppresses distracting messages in the log
* [rails_layout](https://github.com/RailsApps/rails_layout) - generates files for an application layout
* [rpsec-rails](https://github.com/rspec/rspec-rails) - testing framework for rails 3.x and 4.x

Front-end framework:
* [bootstrap-sass](https://github.com/thomas-mcdonald/bootstrap-sass) - Bootstrap for CSS and JavaScript

#### Install the Required Gems
You should run the `bundle install` command to install the required gems on your computer:

<pre>
$ bundle install
</pre>

You can check which gems are installed on your computer with:

<pre>
$ gem list
</pre>

Keep in mind that you have installed these gems locally. When you deploy the app to another server, the same gems (and versions) must be available.

#### Configuration File
The application uses the [figaro gem](https://github.com/laserlemon/figaro)  to set environment variables in the __config/application.yml__ file. The __.gitignore__ file prevents the __config/application.yml__ file from being saved in the git repository so your credentials are kept private. 

You can add any credentials to the file __config/application.yml__:

```
# Add account credentials and API keys here.
# This file should be listed in .gitignore to keep your settings secret!
# Each entry sets a local environment variable and overrides ENV variables in the Unix shell.
# For example, setting:
# GMAIL_USERNAME: Your_Gmail_Username
# makes 'Your_Gmail_Username' available as ENV["GMAIL_USERNAME"]
# Add application configuration variables here, as shown below.
#
GMAIL_USERNAME: Your_Username
GMAIL_PASSWORD: Your_Password
ADMIN_EMAIL: user@example.com
ADMIN_PASSWORD: changeme
```

All configuration values in the __config/application.yml__ file are available anywhere in the application as environment variables. For example, `ENV["GMAIL_USERNAME"]` will return the string “Your_Username”.

If you prefer, you can delete the __config/application.yml__ file and set each value as an environment variable in the Unix shell.

For the Gmail username and password, enter the credentials you use to log in to Gmail when you check your inbox. 

Set values for `ADMIN_EMAIL` and `ADMIN_PASSWORD` for a user that is created when the database is seeded. You will be able to log in to the application with these credentials.

#### Database Seed File
The __db/seeds.rb__ file initializes the database with default values. To keep some data private, and consolidate configuration settings in a single location, we use the __config/application.yml__ file to set environment variables and then use the environment variables in the __db/seeds.rb__ file.

```
# This file should contain all the record creation needed to seed the database with its default values.
# The data can then be loaded with the rake db:seed (or created alongside the db with db:setup).
#
# Examples:
#
#   cities = City.create([{ name: 'Chicago' }, { name: 'Copenhagen' }])
#   Mayor.create(name: 'Emanuel', city: cities.first)
# Environment variables (ENV['...']) can be set in the file config/application.yml.
puts 'DEFAULT USERS'
user = User.find_or_create_by_email :email => ENV['ADMIN_EMAIL'].dup, :password => ENV['ADMIN_PASSWORD'].dup, :password_confirmation => ENV['ADMIN_PASSWORD'].dup
puts 'user: ' << user.email
```

You can change the administrator email, and password in this file but it is better to make the changes in the __config/application.yml__ file to keep the credentials private. If you decide to include your private password in the __db/seeds.rb__ file, be sure to add the filename to your __.gitignore__ file so that your password doesn’t become available in your public GitHub repository.

Note that it’s not necessary to personalize the __db/seeds.rb__ file before you deploy your app. You can deploy the app with an example user and then use the application’s “Edit Account” feature to change email address and password after you log in. Use this feature to log in as an administrator and change the email and password to your own.

#### Set the Database
Once you’ve cloned the repo, prepare the database and add the default user to the database by running the commands:

<pre>
$ rake db:migrate
$ rake db:seed
</pre>

Use `rake db:reset` if you want to empty and reseed the database.

Set the database for running tests:

<pre>
$ rake db:test:prepare
</pre>

If you’re not using [rvm](https://rvm.io), the Ruby Version Manager, you should preface each rake command with `bundle exec`. You don’t need to use `bundle exec` if you are using rvm version 1.11.0 or newer.

#### Change your Application’s Secret Token

Once you’ve cloned the application directly from GitHub, it is crucial that you change the application’s secret token before deploying your application in production mode. Otherwise, people could change their session information, and potentially access your site without permission. Your secret token should be at least 30 characters long and completely random.

Get a unique secret token:

<pre>
$ rake secret
</pre>

Edit your __config/initializers/secret_token.rb__ file to add the secret token:

<pre>
RailsDevise::Application.config.secret_key_base = '...some really long, random string...'
</pre>

#### Test the App
You can check that your application runs properly by entering the command:

<pre>
$ rails server
</pre>

To see your application in action, open a browser window and navigate to [http://localhost:3000/](http://localhost:3000/).

You should see a home page with a navigation bar.

You should be able to click the navigation links for “Log in” and “Sign up.”

Stop the server with Control-C. If you test the app by starting the web server and then leave the server running while you install new gems, you’ll have to restart the server to see any changes. The same is true for changes to configuration files in the config folder. This can be confusing to new Rails developers because you can change files in the app folders without restarting the server. Stop the server each time after testing and you will avoid this issue.

### License
This program is provided under an Apache open source license, read the LICENSE.txt file for details.
