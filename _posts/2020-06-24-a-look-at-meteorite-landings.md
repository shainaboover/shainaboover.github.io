---
layout: post
title: A Look at Meteorite Landings
subtitle: Analyzing the size and frequency of Meteorites found on Earth
cover-img: /assets/img/path.jpg
# tags: [books, test]
---

I took a look at NASA's Meteorite Landings dataset. This set contains information about recorded meteorite landings on Earth between the years 601 and 2013. I wanted to see if I could find anything interesting about the mass, location, and frequency of meteorites.

I wondered:
Historically, how often are meteorites recorded?
Is there a notable difference in mass between the meteorites that were observed falling from the sky vs those that were found on the ground?
Do more meteorites tend to be found in specific locations?

First, to get a feel for the data, I took a general look at how many were found per year.
--find out how to put in image: meteor['year'].value_counts().sort_index(ascending=False).plot(figsize=(20,5), title='Recorded Meteorite Findings')
plt.ylabel('Amount')
plt.xlabel('Year');--

Perhaps unsuprisingly, the vast majority of meteorites were recorded in the last 50 or so years. Here's a look at just the last century's worth of meteorite collection. During the 1970's, we went from recording very few to hundreds and even thousands of meteorites per year!
--find out how to put in image: meteor['year'].value_counts().sort_index(ascending=False).plot(figsize=(20,5), xlim=(1900, 2013), title='Meteorites Found between 1900-2013')
plt.ylabel('Amount')
plt.xlabel('Year');--

Next, I explored how often meteorites were observed falling vs found on the ground. It seems as though meteorite landings that were observed falling are much rarer than those that are found. This makes sense considering how small the meteorites tend to be (more on that later).
--find out how to put in imgage: xtab.plot(figsize=(20,5), xlim=(1900,2013), title='Meteorites: Found vs Observed Falling from Sky')
plt.ylabel('Amount')
plt.xlabel('Year');--

Are observed meteorites generally larger than the ones that are found? To be seen in the sky, I reasoned, they must be larger than average. Intuitively, it seems that the bigger a meteorite is, the easier it can be spotted. I turned out to be wrong in that assumption, however there IS a notable difference in the frequency of smaller meteorites.

Over the last 50 years, we started collecting loads of meteorites. Most of these turned out to be extremely small pieces that were overlooked until we figured out how to spot them. You can see how meteorites of smaller weights are being recorded on a much larger scale than ever before.
--find out how to put in image: xtab2.plot.barh(figsize=(30,20), title='Mass of Meteorites by Year', color=('slategrey', 'navajowhite', 'palevioletred', 'darkseagreen', 'rosybrown'))
plt.xlabel('Number of Meteorites')
plt.ylabel('Mass (Grams)');--

A blog post about meteors wouldn't be complete without a map of all recorded meteorite landings across the globe
--find out how to put in image: m = Basemap(projection='merc',llcrnrlat=-80,urcrnrlat=80,\
            llcrnrlon=-180,urcrnrlon=180,lat_ts=20,resolution='c')
plt.figure(figsize=(5,7), dpi=300)
m.shadedrelief()
lon, lat = np.array(meteor['reclong']), np.array(meteor['reclat'])
x, y = m(lon, lat)
m.plot(x, y, 'b+', markersize=.3, alpha=.3)
plt.show();--

Turns out, meteorites are found everywhere! They are spread across all continents, even on small islands. I wondered which locations had the highest concentrations. I took a look at the 5 coordinates that recorded the greatest number of these surprisingly common space rocks.
-- top_five dataframe --

I learned that all five coordinates (plus the next 4, totalling top 9 most densely concentrated) were in Antarctica! I won't be getting into why this is, but if you're curious like I am, you can follow the links below to learn about the Antarctic Search for Meteorites (ANSMET) program. 

https://www.discovermagazine.com/the-sciences/do-more-meteorites-fall-on-antarctica
https://caslabs.case.edu/ansmet/category/19-20/

I was quite surprised by the number of meteorites we're now finding on Earth's surface. The relatively new realization that these extraterrestrial objects are all around us, is a testament to the connectedness of the universe. A concept that can so easily be lost here on this planet's surface. So the next time you pick up that funny looking rock, remember that you're a part of something fascinating: a mystery of the universe, hiding in plain sight, if you only choose to look.




