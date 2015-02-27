---
layout: post
title: How do I write tests that I don’t have to keep changing?
tags:
- testing
- tdd
- rspec
---

Sometimes I want to check to make sure my controller is sending a message to my model. For example, I want to make sure it's asking the model to return a set of results. But I don't care what message it sends:

{% highlight ruby %}
  Posts.should_receive(:all)
  get :index
{% endhighlight %}

Here I'm making sure I'm asking the model for all posts. However, I soon realized that I wanted them ordered a certain way. So I replaced the controller code to call :order instead of :all

Now I have to go back to the test and change it. But later perhaps I will want to change it again to use `:find` or `:find_all_by` or `:where` or something else altogether.

Will I have to change the test every time? What I really want is a way to say “make sure my controller sends my model a message, it doesn't matter what message it sends.” Because basically all these methods perform a similar task, and I don't care which implementation I ultimately decide on. My tests should just care about the fact that I sent the message at all, and that the model will take care of the rest. So my question is two-fold:
<ol>
	<li>Should I even be testing for this? Or is this not an important thing to test?</li>
	<li>If I should be testing for this, how do I do it so I don't have to change my test code every time?Is this possible?</li>
</ol>