---
layout: post
title: A Look at Meteorite Landings
subtitle: Analyzing the size and frequency of Meteorites found on Earth
cover-img: /assets/img/path.jpg
# tags: [books, test]
---

I took a look at NASA'S Meteorite Landings dataset. This set contains information about all recorded meteorite landings on Earth between the years 601 and 2013. I wanted to see if I could find anything interesting about the mass, location, and frequency of meteorites.

I wondered if there was a significant difference in mass between the meteorites that were observed falling from the sky, and those that were found on the ground. 

But first, to get a feel for the data, I took a general look at how many were found per year
meteor['year'].value_counts().sort_index(ascending=False).plot(figsize=(20,5), title='Recorded Meteorite Findings');

Perhaps unsuprisingly, the vast majority of meteorites were recorded in the last 50 or so years. Here's a look at just the last century's worth of meteorite collection
meteor['year'].value_counts().sort_index(ascending=False).plot(figsize=(20,5), xlim=(1900, 2013), title='Meteorites Found between 1900-2013');




