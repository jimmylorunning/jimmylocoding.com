---
layout: post
title: "What I Learned Building Only the Models for an App"
tags:
- models
- associations
- shoulda
- polymorphic associations
- single table inheritance
permalink: what-i-learned-building-models
comments: true
---

Many books and tutorials are designed around building out one feature from the ground up and then moving on to the next one. While I admire that kind of workflow where you focus on creating working tangible features, I also noticed that for almost every feature, the programmer would have to touch the model, controller, and view. That kind of moving back and forth makes it hard to really understand the structure of the app, at least for me. So I decided that for my next app, I was going to do an experiment. 

Instead of developing each feature, I developed all the models up front. This allowed me to really think about the data structure behind my app and how each part interacts with the whole. I also aimed to do test driven development, by writing tests for each model and their associations before moving onto the next model. The downside of this approach is that by the end of this experiment, I still didn't have one tangible feature, at least not from the user's standpoint. And of course designing the models up front doesn't mean I won't have to change them later when I realize the constraints have changed. But I think it's a good learning experiment, allowing me to not worry about the controllers or views at all, and just focus in on how to connect all the different pieces. 

### My App

I love the site [Goodreads](http://www.goodreads.com). It's a social network around books. At the core of the app are the following features:

#### Around Books
- users have shelves and can create new shelves and can add books to their shelves
- users can read books and update the status of what they've read
- users can review and rate books

#### Around Users
- users can friend each other creating a 2 way relationship
- a user can follow another user, creating a 1 way relationship
- users can like or comment on another user's reviews or statuses

There's *much* more to it, but those are the very core features. Since I love Goodreads and there are a few things I'd like to change about it, I decided to make my next app be a Goodreads clone. I think part of the reason I could design the complete model first is because I'm so familiar with the existing site and know beforehand exactly how each part is supposed to work. That said, I did make a few changes in my version, which I will talk about later.

### The End Result

I'm going to start by showing you what I ended up with, and then explain some of the choices I made. The amazing [Wendy Beth](http://wendybeth.ghost.io/) told me about the [Rails ERD](https://github.com/voormedia/rails-erd) gem which will "allows you to easily generate a diagram based on your application's Active Record models". Here is my ERD (entity relationship diagram):

<img src="{{ site.imageurl }}minigr_models.png" alt="Model Diagram" />

What follows isn't a complete step-by-step tutorial on what I did, but rather a few highlights (or lowlights, depending on how you see it) of my experience building this out.

### Associations and Shoulda

A huge part of this exercise was figuring out how to work with rails associations. You know, those `has_many` and `belongs_to` calls that magically link up your models so that you can simply call `school_of_the_sun.editions` instead of having to write out complicated sql joins (that's [the last book I read and loved](https://www.goodreads.com/review/show/781026074) by the way). I won't go over the basic associations, as I think the [documentation](http://guides.rubyonrails.org/association_basics.html) is not bad. However, I will talk about some of the more tricky associations that I ended up implementing.

One challenge in terms of associations is testing them. Luckily, there is a gem out there for that. It's called [Shoulda](https://github.com/thoughtbot/shoulda) and it's really easy to use. I first learned about it in Michael Hartl's Rails Tutorial, but I quickly forgot about it. 

One of the challenges when reading that book without any prior experience was that it presented all these different concepts together, so that I didn't understand which commands were part of Rails and which were part of Ruby. Similarly, what is part of RSpec and what has been added to it by Shoulda? Over time, much of this has cleared up.

Here are a few examples of Shoulda at work:

{% highlight ruby %}
Spec.describe Book, type: :model do
  it { should have_many(:authors).class_name('Author') }
  it { should have_many(:editions).class_name('Edition') }
  it { should have_many(:copies).class_name('Copy') }
end
{% endhighlight %}

### Implementing Tags

Goodreads doesn't have tags. Instead they have shelves. But it's a bit confusing, because they have two types of shelves. The first type are exclusive shelves. A user must add a book to one and only one exclusive shelf. Examples of exclusive shelves are "read", "to read", and "currently reading". A book cannot be both "to read" and "currently reading" because that doesn't make sense.

The second type of shelf is just a shelf that acts more like a category. You can add a book to as many non-exclusive shelves as you'd like. Examples would be "travel", "romance", "books with blue covers", etc.

Lastly, each user defines his or her shelves, and gets to set which shelves are exclusive and which non-exclusive.

When it came to implementing my solution, I thought having the same name and 2 different behaviors was confusing. So I created two separate models. One is the shelf model, which acts like Goodread's exclusive shelves. And one is the tag model, which acts more like tags do on the rest of the web (and kind of like Goodread's non exclusive shelves).

Shelves were the simpler of the two. A shelf `has_many` copies (the concept being that you don't own a book, you own a copy of a book). And a copy `belongs_to` a shelf.

Tags were a little more complicated. I ended up creating an intermediate Taggings model so that each copy can have many tags and each tag can have many copies. This [Railscast tutorial](http://railscasts.com/episodes/382-tagging) explains what I did pretty well.

### Aliasing a has\_one relationship

I want reviews to `have_one` reviewer, but the name of the class is Reader not Reviewer. And it has to go through several relationships to get there. I could have settled for review.reader, but I wanted my names to be more accurate. After much experimentation, here's what I ended up with:

{% highlight ruby %}
has_one :reviewer, through: :copy,
                   source: :reader,
                   class_name: "Reader",
                   foreign_key: :reader_id
{% endhighlight %}

### Likes and Comments

A reader can like a review or a following or a status. A reader may also comment on reviews and statuses. I would like to have just one Like model and one Comment model instead of several different ones tied to different tables. For example, I could do ReviewLike, FollowLike, and StatusLike. But that's so inelegant, and whenever I want to add the capability to like something else, I would have to write a whole new model and migration for it.

Instead, I decided to use [polymorphic associations](http://guides.rubyonrails.org/association_basics.html#polymorphic-associations). It's a great solution for this situation, I think! Basically a polymorphic association allows you to use one model (Like in this case) and bind it with two or more models through a foreign key *and* a type (which tells the model which model to bind it to in each case). So when I like a review, that type will be "Review" and when I like a status that type will be "Status". Comments work the same way.

### Reader Statuses vs. Copy Statuses

On Goodreads, a user can enter a general status update. This is like "Hey I'm having a great day." and is not tied to a book. But they can also enter a status update on a book. This is like "Hey I'm reading 'Wittgenstein's Nephew' by Thomas Bernhard and I'm on page 47 and here are my thoughts...". The second type of status update is tied to a user's book (copy model in my case) and can include a page number to show progress. Other than that, the two statuses are the same.

So I really wanted an elegant solution here instead of creating two separate models. I read up on [single table inheritance](http://eewang.github.io/blog/2013/03/12/how-and-when-to-use-single-table-inheritance-in-rails/) which seems like a really cool use of inheritance to not repeat code. I wasn't sure this would be the right solution because copy status has two extra data fields. But I liked the idea that a copy status is basically just a status with extra functionality, so therefore it inherits from it. So I decided to implement it.

And I'm glad I did--now I understand why STI is the *wrong* solution in this case. I had to rollback and start again. The problem in this case is that CopyStatus not only has 2 extra fields, but one of them is a foreign key field that references copy whereas Status has no foreign key fields. This represents not only difference in data, but also difference in behavior. While I think it could still work, this has gone from a somewhat elegant solution to a total hack. It's even less elegant than the two models I started with.

### Friendships

While following is a one-way relationship (you can follow someone but they do not have to follow you back), friendships are a two-way relationship. You both agree to be friends.

If we imagine a friends table with "friender" and "friendee" as the two columns, and a friendship is basically any two users that are referenced in this table then...

This poses an interesting problem in that when I say Demetrius.friends I want the model to return all of Demetrius's friends. That means everyone in the friender column where friendee is Demetrius *and* everyone in the friendee column where Demetrius is the friender.

Luckily, I found a [Railscast](http://railscasts.com/episodes/163-self-referential-association) that showed two ways of doing this. One uses a gem and one a self-rolled solution. I avoided the gem because the self-rolled version seems just as simple and easier to customize (less dependencies, too).

For my purposes, I also have to think about the fact that a friend has to request someone to be their friend, then that person has to agree before the friendship becomes official. I added an `accepted` field to the table for this purpose. I'm not sure if this will be sufficient or if I'll have to create a separate FriendRequest model, but I will find out soon when I try to implement it.

### Alternatives?

So these are the basic models and relationships between them that I've come up with. Could they be different? Are there better ways of modelling this? Probably, but I won't find out until I implement it. (Feel free to give your thoughts in the comments section)

One thing I thought of that could be different is whether or not I needed the copy model. What if I got rid of it? Well then the problem becomes, how does one Edition `has_many` Readers (through shelves) as well as one Reader `has_many` Editions? Someone suggested a `has_and_belongs_to_many` association here as a possible solution.

Another thing I'm wondering is if I could get rid of the rating and review classes. Since they belong to copy, could I just have `rating` and `review` as fields in Copy? Do I lose something from doing that?

### Other Things Learned

I learned that I really like thinking about models and focusing on them exclusively, at least in the beginning. I also made some big mistakes that I will not make again. One is that the model-database connection is not automatically in sync. When I was testing this I was running into some weird problems. I finally figured out that just because I updated something from one model does not mean all the other models have updated from that same set of data in the database automatically. I have to reload the model in order for it to fetch that data again from the database.

### The Future

I definitely want to start building out the controllers and views and start making this actually work and look good! My models aren't complete. There are others I need to add eventually, as well as many fields and things like validation that I need to add. But for now it is a good big-picture where I can get started building. There will likely be many challenges in the future and my models will probably have to change and adapt, but that's all part of the process!
