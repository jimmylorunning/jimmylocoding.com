---
layout: post
title: "Jekyll & Hyde"
tags:
- blogging
- jekyll
- github pages
- markdown
comments: true
---

If you're a longtime reader (as in, the 2 months that this blog has been in existence), you may have noticed some changes. That's because I just changed blogging platforms from WordPress to [Jekyll](http://jekyllrb.com/docs/github-pages/).

### Why Change?

In January, I was learning some new things (Rails, Ruby, Agile, etc.) and I had no time to customize a blog the way I liked it. Nevertheless, I needed some place to document what I've learned and connect with people. So I decided to put up a blog as quickly as possible. The only requirement was that it must take almost no time to set up. I was already familiar with WordPress, and have set up several WordPress blogs before. So I set it up, downloaded a free theme, and voila! I was in business.

Two and a half months later, I still like my blog a lot, but it looked cluttered. I started to admire a lot of the other blogs for their minimalistic beauty. The content was front and center. Most of these blogs were hosted on either Ghost, Medium, or GitHub Pages. I decided to look into these options.

### Why GitHub Pages? Why Jekyll?

[GitHub Pages](https://pages.github.com/) is hosted on GitHub. You automatically get one site per GitHub account, and when you push any changes to it, it gets updated. No further work needed! I was attracted mostly to the convenience of updating the blog where I would update my other code--in my text editor. It reminded me of the early days when the internet was just a bunch of static HTML pages, and I'd log into the server to edit my HTML files directly. On top of GitHub pages, you get Jekyll:

> GitHub Pages are powered by Jekyll behind the scenes, so in addition to supporting regular HTML content, they’re also a great way to host your Jekyll-powered website for free.

Jekyll is so cool! With it, I can write all my posts within my text editor using beautiful [Markdown](https://help.github.com/articles/markdown-basics/) instead of ugly HTML or dealing with buggy WYSIWYG interfaces! GitHub Pages and Jekyll provides all the advantages of a static site (speed, simplicity) with all the advantages of a dynamic site ([DRY-ness](http://en.wikipedia.org/wiki/Don%27t_repeat_yourself)). Every time you push the site, Jekyll generates all the static pages for you based on the templates and code you've written. So despite the fact that it's a static site, if you want to change the layout or colors or even functionality of your site, you can do it in just one place.

Jekyll works with regular HTML pages too, so I didn't have to convert all my old posts to Markdown.

Here are the other advantages of using GitHub Pages / Jekyll:

- since content is static instead of in a database, all my blog content is version controlled and backed up on GitHub
- static pages mean non-executable and secure pages! I don't have to worry about someone hacking into my blog if I didn't update to the latest WordPress release
- design-wise, it is so simple. I can do anything I want to the site, it's simply a matter of changing HTML, Markdown, and CSS files


### Setting it up

There's nothing that technically extraordinary about my set-up that I need to write a whole blog post about it. I followed [this tutorial](http://joshualande.com/jekyll-github-pages-poole/), but instead of only using [Poole](https://github.com/poole/poole), I also used a Poole theme called [Hyde](http://hyde.getpoole.com/). The difference? Poole isn't exactly a theme; it comes with all types of default settings on top of Jekyll to give you a solid foundation to build upon. Hyde, on the other hand, <i>is</i> a theme and is built on top of Poole.

The second tutorial I used was [this blog post](http://charliepark.org/tags-in-jekyll/) which helped me implement tags.

### Downsides

The only downside is that I've now lost all of the great comments you've left on my blog. I still <i>have</i> them, of course. But they are no longer on this version of the blog for everyone to see. But since I've implemented comments using [Disqus](https://disqus.com/), it will be pretty easy for you to leave comments on this site from here on out. You don't even need a Disqus account, as you can use OAuth to log in through Twitter or any of the other social networks.

### One additional note

OK maybe two. First, the related_posts method that comes with Jekyll is sorely lacking. Luckily, I was able to find [a plugin](http://www.chrisyin.com/2014/08/23/jekyll-related-posts/) for it, and since Jekyll is written in Ruby, plugins are just Ruby classes that [monkey patch](http://en.wikipedia.org/wiki/Monkey_patch) existing classes. This means that if I didn't like this plugin, I could change it without having to learn a new language.

Second, and this is the unfortunate part, GitHub Pages disables all plugins by default, for security reasons. So even though the related posts and tags plugins work fine on my local Jekyll server, it doesn't work when pushed to GitHub.

Here's the workaround: When you run Jekyll, it generates a static site. When you push to GitHub, GitHub Pages knows to run Jekyll on those files and publish the static files that it generates. But we don't want GitHub to run Jekyll for us because its version of Jekyll ignores plugins. We want to run our own Jekyll and tell GitHub to use our own statically generated pages instead!

So what we need are two repos. One to hold the Jekyll site, and one to hold our own statically generated site.

This second repo <i>must</i> be named github-username.github.io because that's how GitHub Pages knows its the repo to publish. So what I had to do was rename the current jimmylorunning.github.io repo to jimmylocoding.com. This will be the first repo mentioned above.

For the second repo, I go to GitHub and create one named jimmylorunning.github.io. I go to my local \_site folder (which is where Jekyll stores the statically generated site) and type `git init`. I add all the files, commit them, and push to jimmylorunning.github.io as its origin. From now on, whenever I make any changes to my blog, I will have to commit my jekyll files to the jimmylocoding.com repo, run `jekyll serve` or `jekyll build` (which I should run anyway, just to test my changes before pushing), then commit all my generated \_site files to jimmylorunning.github.io.