---
layout: post
title: "Week 3 Round Up: Twitter Fitter&#8212;the tweet generator!"
tags:
- twitter
- APIs
- apps
- gems
- Markov chains
- POROs
- SaaS
- testing
---

So there's still a lot more work I want to do on my week 3 app <a href="https://secret-brushlands-4139.herokuapp.com/">Twitter Fitter</a>. But the general idea is there--it's a <a href="http://en.wikipedia.org/wiki/Markov_chain">Markov generator</a>. You type in a twitter handle, and it spits back a generated tweet (or tweet-like string) that is in the style of that user. (Try @DATABASE\_HULK, @StephenAtHome, @BarackObama, or @kimkardashian) Part of the app/week project is that I want to learn something new each time. So what did I learn this week?

### Firsts:

Well, this was my first app where I had to connect to another service (in this case it was the <a href="https://dev.twitter.com/rest/public">Twitter API</a> through the <a href="https://github.com/sferik/twitter">Twitter gem</a>) and also the first app where I wrote my own POROs (plain old Ruby objects) inside of Rails. In fact, this was barely a Rails app. It doesn't even have a model. It's mostly just a single page that connects to Twitter and then runs the MarkovChain object that I wrote for it. I also obviously learned a lot about Markov generators and how they work. (I knew about them generally but never thought about how to write one before)

### Testing:

I was able to write <a href="https://github.com/jimmylorunning/twitter-fitter/blob/master/spec/lib/markov_chain_spec.rb">tests for my MarkovChain object</a>. I'm pretty proud of this. But I haven't written tests for the actual controller code yet (which is currently very messy).

### To do:

As always there are still many things I want to do to improve it:
<ul>
	<li>Needs major styling. Looks really ugly right now. I want it to look good!</li>
	<li>I want you to be able to retweet the generated tweets. Maybe it will retweet it from a custom account, maybe @TwitterFitter</li>
	<li>I want to make a gem out of the MarkovChain object. There are already similar gems out there (and my algorithm isn't all that unique), but I think it would be a learning experience to create my own gem.</li>
	<li>Tweak my generator code. Currently it's pretty simple, and the results are either pretty funny / nonsensical or else they're pretty boring (like almost word for word of an existing tweet rather than a mix-match of different tweets)</li>
</ul>

### Challenges:

<ul>
	<li>writing the <a href="https://github.com/jimmylorunning/twitter-fitter/blob/master/lib/markov_chain.rb">actual Markov generator</a>, and making it perform okay as well as be open to modification in the future if I wanted to change the way it works later. For example, I thought it would be cool if I could pass it a lambda so that it picks the next word based on running that lambda code. The default is just random, but maybe someone would want to tweak it themselves without having to go into my code.</li>
	<li>figuring out how to call private / public methods within my class, and whether or not to even use private methods. <a title="self or no self" href="http://jimmylocoding.com/self-or-no-self/">Here's a blog post I wrote</a> about this topic.</li>
	<li>tweaking the generator. When I use a prefix length of 2, I get back text that's very similar to the original text, so much so that it's kind of boring. If I set it to 1, I get back things that are sometimes very nonsensical. I decided on 1. But it would be nice to come up with a different algorithm so that it's between totally nonsensical and completely boring.</li>
	<li>figuring out how to include my ruby object in the lib directory and have rails auto include it. I was not naming my file correctly, so it didn't include it when autoloading! Took me some extra googling to figure out why.</li>
	<li>writing test code. I'm not sure I did it right, but testing code that's supposed to be random was also kind of tricky. I had to <a href="http://ruby-doc.org/core-2.2.0/Random.html#method-c-srand">seed the generator</a> with values so that it would be predictable/testable.</li>
	<li>using the Twitter gem. I had to figure out how to give it my API keys and secrets without exposing it through github. I wrote a <a title="Hiding my API keys" href="http://jimmylocoding.com/hiding-my-api-keys/">blog post about this here</a>.</li>
</ul>

### Next week(s):

I've mentioned taking the incredibly helpful <a href="https://www.edx.org/course/engineering-software-service-uc-berkeleyx-cs169-1x">edX.org SaaS class</a> (Software as a Service) before. Well, <a href="https://www.edx.org/course/software-service-uc-berkeleyx-cs169-2x">part 2 of the class</a> has just started, so instead of continuing with my own apps, I will be doing the SaaS homework apps every week for the next few weeks. It's only a few weeks, and there's not a homework for <em>every</em> week, so it won't be taking over this project completely, but its presence will definitely be felt. I will still be blogging about my discoveries, though! Hope you'll keep reading.