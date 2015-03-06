---
layout: post
title: "Week 4: Oracle of Bacon and other stuff"
tags:
- APIs
- Code Club
- CodeNewbie
- Ember.js
- JavaScript
- Kevin Bacon
- legacy code
- Level UP Rails
- meetups
- nokogiri
- tests
- Typo
- validation
- XML
comments: true
---

This week, I started my <a href="https://www.edx.org/course/engineering-software-service-part-2-uc-berkeleyx-cs169-2x">SaaS Part 2</a> class... I decided to just do the SaaS homework in place of my weekly app. The homework involves the <a href="http://oracleofbacon.org/">Oracle of Bacon</a> website, where you can find the <a href="http://en.wikipedia.org/wiki/Six_Degrees_of_Kevin_Bacon">Bacon Number</a> of any actor. It also shows you the linkages along the way... for instance:
<blockquote>Sean Connery
was in Der Name der Rose with
Ron Perlman
who was in Balto with
Kevin Bacon.</blockquote>
So Sean Connery has a Bacon Number of 2. The website also has an API. You can ask it for a connection between any two actors, and it will return that information (if any) in XML format.

Our job was to connect to the API and write a wrapper around the XML that gets returned. Our wrapper would basically detect if the returned value was valid, and if so, it would make it into an object that we can query. The SaaS class (both part 1 and part 2) has been really good at stressing agile practices, and this homework was no different. We were to pair program over Google Hangouts on Air. The tests were written for us in this assignment, but we needed to get them to pass.

<strong>Firsts:</strong>
<ul>
	<li>writing an abstraction layer / wrapper</li>
	<li>handling XML with <a href="https://rubygems.org/gems/nokogiri">nokogiri</a></li>
	<li>writing my own validation method (our class included ActiveModel's Validation methods, so it got a lot of behavior for free)</li>
</ul>
<strong>Homework 2</strong>

I finished early so I started on homework 2, which is all about refactoring and working with legacy code. We have to clone an existing repo, the <a href="https://github.com/saasbook/typo">Typo blogging platform</a> and fix a bug in it, but first we have to write tests around the bug. Here's a Google Hangout video of me trying to work out the first part:

<iframe width="560" height="315" src="https://www.youtube.com/embed/tvMJCXvf7ds" frameborder="0" allowfullscreen></iframe>

I was really confused about half an hour in because I had made some changes and my tests passed, and I was really happy with it. But then all of a sudden all the tests failed even though I hadn't changed anything since the last time! I finally figured out that I had to run bundle exec rake db:test:prepare. Although I still don't understand why... I hadn't changed the database at all since the last time I ran the tests. I thought I only had to run that command when I changed the database.

<strong>Other things:</strong>

<a href="https://leveluprails.com/">Level UP Rails</a> is a project designed to give a common baseline to engineers on the <a href="http://words.steveklabnik.com/rails-has-two-default-stacks">Rails Prime</a> stack. It was designed by Joseph Mastey to help onboard new hires to the Enova team. But guess what? It's also open source, so I'm taking it even though Enova hasn't offered me a job yet (what are they waiting for? Fools!). So far I've finished the first lesson of the first course, which mostly focuses on server commands and borderline sysadmin skills, many of which have intimidated me in the past. I just started on the second section entitled 'Basic Ruby'. The overall course description is: "Learn to build and test a complete Ruby on Rails application. This isn't a basic intro: you will finish with some serious ruby chops." I can't wait to have serious chops! I'm documenting my progress on <a href="https://github.com/jimmylorunning/level-up-rails">github</a>.

Also this week I participated in two <a href="http://www.codenewbie.org/code-club">Code Club</a> sessions (through the <a href="http://www.codenewbie.org/">CodeNewbie</a> website). They were great! It's sort of like hanging out with cool people while learning a lot. Each session has a host, but the host doesn't necessarily have to know any more about the subject than anyone else. It's basically like a study session; everyone is there to learn and encourage others to learn. The first one I took was on <a href="http://javascriptissexy.com/javascript-variable-scope-and-hoisting-explained/">Javascript Variable Scope</a> where I got to hang out with <a href="http://bloggytoons.com/">Saron</a> and <a href="http://cynthialanel.com/">Cynthia</a>. The second one I took was <a href="http://thetechcofounder.com/getting-started-with-ember-js-using-ember-cli/">an introduction to Ember.js</a> with <a href="http://jonathanyeong.com/">Jonathan</a> and Yaw.

And ... and ... and ... I went to a <a href="http://www.meetup.com/atlantaruby/">Ruby Meetup</a> on Wednesday (the featured talk was on Angular JS). I met a lot of nice people. And then I got home just in time to participate in <a href="http://www.codenewbie.org/chat">#CodeNewbie Twitter Chat</a>! I didn't feel like I did that much this week, but I guess I did!