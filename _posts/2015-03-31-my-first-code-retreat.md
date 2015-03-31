---
layout: post
title: "My First Code Retreat!"
tags:
- code retreats
- learning
- game of life
permalink: my-first-code-retreat
comments: true
---

This past weekend I went to my very first code retreat! "What is a code retreat?" you may be asking yourself. Don't worry, I didn't know what it was either until very recently. Here's an intro from the event's sign up page:

> Coderetreat is a day-long, intensive practice event, focusing on the fundamentals of software development and design. By providing developers the opportunity to take part in focused practice, away from the pressures of 'getting things done', the coderetreat format has proven itself to be a highly effective means of skill improvement. Practicing the basic principles of modular and object-oriented design, developers can improve their ability to write code that minimizes the cost of change over time.
>
> More specifically,  individuals are are grouped into teams of two and each team “solves” a common problem, 'The Game of Life'.  There are 6 sessions throughout the day and for each session the groups are reorganized and the code deleted.  After each session there are session reflections to help with the  internalization of lessons.

It's basically a day of learning and exploring with awesome people and no judgment. So pretty much the best thing ever.

The event I went to was hosted at [Big Nerd Ranch](https://www.bignerdranch.com/) and lead by [Kylie Stradley](http://kyfast.net/) and [Stafford Brooke](http://srbiv.github.io/), and also sponsored by [Mandrill](https://mandrill.com/) and [Mailchimp](http://mailchimp.com/).

After a breakfast of gourmet donuts, Kylie introduced us to the problem we were to solve for the rest of the day: [The Game of Life](http://en.wikipedia.org/wiki/Conway%27s_Game_of_Life). The game explores the complexities that arise from a set of very simple rules. And because of its simple rules, it makes for a great software design exercise.

The point was not to write working code, but to explore different possible ways of writing it. The fun came in the variation of solutions, and the explorations of the pros/cons of each.

It reminded me of an exercise I gave myself when I was first exploring the beauty and subtlety of writing. The exercise was simple: pick any sentence and write it 20 or 30 different times using different sentence structures, wording, punctuation or grammar without changing the primary meaning. For example, the sentence "The quick brown fox jumps over the lazy dog." could also be written as:

> Being quick, the brown fox jumps over the lazy dog.

> The lazy dog was jumped over by the quick brown fox.

> Because the fox is lazy, the quick brown fox jumps over him.

> The fox (quick and brown) jumps over the lazy dog.

> Over the lazy dog the quick brown fox jumps!

(This was the type of fun I had in high school hahaha) The other part of this exercise, and arguably the more important part, is to take each sentence and analyze it for how it differs from the original in terms of tone, voice, connotation, emphasis, meaning, etc. I say this is the more important part of the exercise because reflection leads to awareness and understanding of what each tweak does to the original. This kind of obsession eventually lead me to become a poet, so if this looks fun to you: beware! A life of agonizing over words awaits you.

Code retreat reminded me of doing this same exercise, but with code! We were given just enough time to formulate a solution, without enough time to finish or perfect it. That way, we weren't expected to finish anything, and so we could concentrate on issues of design.

We paired with a new person for each session, and by the end of the day we would have paired with almost everybody in the room. For each session, we were also expected to practice test driven development (this made it even harder to complete in 45 minutes, but added the dimension of very intentional forethought and planning).

Many of us had never tackled the game of life problem before, so the first session was basically dedicated to getting comfortable with the problem space. But with each subsequent session, we were given new constraints. Imagine if doing the sentence exercise above, I had given myself rules for each sentence, like "must use a passive verb" or "must have a dependent clause". These constraints stretched us and made us think about the problem in a new way.

We had a diverse group of experts and beginners. Rather than try to make everyone program in one language, we were encouraged to learn from each other. Thus, I got to program with a C# programmer, an iOS developer, and someone with JavaScript and Go experience, as well as people who didn't have much programming experience (but rich experiences in other fields).

At the end of each session, we were encouraged to delete our code. This re-inforced the idea that the code was not the goal, but what we learned from designing it. After each session, we also reconvened with the larger group to talk about what we learned and how we approached the problem and share ideas. This part was super helpful and eye-opening, because some teams came up with very unexpected and inventive designs.

One of the things we talked about was whether the logic of the cell living or dying should go into the board or the cell. There were good arguments on both sides, and at the end of the day I had attempted it both ways and am _still_ undecided about which way is better. As with everything, it's a matter of understanding tradeoffs.

### Looking Back

If I could do code retreat all over again, I would try not to design the entire game every time. Instead, figure out what the constraint is getting me to reconsider, and only design/program that part. For example, we had a constraint where we couldn't use if statements. The method that it would affect most would be the main logic of the program--whether a cell lives or dies.

But we ended up on several tangents, spending a lot of time talking about other aspects of the program, like different ways of seeding it, or how to find neighboring cells and such. And because we only had 45 minutes, I didn't feel like I got enough time to really explore the main issues of that exercise. If I could do it again, I would have just hardcoded a method that returned the same number of neighbors every time, just so that I didn't have to think about that part, and could focus on the really good parts of that exercise.

### Looking Forward

Coderetreat was a great experience, and I loved meeting people in the spirit of learning. Everyone was kind and helpful, and the ideas we shared will continue to help me in my everyday work. But this is just the beginning:

Global Day of Coderetreat is November 15! I'm already looking forward to the next one, and so should you. There is [a website](http://coderetreat.org/) where you can look for coderetreats in your area. But if there isn't one, you should organize one! The website provides all the details you'll need to organize your very own.