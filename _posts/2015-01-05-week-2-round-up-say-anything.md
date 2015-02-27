---
layout: post
title: "Week 2 Round Up: say-anything"
tags:
- apps
- associations
- authentication
- devise
- learning
- rails
- ruby
- testing
---

Week 2 of An App Per Week is over! It was tough and I got a little behind. I planned to implement the <a href="http://docs.railsbridge.org/intermediate-rails/">RailsBridge intermediate curriculum</a>, plus testing and some extra features. Here is what I was able to accomplish:
<ul>
	<li>all the basic features specified in the curriculum</li>
	<li>extra features:
<ul>
	<li>deleting posts</li>
	<li>profile page with a list of posts (not replies yet)</li>
	<li>custom user fields: username and favorite movie fields instead of just the default e-mail and password</li>
	<li>some testing</li>
	<li>fancy bootstrap styling</li>
</ul>
</li>
</ul>
What I wasn't able to finish this time around:
<ul>
	<li>Testing! I got some testing done, but it was taking too long to do for features that I wasn't sure how to build out, so I figured I'd write the tests after the fact. So that's still on my to do list...</li>
	<li><a href="https://github.com/intridea/omniauth">Omniauth</a> -- being able to log in through Twitter, Github, FB, etc. I might do this tomorrow</li>
	<li>fancier post markup, or maybe even a wysiwyg edit window would be nice (I'm sure there's a gem, right?)</li>
</ul>
<a href="https://aqueous-sierra-5780.herokuapp.com/">And here it is!</a> All in all, I am pretty happy with it. The major things I learned:
<ul>
	<li><a href="https://github.com/plataformatec/devise">Devise</a> was a pleasure to work with. It's relatively easy to set up and gave me a lot of standard user stuff out of the box. I really liked it. It wasn't even that hard to add custom fields (username, favorite movie, etc.) to the user profile. At one point I had to look into the Devise source on github to figure something out, but even that wasn't too hard because it's pretty well organized.</li>
	<li><a href="http://guides.rubyonrails.org/routing.html#nested-resources">Nested resources</a>. I implemented replies the non-nested way, then re-read the hints section, and figured out that nested resources was the way to go with this kind of feature. Nested resources gives you an url that corresponds to the relationship of your models. So because replies belong to posts, you can have a URL like post/5/replies. It doesn't matter as much in my finished product since I ended up embedding replies within posts anyway.</li>
	<li>Dealing with <a href="http://edgeguides.rubyonrails.org/action_controller_overview.html#strong-parameters">strong parameters</a></li>
	<li><a href="http://guides.rubyonrails.org/association_basics.html">has\_many / belongs\_to</a> association -- I've dealt with this before, but this was my first time working with them outside of a tutorial, so it sunk in more</li>
	<li>The <a href="http://guides.rubyonrails.org/asset_pipeline.html">asset pipeline</a> -- had to figure some assets out and so I read a little bit about this, but I need to read way more when I have time</li>
</ul>
### Unsolved problems:

When testing, I had to run some tests as a signed in user and some as signed out. How do I do this? After some reading, I figured out that I had to stub the authentication in the specs. I followed <a href="https://github.com/plataformatec/devise/wiki/How-To:-Stub-authentication-in-controller-specs">these directions</a> and put the ControllerHelpers module in spec/support/controller\_helpers.rb as well as the accompanying config. But it kept complaining: "undefined method sign\_in".

After a certain amount of googling, head scratching, and generally going nowhere, I finally just moved the module into my spec file. Not graceful, but I had to keep going. If you have any ideas about this let me know.

Also while trying to test user authentication related things, I figured out how to fake sign in/out inside of rails console and get to the user object:

{% highlight ruby %}
ApplicationController.allow_forgery_protection = false
app.post('/users/sign_in', {"user"=> {"username"=> "jimmy", "password"=> "mypassword"}})
cu = app.controller.current_user
{% endhighlight %}

I find it super useful to be able to try things out in the console. It's probably where I learn the most.

Another problem. In Michael Hartl's Rails Tutorial book, he was able to set up a `has_many` / `belongs_to` association between User and Micropost. And because this was set up, he was automatically able to write something like this:

{% highlight ruby %}
User.micropost.some_method()
{% endhighlight %}

However, I set up my app in a very similar way. My `:post belongs_to :user` and my `:user has_many :posts`. But I couldn't get this to work. I always got "undefined method posts". My workaround was simply to use plain old Posts object and pass it the `current_user` when needed.

Another thing I learned... where and `find_by_???` methods are not interchangeable:

{% highlight ruby %}
x = User.where(id: 3) # returns ActiveRecord::Relation
y = User.find_by_id(3) # returns User
x.id # error, no id method
y.id # returns the user id correctly
x.each { block } # works
y.each { block } # error, no each method on User
{% endhighlight %}

There are many other smaller things I could blog about, but I don't have time and you probably don't have patience. I may write up a few of these smaller issues later if I feel like it.

### Next Week

Any ideas? I'm thinking about writing an app that would involve pulling from some API... maybe the Twitter API and doing something with the data. Stay tuned.