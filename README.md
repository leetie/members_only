```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```

This Project was just some practice with authentication for The Odin Project. It uses the Devise gem for authentication and renders views based on whether or not users are signed in.

* Instructions for getting mailer to work on your local environment

From the Rails app root in terminal:

```

        touch .env && echo "EMAIL_PASSWORD='your_password'" >> .env && echo "EMAIL_NAME='your_username'" >> .env 

```

* Add the .env file with your email and password to gitignore!!!

```

        echo "/.env" >> .gitignore 

```

* Run bundle, fix yarn if it yells at you, and migrate DB

```
        bundle install
        yarn install --check-files
        rails db:migrate

```
* Set up action_mailer config in development.rb. In this example I am using smpt through Gmail. For this to work, you have to enable access through unsecure apps in your account security settings. 

```

        config.action_mailer.default_options = { from: "your_email@gmail.com" }
        config.action_mailer.perform_deliveries = true
        config.action_mailer.default_url_options = {:host => 'localhost:3000'}  
        config.action_mailer.delivery_method = :smtp
        config.action_mailer.smtp_settings = {
          :enable_starttls_auto => true, 
          :address => "smtp.gmail.com",
          :port => 587,
          :domain => "gmail.com",
          :authentication => :login,
          :user_name => ENV['EMAIL_NAME'],
          :password => ENV['EMAIL_PASSWORD']
        }

```

* In config/initializers/devise.rb

```

        config.mailer_sender = 'your_email@example.com'

```


