---
layout: post
title: "SaaS Legacy Homework 2: Lessons Learned"
tags:
- Capybara
- Cucumber
- legacy code
- SaaS
- tdd
- testing
- Typo
---

This week's <a href="https://www.edx.org/course/engineering-software-service-part-2-uc-berkeleyx-cs169-2x">SaaS homework</a> has been the most elaborate so far. As the instructors explain in the lectures, after teaching the class for a while, they asked some of the top software companies what one thing they wish graduates of computer science programs would learn before entering the workforce. The overwhelming answer was "how to work with legacy code". So even though at first they had no idea how to teach this, they set out to do so in this class. And thus we have legacy homework 1 and 2 (last week and this week).

Instead of working on a new custom app, we are given an existing app (the Typo blog platform) that has a long history, sometimes messy code, and spotty test coverage. Last week we were asked to fix a bug in it. This week, we had to add a new feature!

Our feature in a nutshell: add the ability to merge two articles into one. The body of the new article will be a concatenation of the two previous articles. The title and author will be from one of the two articles. And the comments of all previous articles (if any) will now be comments of this article. Only administrators can merge articles. All other users will not see the option at all.

<a href="images/typo_merge_feature.png"><img src="images/typo_merge_feature-sm.png" alt="picture of what the typo merge feature should look like" /></a>

I spent a LONG time on this homework. Around 15 hours. The hardest part was writing the tests. That shouldn't be a surprise because writing the test is always the hardest part for me! I am still very new to Rspec and TestUnit syntax, and spend so long trying to figure out exactly how to phrase things. But I'm proud to say that I stuck to it this time and wrote all the tests before writing the actual code (except for the view and some skeleton methods so it didn't throw method-not-found errors--basically I had to get it to the point where the tests failed for the <em>right</em> reasons and not because it couldn't find some method).

First I wrote the Cucumber integration tests for the happy path only. Then I wrote the unit test for the controller. It was at this time that I realized I was planning to put way too much logic in the controller. So instead of putting all the tests there, I just wrote a few to make sure the controller was asking the model for that information. Then I had to write a bunch of unit tests for the model. At last I allowed myself to write some actual code, which didn't take long.

Then at the very end I wrote the cucumber integration tests for the sad paths. The one thing that was SUPER helpful was using the debugger gem and plain old rails console (with the --sandbox option) while writing the tests, because it helped me figure out exactly how to get to certain elements in order to test them.

Even though I could have knocked out the homework in probably less than half the time without testing, I really liked the practice. It was hard but satisfying. There isn't a more satisfying and empowering feeling than when you can get all your tests passing AND you haven't even looked at your app in the browser yet with your own eyeballs... but you know it's working! This is so different than the way I used to program.

I also feel like testing frees up my brain from worrying about every little bit of my application. If what I'm doing now will break something else, then I'll know about it soon enough (if I wrote my tests right). So all I have to do now is concentrate on writing whatever little bit I'm working on now, instead of trying to keep the entire app in my head and worry about not breaking anything else.

A few SPECIFIC things I learned:
<ul>
	<li>in the controller, the redirect_to method does not redirect immediately. The rest of your method will continue running unless you specifically say "return" after redirecting</li>
	<li>if you want to redirect inside of a helper method (instead of a main controller action), then set that helper method as a before_filter of your main action method or else it won't redirect (return will just return to your main action method which will continue running)</li>
	<li>when using Capybara to find the xpath of an input element with a certain id=“name”, use 'input[@id=“name”]' rather than 'input#name'</li>
	<li>use text_field_tag to create a simple input element with a normal name like "merge_with".. I was trying to use the text_field helper method and it kept making names like "merge[with]". This is because text_field is "tailored for accessing a specified attribute (identified by method) on an object assigned to the template" -- so it's really good if you want to create input fields that correspond to your model, but if not, then it may be too complicated for your needs</li>
	<li>use "tables" to set up a bunch of values in Cucumber. I've used them in previous apps but they always seemed like a mystery to me. But this time I played around with them in the debugger gem. You can <a href="http://www.ruby-doc.org/gems/docs/d/davidtrogers-cucumber-0.6.2/Cucumber/Ast/Table.html">find out more here</a>.</li>
	<li>I tried really hard to keep my git commits small, task based, and meaningful this time, which meant I had to do a few git things I've never done before like adding specific lines instead of entire files. I really like the idea of my git history telling the story of my code. And also having the ability to revert any single change without messing anything else up.</li>
	<li>There's probably a lot of other things but these are the easy ones that I can remember off the top of my head</li>
</ul>
And if you're curious about the code I wrote for this week's homework, it's <a href="https://github.com/jimmylorunning/typo">up on Github</a>.