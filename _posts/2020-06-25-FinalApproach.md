---
layout: post
title: Final Approach
subtitle: A look into 20 years of flights
gh-repo: paulteeter/
gh-badge: [star, fork, follow]
tags: [Data Science, Lambda, Data, Mildly Interesting]
comments: true
---

These days, it seems all you do is wait and wait.

Airports are a necessary part of our lives now, as airtravel has become a mainstay in culture and business. With increasing domestic flight departures and increased customers, airline passengers are on average spending 19% more time waiting for taxiing and takeoff. Some airports report an average wait time of 23-25 minutes between pushback and takeoff.

Despite this annoying factor, a large number of domestic flights occur each year, and as expected, the amount is growing. So how many passengers are actually travelling domestically?

<figure>
		<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/3/34/Manchester_Airport_Departure_Sign.jpg/1280px-Manchester_Airport_Departure_Sign.jpg" width='800' alt="Airport Signage " title="Airport Signage" width="630" height="355">
										
					<font size="1.5"><i><figcaption>PHOTO: Manchester Airport Departure Sign (photo via wikimedia)</figcaption></i></font>
</figure>

Using data from the <a href="http://academictorrents.com/details/a2ccf94bbb4af222bf8e69dad60a68a29f310d9a">US Census Bureau</a> about US Domestic Flights between 1990 and 2009, I explored overall trends in flight data, as well as the specific effect of the events of September 11, 2001.

The questions I set out to answer seemed relatively easy to acquire, namely: <i>How was airtravel affected by the events of 9/11?
Were total passenger and flight amounts curtailed in the aftermath of September 11? Which cities were the most affected?</i> 
However, the task proved to be more difficult than I expected.

While the data was extensive and complete, it was also quite challenging to manipulate to yield usable results. Filtering the data by date while still preserving the other datapoints was extremely challenging, requiring the help of many hands <i>(shoutout to Brandon Mulas, Jacob Padgett, and Dustin Stringer for the help!)</i>.

The first endeavor was to get a list of the Top 20 cities based on total flights. There are many metrics with which airports are measured: total flights, total passenger load, commercial cargo tonnage, etc. For this case, I wanted to find which airports had the highest amount of total flights of origination. This gave me a list of 20 cities based on their total flights occurring between January, 1990 and September, 2001, and also another list of 20 cities post-9/11.
Since airport rankings change based on their flight availability, scheduling, etc. year after year, the differences experienced were not surprising. 
The list of airports after 9/11 did not directly mirror the previous list, so in order to do a comparison, I kept the list of 20 airports from BEFORE Sept 11 and compared how they changed afterwards.

<br />
<h4>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Pre 9/11 Top 20 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Post 9/11 Top 20</h4>
<div id="wrapper">
 <div class="container">
	<img class="image" src="/assets/img/pre911cities.png" alt="Interpret1" width="250" height="600">
 	<img class="image" src="/assets/img/post911cities.png" alt="Interpret1" width="250" height="600">
 </div>
</div>

From the information available, it is not explicitly obvious that the events of September 11 had any direct bearing on TOTAL travel trends, beyond the obvious temporary lull. As seen here, most cities experienced a slight loss in density of average passengers per flight. Even though flight and passenger amounts were on an upward trend despite Sept. 11, this discrepancy can probably be attributed to company policy and market adjustments. Overselling of flights helps keep the margins down and ensures peak profitability with the changing market.

Many changes happened in light of Sept. 11, 2001. The introduction of the TSA and higher security protocols can and did have an affect on overall flights at first. Also, customer confidence plays a part in the slow return of normal flight patterns. As time progressed and the public became used to the "new normal", flights and passenger totals began to climb again.

<iframe width="900" height="460" frameborder="0" scrolling="no" src="//plotly.com/~paul.teeter/1.embed"></iframe>

An interesting point of note here: While major destinations like Las Vegas NV, Orlando FL or Honolulu HI are more "destinations" rather than connections, their totals of average passengers per flight is noticably higher than major connection hubs like Dallas, TX or Atlanta, GA.
This is easily understood because of their large draw, but limited availability for flights -- especially Honolulu. The airlines make sure they sell out the flight to make such a long, expensive trip. No empty seats, please!

<h4>New York</h4>
New York was forever changed by the events of Sept 11. Not only did the skyline change drastically, the sense of unity and compassion that overflowed in the city's population was palpable. All across the nation, Americans mourned the loss of life -- the wanton destruction of our greatest asset. Flights were grounded across the country (even globally, in some cases), and there was a major disruption of commercial aviation. 
Just a simple look at the following graph shows the drastic change around 9/11/2001. It took about a full year to attain the levels of Pre 9/11 flight totals.
The following graph displays flights from ALL airports in NYC from 2000-2005

<img class="image" src="/assets/img/ny2000_2004.png" alt="New York Flights 2000-2004" width="1200" height="500">

Obviously, the immediate affects of Sept 11 were apparent, even without the data to display, but this graph shows the extent as it related to commercial flights. Even though flights were grounded in the US for a total of two days (except emergency medical and approved military flights), there were 10 days of flights before, as well as 18 days of flights after limited service began again. This is reflected in the non-zero low point for september, 2001, totalling 13,298 total flights for the month of September from New York's JFK and LaGuardia airports.
The reason you cannot find a 0 number on this graph is because of the way the data was recorded. Each observation was only recorded as a Year and Month, so that's as far as the data can break down. I was disappointed to find I couldn't specifically pinpoint the two days US domestic flights were grounded, but I still found some use in organizing the data in the way that I did.

When factoring in the other major airport servicing the NY Metro area (Newark Liberty Int'l), the totals of course go up, but the trend is essentially the same. It took about a year to fully recover back to Pre 9/11 flights.
The graph below shows the three major airports servicing NYC over the span of 20 years.

<b>Black:</b> Newark Liberty Int'l<br />
<b>Turquoise:</b> LaGuardia Airport<br />
<b>Purple:</b> JFK Int'l<br />
<img src="/assets/img/metroNYC_allyears.png" alt="Metro NYC Airports 1990-2009 " title="MetroNYC Airports" width="1200" height="500">

<h4> Final Look</h4>
After spending all too much time trying to figure out the best way to organize the data, I settled on a very broad approach to displaying the overall trend of the flights and passengers domestically across the 20-year span. Breaking down each metric by the total for a whole year gives a much cleaner look at the overall trend, without the <a href="https://ibb.co/rxXZNxQ">squiggly</a> lines inherent in high datapoint plotting.

An interesting thing took place around February, 2002: the total passengers grew at a much quicker rate than the total flights. This is probably due to overbooking of flights nationally to make sure flights were carrying more passengers per flight. More passengers = more money. Ultimately, most business decisions come down to profitability for shareholders, so even though travelers were still increasing month upon month, the constraints imposed on airlines and airports required changes in how flights and passengers were scheduled. Of course, it is hard to know when an influx of passengers will come, so there is a delay to create new flight supply to meet the demand of increasing ridership.

<iframe width="900" height="500" frameborder="0" scrolling="no" src="//plotly.com/~paul.teeter/5.embed"></iframe>

Also noticeable from this graph was the economic downturn and subsequent recession beginning in 2007. The decline from the recession is about as precipitous as the fallout from September 11. Unfortunately, the dataset is only extended to 2009, so no further information can be seen, but it would be quite interesting to see how the recession affected flight trends. Of course, the lasting effects of economic recession are probably more noticeable and far-reaching than a singular event, bad as it was. Perhaps another day I will merge a dataset in to expand on this graph and see the extent to which the airlines were affected by the recession. 

<h4>Conclusion</h4>
Despite the shock of using an airplane as a weapon and the expected lasting result of that heinous act, I found very little disruption overall to domestic flight patterns. More and more passengers were flying and more flights were scheduled. For such a devastating event, it had relatively little impact on the flight amounts themselves, while having an outsized impact on other travel metrics, namely time and customer satisfaction. It is becoming increasingly difficult to air travel today, with the restrictions only getting more severe and burdensome. 

Of course, this is also an issue best explored elsewhere, but our aging infrastructure and airport system is not equipped to handle the amount of traffic experienced on a daily basis across the US. This is why wait times are ever growing and a slow pushback/taxi/waiting on the tarmac is experienced more often. I suggest you grab a pillow and your favorite book, you're probably in for a long wait!

