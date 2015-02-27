---
layout: post
title: "Hiding my API keys"
---

### Problem: I don't want to expose API secret keys, but I still want to be able to commit my changes and push to github.

### Solution:
<ul>
	<li>Install <a href="https://github.com/laserlemon/figaro">figaro</a> gem</li>
	<li>set environment variables in config/application.yml
{% highlight ruby %}
my_api_key: 'weoi23urow234jerow67jerjerjwejr'
{% endhighlight %}
</li>
	<li>make sure .gitignore ignores config/application.yml</li>
	<li>in the initializer code, (for my week3 app, I put this in config/initializer/twitter.rb) use `ENV['my_api_key']` instead of hardcoding the api key</li>
	<li>after deploying to heroku, run this command to set heroku's env variables
> figaro heroku:set -e production
</li>
</ul>