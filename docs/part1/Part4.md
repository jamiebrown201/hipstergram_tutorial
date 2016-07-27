# Adding a post

### 1) Your first hipster post

Before we get going lets manage some expectations because nothing is more exciting than managing some expectations. Before we are able to post any of our pictures of our food and coffee we are just going to post a nice simple message, more twitter.

Navigate to your views in `app/views/posts` and we can now add a useless button that will, when it grows up be a your button to create a new post. So on the page add a button (you may delete the original statement but you should note it down and remember it) a simple text stating that there are no posts:

```
No new posts
<button type="button" href="#">New Post</button>
```

### 2) Creating a model

So that we can make posts we are going to need a model. Models are Ruby classes and they talk to the database, store and validate data, perform the business logic and generally do the heavy lifting. We going to use a generator again to make our model:

```
bin/rails g model Post message:string
```

So with this command we ordered rails to make a post model and with a message attribute. Like  I mentioned above this will handle all the back end magic to make our posts be persisted in a database and viewable forever more!

### 3) Migrate, migrate , migrate.

So now we have a lovely model set up but somethings up. Book up your server and try to navigate to the home page. UH OH, its broke! Read through the error and see what is up....

So there is alot of red but also some mention of migrations. So migrations are:

```
Migrations are a convenient way to alter your database schema over time in a consistent and easy way. They use a Ruby DSL (Domain specific language) so that you don't have to write SQL by hand, allowing your schema and changes to be database independent. You can think of each migration as being a new 'version' of the database. A schema starts off with nothing in it, and each migration modifies it to add or remove tables, columns, or entries. Active Record knows how to update your schema along this timeline, bringing it from whatever point it is in the history to the latest version. Active Record will also update your db/schema.rb file to match the up-to-date structure of your database.
```

So basically we need to run a migration so the model we just generated in rails so that it can make it actually exist in the database. Right so how do we run a migrations I hear you ask:

```
rake db:migrate
```

and with that one simple command rails runs of and makes you a perfect sqlite3 database 'posts' with a message field.

### 4) WOW, Much progress, such learning

So finally it is now time for us to actually get our posts displaying on our homepage. First of all we need to navigate to the controller so that when we are on our homepage we have access to our posts. So go back to our posts controller change the index method:

```
def index
@posts = Post.all
end
```

So what this will do is make the instance variable `@posts` available in your index view from this we can do what ever we want with it. So lets do just that, navigate to your index view and through the dark arts we now have access to our posts.

How we will be doing that is through the magic of erb. Like I mentioned earlier erb gives us a way of embedding ruby code into or front end so that we can do all sorts of cool stuff:

```
<% if @posts.any? %>
  <% @posts.each do |post| %>
    <h2><%= post.message %></h2>
  <% end %>
<% else %>
  <h1>No posts yet!</h1>
<% end %>

<button href="#">Add a restaurant</button>
```
So as you can see here we have a normal ruby if else statement but with the added `<%` and `<%=`. These are just ways of the erb templating engine to be able to identify where the ruby code begins and when it finishes. The difference between the version with the equal sign and the version without is a tag with an equals sign indicates that enclosed code is an expression and that the renderer should substitute the code element with the result of the code (as a string) when it renders the template. Tags without the equals sign denote that the enclosed code is a scriptlet. Each scriptlet is caught and executed and the final result of the code is then injected in to the output at the point of the scriptlet.

Now wont you look at that? cool right! But alas with great power comes great responsibility it very easy to get carried away at put loads of logic in our front end. This is bad news, DON'T DO IT! ok? You want to try and keep your views handling mostly just displaying this is all part of the [separation of concerns principle](http://deviq.com/separation-of-concerns/). A further part of this is making sure you do not refer to the model directly in the views, you will want to put it in an [instance variable](http://www.rubyist.net/~slagell/ruby/instancevars.html) like we did in our controller and refer to that in the view..

Brilliant so boot up your rails server and take a look at what has happened. You should see the message that you have no posts being displayed. But we dont have a way of adding posts... yet.

### 5) WOW, Much progress, such learning


### 6) Summary

Ok so we have done a lot and things may be a little fuzzy, so now is a good time to introduce the RAILS CONSOLE. The rails console is a tool that you can use to
