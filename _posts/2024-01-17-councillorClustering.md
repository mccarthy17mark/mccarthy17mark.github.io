---
layout: post
title:  "Clustering: Using the City of Toronto's Open Data to Analyze Councillor Voting Behaviour"
date:   2024-01-17 12:00:00 -0500
categories: 
---

Canadian municipal politics is arguably the most important form of politics to those who live in the jurisdiction, but it can also be impenetrable to outsiders due to the lack of parties, platforms, and the highly specific local issues that are debated. Could we determine which voting blocs exist without this information? Can we determine which politicians make compromises and which refuse to bend?

I  wrote a clustering algorithm to group councillors based their voting records, developed it with Toronto data and evaluated it with Calgary data, and you can see the jupyter notebook [here](https://github.com/mccarthy17mark/councillors/blob/master/councillor_clustering.ipynb). This is, in a sense, a continuation of the analysis being done in my [previous post]().

For the technically-minded reader, the clustering algorithm was a heirarchichal agglomerative clustering using a Bayesian probability of the councillors within the group not being unanimous as the objective function to be minimized. Some analysis is done to identify how a binomial distribution can reasonably be applied to the data despite not having any knowledge of the issues being voted upon. Lastly, the Hartigan-Wong algorithm was applied to ensure we were at a (at least local) minimum.

---

Many municipalities have open source data available on a very wide number of topics. For example, in Toronto you can find data on everything from all public city-provided wifi, to red-light camera locations, to restaurant food inspection results. Here are the data for [Toronto](https://open.toronto.ca/) and [Calgary](https://data.calgary.ca/). Here I've used the data listing how councillors voted in all recorded city council meetings.

If we look at voting records we can try to group councillors together based on how similar they are from each other. To see if we've done a good job clustering, I built everything that follows using the Toronto council voting data. When I was satisfied that the results looked reasonable, I tested to see if it worked using the Calgary council voting data.

Unfortunately we see that there is a substantial difference between the two datasets. Toronto's voting records go back to 2006, whereas Calgary's only go back to 2017. To go back further with Calgary's data, it looks like I'd have to do some pdf scraping of the meeting minutes. Since this is supposed to be a ***fun*** project, I'll just let it be. If I were to do this again, I'd find a better train-validation-test breakdown.

