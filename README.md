# Global Energy Transition Analysis: Growth vs. Decline (2000–2020)  
Data Source: Compiled dataset hosted on [Kaggle](https://www.kaggle.com/datasets/anshtanwar/global-data-on-sustainable-energy), aggregating global metrics from the World Bank, the International Energy Agency (IEA) and Our World in Data (SDG 7).  

### By Nurul Athirah  

## Executive Summary  

Problem: Analysing the global energy transition using raw generation volumes (TWh) makes the growth of renewable energy appear deceptively slow. Because fossil fuels dominate absolute capacity, raw volume scaling hides the true structural velocity of clean energy adoption.
Goal: To look past absolute baseline sizes by normalizing the data into grid percentages. This analysis aims to accurately measure, visualize, and statistically analyze the relative growth rate of renewable deployment against fossil fuel dependency across a 20-year timeline (2000–2020).

### Tech Stack & Tools:  

* Language: Python  
* Libraries: Pandas, NumPy, Matplotlib
* Kaggle Notebooks (Cloud-based Jupyter environment)

## Data Cleaning & Transformation Pipeline  

Here is how the data was transformed from a messy raw file into a high-quality analysis:  

1. Column Type Conversion: The `Density\\n(P/Km2)` column was showing up as an `object` (text) because of formatting issues. Cleaned the string characters and forced the column type to a float/numeric data type using Pandas.
2. Null Values (Missing Data): Investigated the null values and dropped the columns that are **missing more than 25% of its data** as they can threatened the completeness of the project and introduce massive bias.
3. Duplicate Rows: Ran a global duplicate verification check across key tracking columns and confirmed the dataset was **100% unique**. It is to ensures that every country has exactly one record per year, protecting the integrity of all calculations.

### The Calculation Pipeline:  

1. Get Percentage Share: <br> Combined the total of two column (Electricity from renewables (TWh) & Electricity from fossil fuels (TWh)) to find Total Generation, then calculated each source's percentage out of this total.
2. Find Global Average: Used Pandas `.groupby('Year').mean()` to calculate the average of the countries' percentages for each respective year. This condenses thousands of country rows into a single global timeline.
3. Index Baseline (Year 2000 = 100): Used `.iloc[0]` to extract the very first row of this chronological timeline which is the global average for the year 2000 and used it as a locked mathematical divisor. Every subsequent year's average was divided by this year 2000 baseline value, then multiplied by 100. Because the year 2000 divides by itself, it naturally quantified at exactly 100.
4. Correlation Coefficient: Mathematically verified that the renewables actively replacing the fossil fuels. A negative correlation (close to -1) confirmed that there is an inverse relationship between the growth of renewable energy and the fossil fuels reliance.

## Data Insights  

![Energy Transition Gap](./energy_transition_chart.png)  

1. Steady Transition: Both lines started out moving in gradual, steady slopes rather than sudden spikes. <br> Because energy relies on massive physical power grids and factories, change takes time.
2. Turning Point: The year 2012 became a crucial structural turning point for the global energy mix. Prior to 2012, fossil fuel reliance held perfectly steady. Post-2012, renewable growth accelerated upward, marking the exact period where green energy shifted from merely expanding to actively displacing fossil fuels.
4. Growth rate: By 2020, the chart reveals a clear inverse relationship between renewables and fossil fuels energy. Renewables climbed by roughly 15%, while fossil fuels dropped by about 5%. While renewables are scaling up three times faster to capture the vast majority of new global electricity demand, the minor 5% drop in fossil fuels proves that clean energy has not yet completely replaced existing baseline infrastructure.

## Future Analysis Plan  

This multi-dimensional dataset provides an ideal foundation for scaling the analysis across four strategic pillars:

1. Economic Impact: Investigate the relationship between aggressive clean energy adoption by correlating transition velocity against annual GDP growth and GDP per capita.
2. Predictive Modeling: Leverage historical per-capita primary energy consumption to train machine learning forecasting models capable of predicting future global power demands.
3. Environmental Analytics: Quantify the exact displacement efficiency of low-carbon electricity shares in directly reducing metric tons of CO2 emissions per capita.
4. Socio-Demographic: Evaluate infrastructure distribution equity by analyzing how population density impacts a community's access to electricity and clean cooking fuels during a green infrastructure rollout.
