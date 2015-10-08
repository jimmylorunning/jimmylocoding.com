---
layout: post
title: "A Laravel-Rails Dictionary"
tags:
- laravel
- php 
permalink: a-laravel-rails-dictionary 
comments: true
---

Sometimes you struggle for a long time to learn something, and you don't feel like you've really made much progress. But when you learn something new and somewhat similar to it, the learning curve is greatly reduced. It's a great feeling. That's what happened with me recently when I tried to learn Laravel for a work project. Because of the time I spent with Rails, it made learning Laravel so much easier! Laravel is a MVC framework for PHP very similar to the way Rails is for Ruby.

Because a lot of the concepts are similar, I created a chart of equivalent syntaxes that could get someone who is already familiar with Rails started in Laravel much quicker. 

| Laravel                                                     | Rails                                       |
|-----------------------------------------------------------  |-------------------------------------------  |
| composer install (or php composer.phar install)             | gem install                                 |
| composer create-project laravel/laravel your-project-name   | rails new your-project-name                 |
| composer.json                                               | Gemfile                                     |
| composer.lock                                               | Gemfile.lock                                |
| packagist.org                                               | rubygems.org                                |
| blade                                                       | erb or haml                                 |
| Eloquent                                                    | ActiveRecord                                |
| php artisan serve                                           | rails serve                                 |
| php artisan make:controller PagesController                 | rails generate controller Pages             |
| php artisan make:model Article                              | rails generate model Article                |
| php artisan make:migration add\_column\_to\_table           | rails generate migration AddColumnToTable   |
| php artisan migrate                                         | bundle exec rake db:migrate                 |
| php artisan tinker                                          | rails console                               |
| php -a                                                      | irb                                         |
| php artisan route:list                                      | bundle exec rake routes                     |

Overall, I really love Laravel. In fact, I think I like Laravel more than Rails (while I still like Ruby way more than PHP). There are obviously a lot of similarities to Rails, and you can't take away the fact that Rails changed the landscape and paved the way for Laravel. But there are also many things that are different as well, and make Laravel really shine. I'll try to write about those in a future post. 

Meanwhile, here are a few shout-outs:

- [Udemy's RoR Tutorial: Learn from Scratch](https://blog.udemy.com/ruby-on-rails-tutorial-learn-from-scratch/) I was turned onto this tutorial by Molly Elizabeth, who works at Udemy. I haven't gone through the tutorial myself, but it looks like a very good resource if you're just starting out in Rails. If you try it, let me know what you think.
- [PHP: The Right Way](http://www.phptherightway.com/) a very good 10,000 feet birds eye view of the somewhat gnarly PHP scene. It's not the prettiest language, but recent iterations have been able to salvage it a bit. This site is a super useful resource if you have to do PHP, and it covers best practices, how to organize your code, pitfalls you can avoid, etc.
- [Laracast](https://laracasts.com/) these video tutorials are clear, concise, and very useful when learning Laravel. Jeffrey is a really good teacher and communicator, and he covers the topics at just the right speed. Highly recommended.
- [Craft CMS](https://buildwithcraft.com/) I've been working with ExpressionEngine for a while, and while very powerful, it is still a bit frustrating and inflexible at certain things. Craft was designed by people who used to design plugins for ExpressionEngine, so they know all the painpoints and they have been able to create a really amazing product. Check it out if you're looking for a really well thought-out CMS.
- [DigitalOcean](https://www.digitalocean.com/?refcode=af3f55393a0b) paired with [ServerPilot](https://serverpilot.io/). Setting up your stack can't be simpler than with these two tools working together. DigitalOcean provides the servers on the cloud and ServerPilot gives you a really nice control panel to configure them. And the interface of both sites are simple and elegant, and much less headache-inducing than AWS.
- ... speaking of which, if you have to deal with [AWS](https://aws.amazon.com/), here's a really great resource: [AWS in Plain English](https://www.expeditedssl.com/aws-in-plain-english). It comically translates AWS services into what they should have been named in the first place. Nice intuitive names rather than EC2 or S3.