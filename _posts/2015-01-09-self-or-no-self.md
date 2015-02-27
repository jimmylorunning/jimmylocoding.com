---
layout: post
title: "self or no self"
---


Ruby is sometimes very confusing. For example, when you call an instance method within the same class, you can do so with or without `self`... it's optional:

{% highlight ruby %}
instance_method # works from inside the class
self.instance_method # also works from inside the class
other_object.instance_method # works from outside the class
{% endhighlight %}

However, if the method is a setter method, <a href="http://www.rubyfleebie.com/use-self-explicitly/">you <em>must</em> use self</a>. The reasoning behind this is that Ruby doesn't know whether `instance_method` is an instance method or a local variable, and the `self` gets rid of that ambiguity. Let's call this rule A.

{% highlight ruby %}
instance_method = 42 # error
self.instance_method = 42 # works
{% endhighlight %}

However, <a href="http://stackoverflow.com/questions/4293215/understanding-private-methods-in-ruby">private methods can't use self</a>. Let's call this rule B. The reasoning behind this is that private methods cannot be called with an explicit receiver, even if `self` is that receiver.

{% highlight ruby %}
self.private_method # error
private_method # works
{% endhighlight %}

What happens when rule A butts head with rule B?

{% highlight ruby %}
private_method = 42 # violates rule A - error
self.private_method = 42 # violates rule B - but works!
{% endhighlight %}

Apparently in this case, the second line is the one that's allowed. <a href="ttp://devblog.orgsync.com/2013/05/20/private-and-protected-they-might-not-mean-what-you-think-they-mean/">This blog post</a> explains it very clearly:
<blockquote>When using a setter in Ruby we're supposed to use an explicit receiver like `self`. Here we have a private method that doesn't allow an explicit receiver. We appear to have reached an impasse. <strong>In this case it turns out Ruby breaks its own rule.</strong></blockquote>
Before I found this, I was trying to get around the impasse by doing jenky things like this:

{% highlight ruby %}
private_method=(42)
{% endhighlight %}

I was surprised this wasn't a bigger topic, but then <a href="http://heartmindcode.com/2013/04/25/private_accessors_in_ruby/">I read this article</a> about how private and protected methods aren't even used that much in Ruby!
<blockquote>For the most part, we just... don’t [write private methods].</blockquote>
The following is from the book I'm reading, <a href="http://www.poodr.com/">Practical Object Oriented Design in Ruby</a> by Sandi Metz:
<blockquote>Users of a class can redefine any method to public regardless of its initial declaration. The private and protected keywords are more like flexible barriers than concrete restrictions. ... Using them sends two messages:
<ul>
	<li>You believe that you have better information today than programmers will have in the future</li>
	<li>You believe that those future programmers need to be prevented from accidentally using a method that you currently consider unstable</li>
</ul>
These beliefs may be correct but the future is a long way off and one can never be certain... many perfectly  competent Ruby programmers omit them and instead use comments or a special method naming convention (Ruby on Rails, for example, adds a leading '\_' to private methods) to indicate public and private parts of interfaces.</blockquote>
I don't know what I feel about all this yet, but I might skip over writing private methods for now just because it makes things much easier for me immediately.