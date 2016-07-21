# Setting up

Right now time to get started on the good stuff. First of all we are going to make sure we have everything on our system to start using rails. If you know you have ruby installed skip to step 2.

### 1) Prep

![prep](https://media.giphy.com/media/J9Sj8clG3CUFO/giphy.gif)

This tutorial assumes you have homebrew installed on your system. To check if you do run `brew -v` in your command line. If it returns a version number then you are good to go, if not follow how to install it [here](http://brew.sh/).

Next to check if you have ruby installed run `ruby -v` and once again if it does not return a version of ruby you will need to install it. This can be done by running `brew install ruby`, now go get yourself a drink (I suggest a cocktail) and wait for ruby to be installed onto your system. Run `ruby -v` again to check everything was installed nicely. If it hasn't tough... only joking just get on google you lazy, lazy person.

Next we have to check if you have your database ready for rails to store your sweet, sweet data. Rails by default uses SQlite3 but you can configure it to use others if you so please. Now, you know the drill run `sqlite3 --version` and if it does not report its version `brew install sqlite3`(get yourself another cocktail and you should be tipsy enough to tackle rails).

### 2) Intalling rails

FINALLY, now time to get ruby on dem rails.

First of all you will need to install rails with RubyGems (if you want to know more about ruby gems go [here](http://code.tutsplus.com/articles/ruby-for-newbies-working-with-gems--net-18977) and get stuck in).

```gem install rails```

Now run `rails --version` (I promise this will be the last time you have to do that) to make sure everything is fine and dandy.

[ONWARDS AND UPWARDS](part2.md)
