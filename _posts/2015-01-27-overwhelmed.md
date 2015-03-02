---
layout: post
title: "Overwhelmed!"
---

I didn't finish my app this week! I tried to do too much. But here's what I did finish:

### My SaaS homework

I talked a little about this last week. We had to refactor and fix some bugs in a legacy codebase (Typo). I figured out that I had to run bundle exec rake db:test:prepare if I want to run Rspec after I run Cucumber. For some reason Cucumber messes up the database. Then, the biggest road block was writing tests and then getting them to pass. I ended up overly fixing it... and the autograder was not giving me credit because it was expecting this form to be submitted to an edit action when in fact it's really a new action, so I had changed it to new in order to be more accurate.

### My portfolio

I got it into my head that I can bang out <a href="https://github.com/jimmylorunning/portfolio">a portfolio webpage</a> real quick. But quickly got stuck in a rut. Had a hard time setting up gulp. And it's still working weirdly. When I run "gulp sass" it might more might not give me an error. Then if I change some tab inside the gulpfile... or if I just run "gulp" without any task specified, then run "gulp sass" again, it may or may not just work. It's so erratic that I was tearing my hair out trying to figure it out. But I finally just gave up and wrote a shell script that does the same thing. Maybe I'll try grunt next time.

### My app

<a href="https://github.com/jimmylorunning/om-nom-nom">Started but didn't finish it</a>. <span style="line-height: 1.5;">But the original idea for it was pretty good. It's basically going to be a social network for yoga lovers. Yoga lovers can add yoga poses. And then they can create yoga routines by putting poses together in a certain order. Yoga poses that are shared publicly can be added on other people's routines. There will be many other features, but that's the core functionality. For example, when a routine is done, you can play it back and it will guide you through the routine in real time.</span>

I was basing yoga poses/routines off of Youtube's videos / playlists. So I might work on it in the future. I feel like I need to at least learn a front end javascript framework before attacking this because there are pages that would be really awkward without loading things dynamically on the page without reloading the page.

### Level UP Rails

made some progress on this curriculum. Although I started over-engineering one of the exercises, so my time was all sucked up in that. You can see it here. It's still not finished (there are some improvements I am planning) but it's basically a program that reads in two comma separated value files (CSV) of dinosaur data and creates an object that you can query. For example, you can say dinosaur.big to get a list of all the big ones. or dinosaur.bipeds. The cool thing is that you can also chain them together in any order like dinosaur.big.bipeds to get an intersection. You can see <a href="https://github.com/jimmylorunning/level-up-exercises/tree/master/dino_catalog">my code here</a> (comments and suggestions welcome)

### My work

I'm still doing some freelance work for the library. Did a lot of refactoring of code this past week and that was oddly satisfying.

### Meetups

went to a Ruby meetup where everyone just socialized and worked on their projects at a coffeeshop. It's not the main meetup they do (with an official speaker) but the other one where it's more just like casual hanging out.