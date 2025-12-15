# Project Title

## 1. Research Question

I am investigating the significance of driving distance on the PGA Tour to winning purse money in a tournament. I know this may not advance the common good, as is the mission of St. Thomas, but it's an extremely interesting topic to me and something I am motivated to do analysis on.

** Stretch goal: does driving distance, driving accuracy, or proximity to the hole contribute more to purse money won?
** Time permitting, I'd like to analyze these three performance categories to see which correlates most highly to money earned.

## 2. Hypothesis

Null hypothesis: greater driving distance has no impact on the percent of purse money won.
Alternate hypothesis: the longer average drive/the higher a player ranks in driving distance, the higher percent of purse money they win.


## 3. Data Description

Describe your data source(s):
* My data comes from the PGA Tour statistics website: https://www.pgatour.com/stats
* I pulled data on average driving distance and where that player ranked in 2024 on Tour, as well as their percent of purses won
    * I chose percent of purse because this is a better indicator of performance then total money earned.
    * Total money earned can vary by many factors - some players play in more tournaments than others. Some tournaments pay out much larger winnings than others. I believe that percent of purse won (money earned / total purse available) is a better indicator of performance.
* My data consists of 180 rows, 180 players with qualifying driving statistics and money earned.
* I don't believe I'll need to clean the data as it is precise, specific to what I need, and void of any outliers or invalid rows.
    * However, I will use the opportunity to standardize the data - numeric, percentages, lower case objects, etc.

  My data is stored in my github repository as a release: https://github.com/matthewscheney/631_project_golf_purse/releases

## 4. Methods

Summarize how you analyzed the data:

* The test statistic for your permutation test
     * My test statistic is the difference in mean percent of purse won between "long" hitters (top quartile in driving distance) and "short" hissters (bottom quartile)
* How you simulated or resampled under the null hypothesis
     * I used a permutation test to obtain a reference distribution if driving rank is shuffled among the percent purse won values
     * I then performed a bootstrap analysis to obtain a 95% confidence interval on the mean percent for each quartile
     * Finally, performed a bootstrap analysis for a 95% CI on the max percent in each quartile
* The metric(s) for which you created bootstrap confidence intervals
     * I first used the mean of percent purse won, then used Max (a measure unusable by CLT)
* Why the CLT does not apply to at least one metric
     * CLT does not apply to the Max because it is not an additive value
     * What is interesting is to see the distribution of Max in my histogram. It's not pretty, but it's an interesting visual on how a value like Max behaves when bootstrapped, especially on a *relatively* small sample size like i have here (~45).

## 5. Results

Present your main findings:

* Key summary statistics and visualizations
      *See powerpoint for visualizations
      *Top 25 -- Mean: 1.08	Upper 95: 1.51	Lower 95: 0.76	Range: 0.76 
      *Bottom 25 --	Mean: 0.86	Upper 95 : 1.09	Lower 95: 0.66	Range: 0.43
      * Difference in means: 0.2233

* Observed test statistic and p-value (if applicable)
*    Observed: 0.2233
*    p-value: 0.3465
* Bootstrap confidence intervals for relevant metrics
*    CI for Mean: Top 25 -- Mean: 1.08	Upper 95: 1.51	Lower 95: 0.76	Range: 0.76
*    Bottom 25 --	Mean: 0.86	Upper 95 : 1.09	Lower 95: 0.66	Range: 0.43
*    CI for Max: Top 25		Max: 7.76	Upper: 7.76	Lower: 1.44	Range: 6.32
               Bottom 25	Max: 4.00	Upper: 4.00	Lower: 1.13	Range: 2.87


## 6. Uncertainty Estimation

Discuss your resampling results:

* How many resamples you used
*    10,000 resamples for the permutation and each CI test    
* What the bootstrap or randomization distributions looked like
*    The permutation mean distribution is normal, centered on 0, with short tails
*    The CI distribution for the Mean is also normal for both groups, centered around their perspective means
*    The CI distibution for the Max is very odd looking, with a only a few values represented. Not normal shaped.
* How you interpret the interval estimates
*    For mean, we have 95% confidence that the mean percent purse won is between 0.76% and 1.51% for the top quartile, and between 0.66% and 1.09% for the bottom quartile. For this analysis, the fact that the lower bound of the top quartile and the upper bound of the bottom quartile means we cannot say there is a statistically significant difference between the groups.

## 7. Limitations

Briefly note any limitations in data, assumptions, or methods, including sources of bias or missing data.
* I don't know that my data had limitations, in fact it might be the opposite. If we only use my data to analyze PGA performance, then we don't really have a sample of data - we have the population.
* One could theoretically extrapolate this to lower professional tours, but as is, we have PGA data and can only realistically apply it to PGA performance.
* The CI bootstrap on Max was interesting. I was actually convinced it would not work - why would I need to calculate the bootstrap max of the sample when I can simply find the max without calculation (unlike mean). AI did help me with this, telling me that bootstrapping the max is still valuable in assessing variability and uncertainty.

## 8. References

List all datasets, tools, libraries, or papers you cited.
https://www.pgatour.com/stats/detail/101
https://forefathers.medium.com/how-bryson-dechambeau-gained-45lbs-and-45-yards-in-9-months-79fc624ab717
https://claude.ai/share/9d10c217-f71b-4290-b4a8-f05a585cf65c

---

**Reminder:** Your README should be clear enough that someone unfamiliar with your work could understand what you studied, how you analyzed it, and what you found.
