---
layout: post
title: "TwitterFitter v2.0"
tags:
- Markov chains
- APIs
- twitter
- security
- refactoring
- TwitterFitter
comments: true
---

So I decided to revisit my <a href="http://jimmylocoding.com/2015/01/12/week-3-round-up-twitter-fitter/">week 3 app</a>, TwitterFitter. At the end of week 3, it was a simple app that generated tweets based on a Twitter handle. The tweets it generated would be in the style of the Twitter account you gave it. It does this by chaining together words that often appear together. But there were a lot of things lacking in the app, so this week I revisited it and made it much better!

<a href="https://secret-brushlands-4139.herokuapp.com/">Version 2.0 of Twitter Fitter</a> has a new design (it was just a white page before), and you can now enter TWO twitter handles and the app will generate tweets based on BOTH feeds combined. Also, you can now tweet the results (it tweets from the @FitterTweets account).

Most of these enhancements were straight forward, but there were a few tricky parts:
<ol>
	<li>At first, the generated tweets appeared on the results page and when you clicked "Tweet!", it would tweet whatever was in the text field. But then I started thinking: is this a magnet for spammers? Anyone could just erase what's in that text field, type something new in, and click "Tweet!" and it would look like it was coming from the @FitterTweets account. This is a major security flaw, and even though there many ways to hide this information, like making the field uneditable and in a POST action instead of a GET action, people could still easily spoof it. So instead of sending the tweet from a form, I saved the generated tweets in a Tweet model as soon as they are generated. Then in the results page, in addition to showing the tweets in a text field, I also include a hidden field with the ID of the generated tweet (from the model). So when you click "Tweet!" you're not actually tweeting anything from the form, you're just saying "tweet this previously generated tweet with this ID". So everything that is tweeted from the account is pretty much vetted and safe (at least I hope so).</li>
	<li>My controller was getting pretty fat, and I had to look at it long and hard and figure out how to refactor it. I decided to make a Feeds class, which now lives in the lib folder. It wasn't easy breaking apart the fat methods in the controller, but I'm glad I did because it looks much cleaner this way.</li>
</ol>

### To Do

Tests! For the Feed class and for the controller. I'm not very good at writing tests before the code, but as long as I write the tests some time, that's probably better than never.

Please take a look at my code <a href="https://github.com/jimmylorunning/twitter-fitter">on GitHub</a>, and play around with it <a href="https://secret-brushlands-4139.herokuapp.com/">on Heroku</a>. Any feedback is welcome!"