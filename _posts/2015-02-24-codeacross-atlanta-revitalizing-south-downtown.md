---
layout: post
title: "CodeAcross Atlanta: Revitalizing South Downtown"
tags:
- CodeAcross
- hackathons
- CodeForAtlanta
- civic hacking
comments: true
---

This past weekend, I attended my first hackathon-like event (there was no competitive element, so it's not a hackathon, technically speaking). Organized by <a href="http://www.codeforatlanta.org/">Code For Atlanta</a> and hosted by the <a href="http://www.civicatlanta.org/">Center for Civic Innovation</a> as part of an international <a href="http://www.codeforamerica.org/events/codeacross-2015/">CodeAcross event</a>, we met in South Downtown Atlanta to tackle the problems there, namely, how to revitalize the neighborhood.

In order to tackle the problem, we first had to understand the problem. So after a quick presentation on the history of the area, we took a walking tour of it. This introduction was captivating, but at the same time, I didn't see eye to eye with our hosts.

Many of the participants of this event were not from this area. They see it as a dilapidated poor neighborhood that needs to be cleaned up. But I live within 5 miles of South Downtown and enjoy biking through the area. I also regularly attend shows at the <a href="http://www.eyedrum.org/">Eyedrum Art Gallery</a> and <a href="http://www.mammalgallery.com/">Mammal Gallery</a>. Yes, the neighborhood is poor, but people live and work here too. Often when we say we want to revitalize a neighborhood, it means gentrification. When we say we want to attract new developers, we're also implying that we want the old businesses out. That means <a href="http://largefeet.com/">Friedman's Shoes</a>, who's been serving large feet since 1929. That means the local charm of <a href="http://clatl.com/atlanta/i-like-south-downtown-atlanta-the-way-it-is/Content?oid=4209416">Rondo</a>, which sells hexes, charms, and mojo powder.

But I wasn't completely against the enterprise. I agree that many things could be improved in this area. But I tried to steer our group into thinking about what those needs were based on what the locals wanted instead of what tourists would want. To improve the area, we must improve the lives of the people in the area, not bring new people in.

<img src="images/southdowntown1.jpg" alt="South Downtown Atlanta" />

Perhaps this is all too political for a tech blog, so let me go back to describing the rest of the weekend's events.

We broke into three groups:
<ol>
	<li><strong>Branding and storytelling</strong> - how to brand the neighborhood to attract the 'right' elements</li>
	<li><strong>Interactive asset map</strong> - so people can see what's there and what can be there</li>
	<li><strong>Participatory tool</strong> - to gather opinions from the community about what the area needs</li>
</ol>
I joined the second group because I was interested in mapping and because I felt like I could learn the most there. First we talked about who the audience for the map could be, and given that, what assets we could or should map. Then we broke into two groups, one responsible for data gathering and one for building out the map with the given data. I joined the latter group, which consisted of four people: me, <a href="http://mollietaylor.com/">Mollie</a>, <a href="http://luigimontanez.com/">Luigi</a>, and <a href="http://www.bryan-lackey.com/">Bryan</a>.

Mollie was the resident expert on maps and mapping. She showed us how to use <a href="http://leafletjs.com/">Leaflet.js</a> to quickly build out maps and create interactive event based behaviors. While she built out a prototype, the rest of us went through some tutorials to get acquainted with Leaflet, and also explore other possibilities like <a href="https://www.mapbox.com/">Mapbox</a>.

After that, I started to think about where I could be most useful. Since Mollie was already kicking ass on the maps, I thought I could do something to help import the data. The data gathering team was sending us Excel files with street addresses. In order to plot the points, geocode data was needed, which just means latitude and longitude. So I decided to write a small utility that would take a CSV file and write a new CSV file with all the existing data plus latitude and longitude.

Writing a script to do that wouldn't have taken long, but I thought this might be a tool that could be used in the future by Code For Atlanta or other similar groups faced with this same problem. So I worked on a Ruby program that could potentially be re-used in other projects. You can see the code for it <a href="https://github.com/codeforatlanta/csv_geocoder">on GitHub</a>, and I'll probably write a follow up post soon on a few interesting design challenges I ran into.

<img src="images/southdowntown2.jpg" alt="Screenshot of South Downtown Asset Map" />

### Day 2

Things began slowly with coffee at 9am. A few folks stared into their laptops like zombies. I was one of those. My CSV Geocoder was working, but I couldn't help tinkering with it, refactoring and improving it (in fact, I was still doing that earlier today). But more of the data was coming in in different formats. I was looking for a new task to do.

One of the things Mollie implemented the day before was integration of <a href="https://foursquare.com/">Foursquare</a> data from their API. We were now pulling in data about government buildings in South Downtown. But what other Foursquare locations could we map? I wrote some scripts to automate this query. Other than that, I did some research on icons, and I also talked with members of the other teams about what they were doing.

At the end of the day, we all presented our projects. It was inspiring to see how much progress we made in just two days, and also to think about how all three projects will integrate into one larger project. The map will live on the website that the branding group created (which will eventually live at <a href="http://www.southdowntown.org/">southdowntown.org</a>) and the participatory tool created by the third team will eventually feed back into the map and website so that the wishes and desires of the locals will be our guide.

Speaking of the future, this weekend was just the beginning of a longer effort. We will continue to meet about once a month to continue developing this project.

Overall, I had a great first hackathon. I met some amazing people and learned a lot from them. I worked on interesting projects, and I got to become more familiar with a local neighborhood.

To learn more about the details of making the map, creating the layers and interactions, go read <a href="http://blog.mollietaylor.com/codeacross-asset-map.html">Mollie's excellent blog post</a> about this same event! It's pretty great. You can also see the source of both the asset map and my CSV geocoder on the <a href="https://github.com/codeforatlanta/">codeforatlanta GitHub page</a>.