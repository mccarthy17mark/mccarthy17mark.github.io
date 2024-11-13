---
layout: post
title:  "Regression with ML - using Toronto traffic as a case-study"
date:   2028-01-31 12:00:00 -0500
categories: 
usemathjax: true
---

## Overview

I wanted to get some practice with ML regression algorithms, and use an interesting but not too simple dataset. To do this project I used Toronto turning movement count (TMC) data for the traffic values, combined with the Toronto street centreline dataset, and the intersection dataset for some geographic context. With the data I trained some regression models from python's scikit-learn package to have a model for traffic volume at arbitrary intersections based on location, year, and the sizes of the streets involved in the intersection.

You can find the code that generated this analysis on [my github]()

### The datasets

The [TMC dataset](https://open.toronto.ca/dataset/traffic-volumes-at-intersections-for-all-modes/) is a manual count of automobile, bicycle, and pedestrian traffic, usually at an intersection. Since these are manual counts, there are some quirks to the data, as the traffic is primarily recorded during working hours only:

![Plot showing measurement times are clustered to working hours, with breaks visible](assets/posts/torontoTraffic/time_of_day_counts.png)

I've coloured the typical 9-5 workday in green and the surrouding two hours in yellow to highlight when traffic is expected to be the most significant.

![Plot showing measurements per day-of-week, with Fridays and Sundays having very low counts](assets/posts/torontoTraffic/time_of_day_counts.png)

Now that we have an understanding of the temporal quirks of the data, let's take a look at how our measurements are distributed spatially:

![Map showing traffic measurements distributed across Toronto](assets/posts/torontoTraffic/raw_car_traffic.png)

The larger roads and highways receive more attention than smaller streets.
