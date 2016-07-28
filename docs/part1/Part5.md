# [Buttons](https://www.youtube.com/watch?v=VCLxJd1d84s)

### 1) Adding a new post

Ok so we want our button to lead us to a new post page where we can write our post. So what did we do before when we wanted to create a new page, we created a new method in our controller.

```ruby
def new
end
```
 then we need to create our view file in our views folder `/app/views/posts/new.html.erb`. Put something on the page so you can test the route is working. Before we can test if its working we need to set up our routes again. So go to your routes file `config/routes.rb` and you can add anouther route ``get '/posts/new', to: 'posts#new'``. So thats all well and good but think of when our hipstergram site is getting more and more complex adding each route can get pretty messy pretty quickly. So rails gives us a way of clearing this up. In our routes delete the two get statements and replace it with:

 ```ruby
Rails.application.routes.draw do
  resources :posts
  root 'posts#index'
end
 ```

The resources command will creates seven different routes in your application with just one command so now we are pretty much covered on our posts controller. So boot up your server and test it out SORTED.

Right now its time to set up our form on our new page so we can create our posts. So go back to your new view and add in a form:

```ruby
<%= form_for Post.new do |f| %>
  <%= f.label :message %>
  <%= f.text_area :message %>
  <%= f.submit %>
<% end %>
```
lovely run up your server go to `http://localhost:3000/posts/new` and try submitting a form. Uh oh error, give it a read and see if you can figure out what we need to do next....

### 2) CREATE

Correct!!!(or incorrect I have no way of knowing). We are going to need to make a create method in our posts controller called `create` so run along and do that. Done? Good. However we are not done because we need to put some logic in this method so that when we press our submit button it will store our posts in the database:

```ruby
def create
  Post.create(params[:post])
end
```
Looking fly, but as always we aren't quite done yet, soz.

_If you are a bit confused at this whole params malarky do some googling and come back and try and make sense of it._

### 3) Only accepting the correct params

If you try running your server and submitting your message you get a big error `:ForbiddenAttributesError `. So why is this? Well apparently back in the 1900s(what?! I dont know it was before I ever started working on rails) when we accepted the params like we just did it means anyone can send whatever the hell they want, resulting in security flaws that aren't too pretty.

Right so lets sort this mess out. So in our controller we need to explicitly state what params we are willing to accept when someone submits the form. We can do this by adding a new private method to our controller (if you haven't covered private methods follow this link [here](http://culttt.com/2015/06/03/the-difference-between-public-protected-and-private-methods-in-ruby/))

```ruby
private

def post_params
  params.require(:post).permit(:message)
end
```
So this method basically tells rails to only accept the params of `message`. Now all we need to do is call that in our create method instead of our params and we are ready to go.

```ruby
def create
  Post.create(post_params)
  redirect_to '/'
end
```  

Nearly there all we need to do is link our home page button to our form to create a post and we are all done with posts. So change the blank button earlier to this

```ruby
<%= button_to 'new post', '/posts/new', method: :get %>
```
Now run up your rails server and bask in the glory of what you have created!

[ONWARDS AND UPWARDS](Part6.md)
