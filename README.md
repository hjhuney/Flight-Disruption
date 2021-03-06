# Flight Disruption in the US

This notebook analyzes US flight disruptions using the [Bureau of Transportation Statistics](https://www.bts.gov/topics/airlines-and-airports-0) on-time performance data running from December 2015 to November 2018. We define disruptions to mean cancellations and flights delayed more than 4 hours. We also look at the replacements costs of these disruptions based on an assumed cost of $500 per disrupted flight. For instance, if 2 flights out of 100 were disrupted, replacement cost would be $1,000 divided by 100 flights, or $10 per flight on average. 

There were over 18 million flights in the United States during this 3-year timeframe. 266,449 of these flights (1.45%) were cancelled and 358,672 were disrupted (1.95%). The average expected replacement ticket cost per flight was $9.75 based on our $500 assumption. Based on the data, it would appear that most long delays were due to carrier (approximately 68%); with weather and NAS operation delays being the next most common reasons. 

We'll examine disruption stats by airport, route, carrier, month, state, time block, and distance. 

The full code includes a model to predict the cost of insuring disrupted flights. 

Full code can be found [here](https://nbviewer.jupyter.org/github/hjhuney/Flight-Disruption/blob/master/BTS_Airline_OnTime_Perf_2016_18.ipynb). 

## Airport Stats

There are over 300 airports in the US for this analysis. To make the visualizations most useful, we'll only analyze the top 40 airports in terms of traffic. First, let's look at the disruption percentage by the top 40 airports. 

![Top 40 Airports Disruption %](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/airport002.svg)

Now we'll look at the replacement cost measures. Note that this is the exact same chart as above, just with replacement ticket cost estimates forming the y-axis rather than disruption rate. 

![Top 40 Airport Disruption Costs](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/airport001.svg)

What we can see from the data is that the New York area airports (LGA / JFK / EWK) have the highest disruption costs. The Northeast US, in general, seems to be most prone to disruptions with Boston (BOS), DC National (DCA), and Philadelphia (PHL) all high on the list. Chicago-O'Hare (ORD) is also very high on the list. While winter weather may be a problem, we should note that most of the Rocky Mountain airports do not experience the same disruption issues, with Salt Lake City (SLC) and Denver (DEN) both having below-average disruption rates. We may surmise from this that a combination of traffic issues, airline specific issues, and weather are responsible for most disruptions. 

## Route Stats

Let's break down the airport stats further and look at major routes. There are over 6,000 different routes, so first off, we'll shrink our analysis down to the 200 most frequently travelled routes. From those 200 routes, we'll look at the top 40 in terms of passengers as well as the highest disruption costs. First, the top 40 routes in terms of traffic. 


![40 Most Travelled Routes by Disruption Cost](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/route001.svg)


Now, we'll look at the top 40 routes in terms of disruptions out of the top 200 most travelled. 


![40 Common Routes with Highest Disruption Costs](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/route002.svg)

The routes with he highest disruption costs include:

* Boston (BOS) to New York (LGA / JFK / EWR)
* Houston (HOU) to Dallas (DFW)
* New York (LGA) to Charlotte (CLT)
* Orlando (MCO) to New York (LGA / JFK / EWR)
* Los Angeles (LAX) to San Francisco (SFO)


## Carrier Stats

Next, we'll take a look at carrier performance. 

![Average Disruption Costs by Carrier](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/carrier001.svg)

From this chart, we can see that Delta Airlines does extremely well versus other major carriers, particularly given its nationwide geographic reach, this is very impressive. Of the major carriers, American Airlines performs the worst. Regional carriers such as PSA, Republic, SkyWest, and ExpressJet dominate the carriers with the highest disruption costs. 

JetBlue does not perform that well here, but we need to examine it more closely to get a deeper picture. Is JBLU's poor disruption performance a result of operating issues or a result of having exposure to "high disruption rate airports" such as LGA and JFK? 

We can further isolate the carriers by looking at origin airport and route specific stats. Let's take a look at the disruption rates at five of the US's busiest airports: 

Atlanta's Hartsfield-Jackson Airport (ATL):

![Average Disruption Rate ATL](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/disrupt_atl.svg)

New York's LaGuardia Airport (LGA):

![Average Disruption Rate LGA](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/disrupt_lga.svg)

Boston's Logan Airport (BOS):

![Average Disruption Rate by BOS](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/disrupt_bos.svg)

Chicago O'Hare (ORD):

![Average Disruption Rate by ORD](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/disrupt_ord.svg)

Los Angeles International (LAX):

![Average Disruption Rate by LAX](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/disrupt_lax.svg)

We can see that Delta performs well at every airport examined. While Alaska Airlines doesn't have as big of a reach as Delta, it performs very well in the airports it services. We can also see that JetBlue's stats look better on an airport-specific basis. It has a ~ 4% disruption rate at LGA (well above the national disruption rate average of around 2%), but this makes it the 4th best performing airline at that airport. Similarly, JetBlue is the 4th best performing airline at BOS, so JetBlue's above-average disruption rate in the aggregate may be a consequence of being more exposed to New York and the Northeast rather than an issue with its own operations. 

Finally, let's look at some route stats for the carriers, as well. There are thousands of routes and I'm only going to show visualizations for 3 heavily-travelled ones: 

(1) Atlanta (ATL) - LaGuardia (LGA)
(2) Atlanta (ATL) - O'Hare (ORD)
(3) Boston (BOS) - LaGuardia (LGA)

![Average Disruption Rate ATL-LGA](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/disrupt_atl-lga.svg)
![Average Disruption Rate ATL-ORD](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/disrupt_atl-ord.svg)
![Average Disruption Rate BOS-LGA](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/disrupt_bos-lga.svg)

Once again, we can see that Delta is a top performer. JetBlue also does well on the BOS-LGA route. 

Now, let's move onto some other stats. 

## Month and Year Stats

Next, we'll take a look at disruptions by month. 

![Average Disruption % by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/month001.svg)

Here we see that January is the month most prone to disruptions, but winter and summer months, in general, are the most likely to be disrupted, while Spring and Autumn months (April, May, October, November) are least likely to be disrupted. 

Below, we can see the same chart, but with the breakdown by replacement ticket costs per customer. 

![Average Disruption Costs by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/month002.svg)

Now, let's take a look at the breakdown by year, while also viewing the stats for the major carriers. 

![Average Disruption Costs by Year and Carrier](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/carrier_by_year.svg)


## State Stats

The chart below analyzes disruption costs per customer by origin state. Note, that origin and destination stats tend to be fairly similar, so I'm only showing one of the two. 

![Average Disruption Cost by Origin State](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/state002.svg)

From this chart, we can see that Maine (ME), Vermont (VT), and West Virginia (WV) have the highest costs. New York (NY) and New Jersey (NJ) are also very elevated. States with the fewest disruptions include Washington (WA), Utah (UT), and Hawaii (HI). 

## Time of Day Stats

Below, we can see disruption percentage by takeoff and arrival time blocks. Common theme is that late morning / early afternoon flights tend to have the lowest disruption rates. 

![Average Disruption % by Takeoff Timeblock](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/timeblock001.svg)


![Average Disruption % by Arrival Timeblock](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/timeblock002.svg)


## Distance Stats

Finally, we'll take a look at distance blocks, where we'll discover that short flights tend to have the highest disruption costs. 

![Average Disruption Cost by Distance](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/distance001.svg)


## Thanks

That's it for the visualization. To see the full code and prediction model, view the notebook in the main repoistory. Thanks for reading!
