---
layout: post
title: "Weekend in Review: GoodieHack"
tags:
- hackathon
comments: true
---

This weekend I went to GoodieHack, which was only my second hackathon ever (or first official one with a competitive element). Here's a description according to [their website](http://goodiehack.com/):

> Goodie Hack is an intense and high energy event where non-profits, with a focus on under-served communities, present their top operational problems to an audience of techies and non-techies who form teams to brainstorm and develop web and mobile apps to solve these problems.

The event spanned 24 hours, from Friday 7pm to Saturday 7pm, at the Google Atlanta headquarters.

I'm glad this wasn't my very first hackathon, because it may have scared me away from them all! I don't want to be overly critical, but there were definitely some areas that could be improved organization-wise, especially on the first night. For example, the room was too small to hold everyone, so a lot of people were outside and couldn't hear. Many of these people started talking over the presenter, and if you were near the back of the room, you could barely hear a thing. What's more, the PA system was not loud enough even if everyone was quiet. Then, after all the nonprofits pitched their problems, there was a mad dash to sign up for teams. Each team could only be 7 people, so it was total chaos. Some people didn't get on a team and others ended up on a team of almost all developers or no developers.

Each nonprofit presented two problems: one internal and one external. I chose the Atlanta Regional Commission, who were trying to solve the problem of transporting people with health issues to their healthcare provider. This was done through ride shares and tranpsortation providers/stakeholders. Their external problem involved coordinating these rides and routes. But I wanted to work on their internal problem, which involved visualizing the data they already have so that they can increase the efficiency of the program.

But when we were signing up for teams on the white board, there was no indication which one was the internal or external, they were just labelled Team 1 and Team 2. And even though the schedule said that we had until 11pm for breakout sessions, in reality we had almost no time: we had to leave the building by 9:30. There was no time on Day 1 for the actual work or even talking about and truly understanding the problem with our client.

All this to say that if anyone from GoodieHack is listening, please fix these problems next year! I still had fun, and it was still a rewarding experience, but it could be so much more so if things were planned out a little better.

### Day 2

Because we barely met our teams on Day 1, all the work happened on Day 2, which started at 8am. After breakfast and a few short speeches, we got to finally meet with our teams. There were many problems when we were first starting up. Some people didn't show up and the external team had no developers. On top of that, ARC was the only nonprofit to present two different external problems instead of one. We eventually decided to consolidate the team into one and all work on the internal problem.

Finally things were beginning to happen. We were gathered together in one corner of the Google offices and Janae (our client) told us what her problem was. But because she knew so much about the problem, it was very difficult for us to distill her knowledge into something we can tackle. Because at the end of the day, we were to pitch our solution as a potential start-up, it had to encompass her problem and widen out to a general problem that could be solved in an industry.

Thankfully GoodieHack had arranged for industry experts to help the different groups as mentors. We had Chidi, Haider, and Chris who were able to guide our conversation. We soon figured out the problem. ARC has all this data, or were planning on collecting all this data, about the rides that it was organizing between providers and riders. Janae had a gut feeling that there were inefficiencies driving up the cost per ride under certain providers. But a. she had no way of importing this data into usable form and b. she cannot ask a provider to increase their performance based on a gut feeling. She needed a visualization clearly showing which areas were lagging.

We quickly worked out a few user stories, and started dividing up the app into the major areas for different teams to work on. There was a team working on importing, a team on creating the map data, and a team working on the dashboard. There were also people thinking about the branding and design and people working on our actual presentation/pitch for the end of the day. We needed to turn everything in by 4pm, and it was already 11am at this point. Could we deliver a minimum viable product in about 4 hours?

Diana and I were the dashboard team and we got to work. First, I wanted to see if there were any ready built open source dashboards out there that I could grab. I found this <a href="https://github.com/keen/dashboards">one solution</a> that basically added a few layout classes to Bootstrap, which I was already familiar with. So it seemed like the right choice. It was made to work with Keen IO's visualization toolkit, but it wasn't hard to remove that part and substitute Google Charts (the event was sponsored and hosted at Google, so any inclusion of Google products gave us bonus points). Diana investigated Google Charts and figured out how to create charts of the types of data we wanted. I'd never worked with Google Charts but it turns out they're very easy to include in your page, and pretty powerful too.

After lunch, I worked with the map team to include the maps (done in Tableau) into the dashboard as well, as a separate tab. Then Diana worked on a beautiful logo that I included in the dashboard header. It was getting down to the wire. Dan was making last minute changes to his html5 slides and David was practicing his pitch.

We went back into the main room and made our pitches. We were the first team and I thought David made an [awesome pitch](https://www.youtube.com/embed/6axBpWJpnq4). The other teams made amazing apps too. The team that won made an Android app for underpriveleged youth to gain financial literacy. It was really cool! You can buy and sell pretend stocks that are updated from actual stock exchange, and answer financial quiz questions for credit. There were many other ideas that impressed me as well. One team made a mobile app for engaging kids which had the cutest icons and look and feel.

All in all, despite some initial misgivings due to organizational chaos, I had an amazing experience and met some awesome people who I will continue to learn from.