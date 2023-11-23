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
#### *Gemfile*
First Look into `Gemfile`. Gemfile Allows to install defferent things into your app. 

#### *app/assets*
All the CSS and Image file are present here.

#### *app/models*
Database Connection files

#### *app/view*
Web page is written in the view
#### *app/controllers*
All the Logical this are written in controllers

#### *config/routes.rb*
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
*Links in rails*
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
*`Push migration into the databse`*
```bash
rails db:migrate
```
after pushing migration into database you can see a schema file in **`db/migrate/schema.rb`**

we can find friend pages in `views/friends`

### **Style App with Bootstrap**
