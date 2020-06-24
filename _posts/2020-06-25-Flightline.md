---
layout: post
title: Flightline
subtitle: A look into 20 years of flights
gh-repo: paulteeter/
gh-badge: [star, fork, follow]
tags: [beginning]
comments: true
---

It seems all you do is wait and wait.
Airports are a necessary part of our lives now, as airtravel has become a mainstay in culture and business. With increasing domestic flight departures and increased customers, airline passengers are on average spending 19% more time waiting for taxiing and takeoff. Some airports report an average wait time of 23-25 minutes between pushback and takeoff.

Despite this annoying factor, a large number of domestic flights occur each year, and as expected, the amount is growing. How many flights and passengers are actually travelling domestically?

<figure>
		<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/Manchester_Airport_Departure_Sign.jpg/1280px-Manchester_Airport_Departure_Sign.jpg" width='800' alt="Airport Signage " title="Airport Signage" width="630" height="355">
										
					<font size="1.5"><i><figcaption>PHOTO: Manchester Airport Departure Sign (photo via wikimedia)</figcaption></i></font>
</figure>

Using data from the <a href="http://academictorrents.com/details/a2ccf94bbb4af222bf8e69dad60a68a29f310d9a">US Census Bureau</a> about US Domestic Flights between 1990 and 2009, I explored overall trends in flight data, as well as the specific effect of the events of September 11, 2001.

The questions I set out to answer seemed relatively easy to acquire, namely: <i>How was airtravel affected by the events of 9/11?
Were total passenger and flight amounts curtailed in the aftermath of September 11? Which cities were the most affected?</i> 
However, the task proved to be more difficult than I expected.

While the data was extensive and complete, it was also quite challenging to manipulate to yield usable results. Filtering the data by date while still preserving the other datapoints was extremely challenging, requiring the help of many hands<i>(shoutout to Brandon Mulas, Jacob Padgett, and Dustin Stringer for the help!)</i>.

The first endeavor was to get a list of the Top 20 cities based on total flights. There are many metrics with which airports are measured: total flights, total passenger load, commercial cargo tonnage, etc. For this case, I wanted to find which airports had the highest amount of total flights of origination. This gave me a list of 20 cities based on their total flights occurring between January, 1990 and September, 2001, and also another list of 20 cities post-9/11.
Since airports change based on their flight availability, scheduling, etc, year after year, the total metrics changed. 
The list of airports after 9/11 did not directly copy from the previous list, so in order to do a comparison, I kept the list of 20 airports from BEFORE Sept 11 and compared how they changed afterwards.

<br />
<h3>Pre 9/11 Top 20 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Post 9/11 Top 20</h>
<div id="wrapper">
 <div class="container">
	<img class="image" src="/assets/img/pre911cities.png" alt="Interpret1" width="250" height="600">
 	<img class="image" src="/assets/img/post911cities.png" alt="Interpret1" width="250" height="600">
 </div>
</div>



<iframe width="900" height="460" frameborder="0" scrolling="no" src="//plotly.com/~paul.teeter/1.embed"></iframe>
