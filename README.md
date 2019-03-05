# Flight-Disruption

Here we analyze US flight disruptions using the Bureau of Transportation Statistics on-time performance data running from December 2015 to November 2018. We define disruptions to mean cancellations and flights delayed more than 4 hours. We also look at the replacements costs of these disruptions based on an assumed cost of $500 per disrupted flight. For instance, if 2 flights out of 100 were disrupted, replacement cost would be $1,000 divided by 100 flights, or $10 per flight on average. 

There were over 18 million flights in the United States during this 3-year timeframe. 266,449 of these flights (1.45%) were cancelled and 358,672 were disrupted (1.95%). The average expected replacement ticket cost per flight was $9.75 based on our $500 assumption. Based on the data, it would appear that most long delays were due to carrier (approximately 68%); with weather and NAS operation delays being the next most common reasons. 

We'll examine disruption stats by airport, route, carrier, month, state, time block, and distance. 

The full code can be found [here](https://github.com/hjhuney/Flight-Disruption/blob/master/BTS_Airline_OnTime_Perf_2016_18.ipynb). It includes a model to predict the cost of insuring disrupted flights. 

## Airport Stats

There are over 300 airports in the US for this analysis. To make the visualizations most useful, we'll only analyze the top 40 airports in terms of traffic. First, let's look at the disruption percentage by the top 40 airports. 

![Top 40 Airports Disruption %](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/airport002.svg)

Now we'll look at the replacement cost measures, first looking at total average replacement cost per customer and then breaking it down by cancellations versus 4+ hour delays. 

![Top 40 Airport Disruption Costs](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/airport001.svg)

![Cost Attributable to Cancellations](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/airport003.svg)

![Costs Attributable to Delays](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/airport004.svg)

What we can see from the data is that the New York area airports (LGA / JFK / EWK) have the highest disruption costs. The Northeast US, in general, seems to be most prone to disruptions with Boston (BOS), DC National (DCA), and Philadelphia (PHL) all high on the list. Chicago-O'Hare (ORD) is also very high on the list. While winter weather may be a problem, we should note that most of the Rocky Mountain airports do not experience the same disruption issues, with Salt Lake City (SLC) and Denver (DEN) both under the average disruption rate. We may surmise from this that a combination of traffic issues, airline specific issues, and weather are responsible for most disruptions. 

## Route Stats

Let's break down the airport stats further and look at major routes. There are over 6,000 different routes, so first off, we'll shrink our analysis down to the 200 most frequently travelled routes. From those 200 routes, we'll look at the 40 most frequently travelled as well as the 40 with the highest costs. First, the top 40 routes in terms of traffic. 


![40 Most Travelled Routes by Disruption Cost](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/route001.svg)


Now, we'll look at the top 40 routes out of the top 200


![40 Common Routes with Highest Disruption Costs](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/route002.svg)


## Carrier Stats

![Average Disruption Costs by Carrier](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/carrier001.svg)

## Month Stats

![Average Disruption % by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/month001.svg)

![Average Disruption % by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/month002.svg)

![Average Disruption % by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/month003.svg)

![Average Disruption % by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/month004.svg)

## State Stats

![Average Disruption % by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/timeblock001.svg)

## Time of Day Stats

![Average Disruption % by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/timeblock002.svg)


![Average Disruption % by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/timeblock003.svg)


## Distance Stats

![Average Disruption % by Month](https://github.com/hjhuney/Flight-Disruption/blob/master/Images/distance001.svg)
