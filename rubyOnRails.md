# Ruby On Rails 🚂

### **Installation on Windows**

- Node Js
- Yarn
- Git
- Text Editor (Sublime, VS Code etc)
- Ruby Installer (Update Ruby & Rails after installation complete)
  - Update Ruby (latest Ruby installer)
  - Update Rails (~$ gem install rails)

### **Creating Rails Project**

Creating a new directory for rails project

```bash
mkdir railsproject
```

Change Current directory to railsproject directory

```bash
cd railsproject
```

Create rails project

```bash
rails new <projectName>
```

Rails project created successfully.

Now, Open rails project on text editor.

Start rails project

```bash
rails s
```

http://127.0.0.1:3000/

### **First Web Page And MVC**

#### _Gemfile_

First Look into `Gemfile`. Gemfile Allows to install defferent things into your app.

#### _app/assets_

All the CSS and Image file are present here.

#### _app/models_

Database Connection files

#### _app/view_

Web page is written in the view

#### _app/controllers_

All the Logical this are written in controllers

#### _config/routes.rb_

Handle routing

### **Creating Home Page in Rails**

First Open Bash cmd

```bash
rails generate controller home index
```

hit enter,

```bash
      create  app/controllers/home_controller.rb
       route  get 'home/index'
      invoke  erb
      create    app/views/home
      create    app/views/home/index.html.erb
      invoke  test_unit
      create    test/controllers/home_controller_test.rb
      invoke  helper
      create    app/helpers/home_helper.rb
      invoke    test_unit

```

Successfully created.

http://127.0.0.1:3000/home/index.html

### **Application Partial Links and New Pages**

_Links in rails_

```html
<!-- this is normal html -->
<a class="navbar-brand" href="#">Friends App</a>
```

This way you can links pages

```erb
<!-- this way we can link pages -->
<%=link_to 'Friends App', root_path, class:"navbar-brand"%>
```

### **CRUD Scaffold**

https://www.rubyguides.com/2020/03/rails-scaffolding/

https://guides.rubyonrails.org/active_record_migrations.html

Creating a friends table

```bash
rails generate scaffold friends first_name:string last_name:string phone:string instagram:string
```

Hit enter,

```bash
[WARNING] The model name 'friends' was recognized as a plural, using the singular 'friend' instead. Override with --force-plural or setup custom inflection rules for this noun before running the generator.
      invoke  active_record
      create    db/migrate/20231123160351_create_friends.rb
      create    app/models/friend.rb
      invoke    test_unit
      create      test/models/friend_test.rb
      create      test/fixtures/friends.yml
      invoke  resource_route
       route    resources :friends
      invoke  scaffold_controller
      create    app/controllers/friends_controller.rb
      invoke    erb
      create      app/views/friends
      create      app/views/friends/index.html.erb
      create      app/views/friends/edit.html.erb
      create      app/views/friends/show.html.erb
      create      app/views/friends/new.html.erb
      create      app/views/friends/_form.html.erb
      create      app/views/friends/_friend.html.erb
      invoke    resource_route
      invoke    test_unit
      create      test/controllers/friends_controller_test.rb
      create      test/system/friends_test.rb
      invoke    helper
      create      app/helpers/friends_helper.rb
      invoke      test_unit
      invoke    jbuilder
      create      app/views/friends/index.json.jbuilder
      create      app/views/friends/show.json.jbuilder
      create      app/views/friends/_friend.json.jbuilder

```

_`Push migration into the databse`_

```bash
rails db:migrate
```

after pushing migration into database you can see a schema file in **`db/migrate/schema.rb`**

we can find friend pages in `views/friends`

### **Style App with Bootstrap**

### **Devise User Management**

Ruby Gem Org

https://rubygems.org/

Go to this website and search `devise`

```gem
gem 'devise', '~> 4.9', '>= 4.9.3'
```

Add this line to Gemfile, and run the command `bundle install`, hit enter

```bash
bundle install
```

https://github.com/heartcombo/devise

Next, you need to run the generator
```bash
rails generate devise:install
```
At this point, a number of instructions will appear in the console. Among these instructions, you'll need to set up the default URL options for the Devise mailer in each environment. Here is a possible configuration for `config/environments/development.rb`:
```bash
$ rails generate devise:install
      create  config/initializers/devise.rb
      create  config/locales/devise.en.yml
===============================================================================

Depending on your application's configuration some manual setup may be required:

  1. Ensure you have defined default url options in your environments files. Here
     is an example of default_url_options appropriate for a development environment
     in config/environments/development.rb:

       config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }

     In production, :host should be set to the actual host of your application.

     * Required for all applications. *

  2. Ensure you have defined root_url to *something* in your config/routes.rb.
     For example:

       root to: "home#index"

     * Not required for API-only Applications *

  3. Ensure you have flash messages in app/views/layouts/application.html.erb.
     For example:

       <p class="notice"><%= notice %></p>
       <p class="alert"><%= alert %></p>

     * Not required for API-only Applications *

  4. You can copy Devise views (for customization) to your app by running:

       rails g devise:views

     * Not required *

```
**Depending on your application's configuration some manual setup may be required:**

**1. Ensure you have defined default url options in your environments files.**

Here is an example of default_url_options appropriate for a development environment
     in `config/environments/development.rb`:
       config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
     In production, :host should be set to the actual host of your application.
     *Required for all applications.*

```bash
config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }
```
Copy this, `config.action_mailer.default_url_options = { host: 'localhost', port: 3000 }` and past it into `config/environments/development.rb` or `config/environments/production.rb` before `end`.

**2. Ensure you have defined root_url to *something* in your config/routes.rb.**

For example:
       root to: `"home#index"`
     *Not required for API-only Applications*

**3. Ensure you have flash messages in app/views/layouts/application.html.erb.**

 For example:
       <p class="notice"><%= notice %></p>
       <p class="alert"><%= alert %></p>
     *Not required for API-only Applications*

**4. You can copy Devise views (for customization) to your app by running:**
```bash
rails g devise:views
```
**5. Then we create MODEL**

The generator will install an initializer which describes ALL of Devise's configuration options. It is imperative that you take a look at it. When you are done, you are ready to add Devise to any of your models using the generator.

In the following command you will replace MODEL with the class name used for the application’s users (it’s frequently User but could also be Admin). This will create a model (if one does not exist) and configure it with the default Devise modules. The generator also configures your config/routes.rb file to point to the Devise controller.
```bash
rails generate devise MODEL
```
we create user table

example, `rails generate devise user`

**6. After creating migration Push the migration**

Push migration using this command
```bash
rails db:migrate
```
Note, If you get some routing error on `delete method` then paste this code in `routes.rb`

```rb
  devise_scope :user do  
    get '/users/sign_out' => 'devise/sessions#destroy'     
  end
```
in `config/routes.rb`
```rb
Rails.application.routes.draw do
  devise_for :users
  
  devise_scope :user do  
    get '/users/sign_out' => 'devise/sessions#destroy'     
  end
  resources :friends
  # get 'home/index'
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Defines the root path route ("/")
  # root "articles#index"
  root 'home#index'
  get 'home/about'
end
```
