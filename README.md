# PyBer Analysis Report

## CHALLENGE
This weeks challenge has three parts: 
- two technical analyses
- a written report that delivers your results to the CEO.

Technical Analysis Deliverable 1:
- A DataFrame that summarizes the key metrics for the ride-sharing data by city type. 
- See **PyBer.ipynb** Jupyter Notebook

Technical Analysis Deliverable 2: 
- A multiple-line chart, with one line for each city type, that shows the sum of the fares for each week. 
- See **PyBer.ipynb** Jupyter Notebook

Delivering Results: 
- A written report of your results, saved in a README.md document on your GitHub repository. 
- See this **README**

## Background and Results
Module 5 set up the initial analysis for PyBer using the Matplotlib library to plot various graph views of the PyBer data set

### Purpose
The purpose of this challenge is to provide a technical analysis and written report for the ride-sharing data. In particular we provide:
- a summary of the key metrics for the ride-sharing data by city type
- a vizualization of the total fares for each week by each city type
- a written report
  - on the results of the new analysis
  - challenges encountered and overcame during the analysis
  - future recommendations for analysis

### Technical Analysis
We first produced a DataFrame to summarize the key metrics by City Type (Urban, Suburban & Rural) as follows:
- Total Rides
- Total Drivers
- Total Fares
- Average Fare per Ride ( = Total Fares / Total Rides )
- Average Fare per Driver ( = Total Fares / Total of Drivers )

We then produced a multiline chart showing the weekly total fares per City Type for the time period indicated:
- 2019-01-01 to 2019-04-28

### Results

We can say the following with respect to the ride-sharing data across the City Type category.

**Key Metrics Summary DataFrame**
Based on the summary we can readily see the following:
- The Urban rides account for approximatly 68% of the rides (total=2,375) provided by the service, but account for approx 63% of the overall fares (total approx $63k (rounding up to 1,000)).
- The Suburban rides account for approx 26% of the rides and 30% of the fares.
- The Rural rides account for approx 5% of the rides and 6% of the fares.
  - This corresponds with the Pie charts produced during the module portion of the analysis.
- The urban ave fare per driver is less than the average fare per ride, perhaps due to there being fewer active drivers than the stated Urban driver total.
  - Looking at the number of rides versus the number of drivers, there are at least one third of the urban drivers who did not provide any rides
  - Further analysis is required to determine the actual number of active drivers (start with the Urban category)
- Comparing the average fare per Rural and Suburban driver vs the fare per ride, the fare per driver is lower. 
  - This suggests that rides and fares are not evenly distributed amongst the drivers.
  - Further analysis required to understand distribution of rides & fares amongst drivers.

The following figure is a screenshot of the summary dataframe.
![Summary DataFrame of Key Metrics](https://github.com/damiencorr/PyBer_Analysis/blob/master/analysis/Fig9%20-%20Screenshot.jpg)

Total Fares by City Type multiple-line graph
- Observing the start and end of the 4 month period, both Urban & Suburan weekly fares finished higher than the start of the period.
  - Urban fares finished up approx 24% (start-finish difference approx 2250-1700 = $500), with the last half of the final month trending downwards.
  - Suburban fares finished up approx 45% (start-finish diff approx 1400-750 = $650), with the last half of the month trending upwards
- Rural fares remained flat at the finish of the period
- All types saw a bump around the same week towards the end of Feb
  - Further investigation required to determine what might have been hapening in the company and the market at that time
- Before that end of Feb peak Urban saw a relatively steady increase, Suburban saw an increase but then declined
- Rural was bumping along and more erratic, likely due to lower usage resulting in more noticable variation.
- Post the end of Feb peak Urban saw-tooth declined gradually, Suburban declined more quickly and Rural declined to a lesser degree.
- Another feature of note is in April both Urban & Rural experienced a peak, both declined from that point
- And final feature a week later Suburban's decline reversed & the increase sustained until the end of period
  - Further investigation required to determine any company or external actions correlate to the peaks & trough.
  
The following figure is the multiline graph saved from the notebook.
![Weekly total fares per City Type](https://github.com/damiencorr/PyBer_Analysis/blob/master/analysis/Fig8.png)

### Summary
From the key metrics summary we note that:
- the Urban category accounts for the main share of, drivers, rides and fares.
- The number of active drivers should be determined to help improve analysis of correlations
- The distribution of rides & fares amongst drivers should be analysed

From the line graph for the selected period we note that:
- Both Urban & Suburban weekly total fares increased over the selected period
- There are peaks which may correlate with company and/or market events

## Challenges Encountered and Overcome

### Challenges and Difficulties Encountered

* Programming
- Jupyter Notebooks enabled with matplotlib inline graphing is a very powerful rapid vizualization capability!
- Merging data frames requires understanding join types and selection of suitable columns to join on
- Be aware of options to determine central tendency in the data, depending on whether or not you are working in python/VS Code or Jupyter Notebook environments.
- Central tendency measures can be revealed using the  .describe() method
- Pivot is a convenient way to transpose a dataframe table
- It is straightforward to change the index associated with an existing dataframe, to specify the index when creating a new dataframe, and to reset a dataframe's index back to a default integer index

* Data analysis
- Use groupby with sum & count to summarize data by categories, and cmpare the summaries across the categories 
- Use pivot to transpose data to enable a timeseries analysis across categories
- Use .loc to slice out a range of data and .resample to specify timeseries bins, in this case weekly

* Graphing, etc
- Employ bubble charts to display x,y, + additional attribute, also display multiple series of data on the same shart
- Use the BoxPlot to visualize the measures of central tendency. Also display multiple series on the same chart
- Calculate %'ages and display using pie charts
- MATLAB style of graphing mimics an existing graphing package enabling someone familiar with it to readily engage with matplotlib to produce plots
- Matplotlib's object oriented style of graphing provides for more flexible coding, though is a little more complicated to use
- Detailed control of every element of a plot is possible, including major & minor tick intervals & labels, and formatting and placement of labels/legends elements

### Technical Analyses Used
Module work
- Calculation of tabular summary totals and central tendencies aross City Type category
- Box & Whisker plot visualizations by categor
- Pie Chart visualizations of summary totals by category
Challenge
- Tabular key metrics as summary totals across category
- Total Fares per week as a timeseries visual for the specified four month time period

## Recommendations and Next Steps

### Recommendations for Future Analysis

There are a few questions should be considered for further analysis.
- Are there fewer active drivers than the stated Urban driver tota?
- What is the distribution of rides and fares amongst the drivers in each category?
- What was hapening before or at the time that weekly fare totals increased, in unison or seperately, across the City Type categories?

### Additional Analysis 1

* Add Unique Driver ID to determine distribution of rides/fares across drivers
Are there fewer active drivers than the stated Urban driver total?
- Include a unique driver ID to inspect per driver ride/fare activity

* Technical Steps
- Reprovide the ride data CSV file, this time including a column with a unique identifier for each driver
- Produce a new Drivers data CSV file, using the unique identifer as the primary key
- Read the new ride and driver data files, create & then merge into one dataframe
- Filter for those drivers with NO rides/fares data
- Determine and establish bins for ranges of rides and fares across drivers

### Additional Analysis 2

* Scan the company and environment to identify events and indicate correlations with weekly fare total changes
What was hapening before or at the time that weekly fare totals increased, in unison or seperately, across the City Type categories?
- Further analysis will require examining factors outside the provided data, i.e.
  - actions taken by the company, e.g. marketing campaigns, product/policy changes
  - events in the marketplace, e.g. seasonal factors, major events impacting travel, competition changes

* Technical Steps
- Once determined, mark up timeseries lines with indicators to denote possible correlations with totals increase or decreases


## APPENDIX - CHALLENGE SPEC
### Delivering Results
To deliver the results of your analysis, you will submit a written analysis created for your CEO, V. Isualize, in the form of a README.md file on your GitHub repository. In your README.md, you should have three paragraphs consisting of 4 to 5 sentences each.
The first paragraph should include the following:
- Describe the purpose, or the reason, you did this assignment.
### Challenges and difficulties encountered
- If none, then briefly explain what challenges or difficulties may be encountered and how to avoid them using technical analysis.
- Explain how you overcame any challenges or difficulties, and include what technical analysis you use to overcome the challenges or difficulties.
### Recomendations
- Based on the data from the different city types, what recommendations would you give the CEO for addressing any disparities among the city types?
- Provide two additional analyses you could do to gain more insight into the data, like using other datasets.
- What technical steps would you take to perform the additional analyses?
