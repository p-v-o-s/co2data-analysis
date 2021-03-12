## Analyzing heating events at Artisan's Asylum

At Artisan's asylum, we'd been monitoring CO2 levels for a few weeks; data is here: [http://co2dataviz.pvos.org/data/brj93kvnkf6b/](http://co2dataviz.pvos.org/data/brj93kvnkf6b/)

We'd noticed particularly high CO2 levels.  A series of heating system failures led us to realize that the main source of the CO2 we were seeing was the heating system.  
![](img/heating_events_mar_5_annotated.png)

Based on the ventilation analysis suggested in [this twitter thread](https://twitter.com/Poppendieck/status/1366055149983076354), we attempt below to model several of these heating-system-failure events (labeled "A", "B", "C" above) with exponentials, in order to assess the time constant for the decay of CO2 over time. 

![](img/twitter_fit.png)

Some notes on the suggestions in the thread above:
- Avoid using the first 5 minutes after the initial decay onset
- Avoid using values below 600 ppm
- Assessing the time constant in units of hours results in a standardized measure of ventilation, the "air change per hour" (ACH).

![](img/ach_guidance.png)

## Analysis algorithm

Identify a subset of the dataset in which you suspect an appropriate exponential decay.
- $t$ = the time values of this subset of the data, in hours
- $y$ = the co2 values of this subset of the data, in PPM

A plot of $y(x)$ should look like an exponential decay; e.g. the red data subset shown below: 

![](img/exp_decay.png)

We are looking to determine the time constant for this exponential decay. A straightforward way to do this is to first normalize the data so that our decay occurs between values of 1 and 0, and begins at time $t=0$ hours.  

## References

- [Wikipedia article on air changes per hour](https://en.wikipedia.org/wiki/Air_changes_per_hour).
