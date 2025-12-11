# Project Title

## 1. Research Question

I am investigating the significance of driving distance on the PGA Tour to winning purse money in a tournament. I know this may not advance the common good, as is the mission of St. Thomas, but it's an extremely interesting topic to me and something I am motivated to do analysis on.

** Stretch goal: does driving distance, driving accuracy, or proximity to the hole contribute more to purse money won?
** Time permitting, I'd like to analyze these three performance categories to see which correlates most highly to money earned.

## 2. Hypothesis

Null hypothesis: greater driving distance has no impact on the percent of purse money won.
Alternative hypothesis: the longer average drive/the higher a player ranks in driving distance, the higher percent of purse money they win.


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
     * My test statistic is the mean difference in percent of purse won between "long" hitters (top 25% in driving distance) and "short" hissters (bottom 25%)
* How you simulated or resampled under the null hypothesis
     * I used a permutation test to obtain a reference distribution if driving rank is shuffled among the percent purse won values
* The metric(s) for which you created bootstrap confidence intervals
     * I first used the mean of percent purse won, then used Max (a measure unusable by CLT)
* Why the CLT does not apply to at least one metric
     * CLT does not apply to the Max because it is not an additive value
     * What is interesting is to see the distributino of Max in my histogram. I chose not to use this in my presentation because it is not pretty to look at, but          it's an interesting visual on how a value like Max behaves when bootstrapped, especially on a *relatively* small sample size like i have here (~45).

## 5. Results

Present your main findings:

* Key summary statistics and visualizations
* Observed test statistic and p-value (if applicable)
* Bootstrap confidence intervals for relevant metrics

## 6. Uncertainty Estimation

Discuss your resampling results:

* How many resamples you used
* What the bootstrap or randomization distributions looked like
* How you interpret the interval estimates

## 7. Limitations

Briefly note any limitations in data, assumptions, or methods, including sources of bias or missing data.

## 8. References

List all datasets, tools, libraries, or papers you cited.

---

**Reminder:** Your README should be clear enough that someone unfamiliar with your work could understand what you studied, how you analyzed it, and what you found.
