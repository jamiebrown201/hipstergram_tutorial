# Hello world

### 1) Controller and view?

Now time to get down and dirty with rails. In the grad tradition of programming we are going to first make sure everything is in order by displaying hello world to the screen.

We first of all need to create a controller. What is a controller I hear you ask:

```A controller's purpose is to receive specific requests for the application. Routing decides which controller receives which requests. Often, there is more than one route to each controller, and different routes can be served by different actions. Each action's purpose is to collect information to provide it to a view.```

Now that may seem a bit confusing but it will become much clearer as we work through this and if you go back to this after a couple more steps things should become much clearer.

Now what in the hell are these view things?

```A view's purpose is to display this information in a human readable format. An important distinction to make is that it is the controller, not the view, where information is collected. The view should just display that information. By default, view templates are written in a language called eRuby (Embedded Ruby) which is processed by the request cycle in Rails before being sent to the user.```

Slightly easier to understand but its basically html and css that displays your information and makes it look all pretty and stuff.

### 2) Creating your controller

Now we are going to create them, but don't worry rails generators are once again going to do all the work for you run:

```
bin/rails g controller posts
```
_g is short for generate and helps us be even more lazy_

This command will create a lovely new file in `app/controllers` as well as some other files that we don't need to concern ourselves with at the moment.

Now navigate to `app/controllers/home.rb`. You will be greeted with a blank class entitled `postscontroller` in this class you are going to want to add a ruby method called index that will let the controller know what exactly it needs to do (bear with me). Then in that method we are going to just raise an error with 'hello world'. Ok bit weird but stick with it. Your class should look like this now:

```ruby
class PostsController < ApplicationController
  def index
    raise 'Hello world!'
  end
end
```
Now load up your server `rails s` (that is the last time I will be showing you that so note it down godammit). Visit `http://localhost:3000/posts` and you will see a horrible error page BUT it will say hello world at the top. GREAT SUCCESS :thumbsup:

### 3) Creating your view

Now its time to get some good old fashioned HTML on your app. If you navigate yourself to `app/views/posts` you will now want to create a file in that directory called `index.html.erb`. Now you probably know what html is but what on earth is this 'erb' madness? Well simply erb is a templating engine that lets you embed ruby code into your html page (erb stands for embedded ruby). As you will see this will help us out a lot but for now we can ignore it and just write in html. So in the index page you just created add a simple but true statement:

```html
<h1>Jamie Brown is the BEST</h1>
```

Now go back to your controller and delete the raise statement we created earlier leaving the method blank (rails will know that the index that you just created matches up with your controller).

### 4) Routing!

Now before we get ahead of ourselves there is one more tiny thing we need to do to let rails know when to display our posts page. We want our posts page to be the homepage, and if you go there now it is still that stupid welcome page. Navigate to `config/routes.rb` and open it up.

This is your routes rile which holds entries that tells rails how to connect incoming requests to controllers and actions. First of all you will want to add `get '/posts/index', to: 'posts#index'` to the class. This will mean that when you visit http://localhost:3000/posts/index we will get our page.

Additionally you can edit this file to add `root 'posts#index'` at the bottom of the class. What this command will do is display your homepage when you visit http://localhost:3000/.

### 5) Summary

So we have done a bit here so take some time to remind yourself what we did and maybe google bits you aren't too familiar with.

[ONWARDS AND UPWARDS](Part4.md)
