# Kickstarting with Excel

## Overview of Project 

### Purpose
The purpose of this analysis is to discern patterns in the relationships between the outcomes of Kickstarter campaigns and, 
1. The time of year campaigns were started and,
2. The initial funding goal of campaigns. 

This analysis may help to determine the best and worst times of year to start a campaign and to chose a funding goal that can be expected to be successful.

## Analysis and Challenges
This analysis is based on data collected from over 4,000 Kickstarter campaigns launched between 2009 and 2017.

### Analysis of Outcomes Based on Launch Date
#### Timing
The launch and end dates of each campaign were originally provided in Unix timestamps. To convert these timestamps to human-readable data, I used,`[unix timestamp]/60/60/24 + DATE(1970,1,1)`.
From there, I was able to refine my analysis by grouping the campaigns based on the year and month in which they were started. The pivot table below is based off of this data and displays the results of campaigns in the theater parent category based on the month in which they were launched.

<img width="407" alt="Outcomes_vs_Launch_1" src="https://user-images.githubusercontent.com/114126935/194795576-b5ca5d7f-c4d0-4b61-8077-3e41c5a9b624.png">

The following pivot table shows the same data but limited to the year 2015.

<img width="412" alt="Outcomes_vs_Launch_2015" src="https://user-images.githubusercontent.com/114126935/194795627-76050315-38b3-4e32-9834-b67a4fe9ddf2.png">

### Analysis of Outcomes Based on Goals
#### Goal Categories
The original data included the funding goal for each campaign. In order to analyze this information with more depth and relate it to the outcome of each campaign, I organized it based on dollar amount ranges for each goal and whether the campaign was successful, failed, or canceled. To do this, I created a new sheet in Excel that displays these categories. I populated the count for each category using the COUNTIF. One example cell reads `=COUNTIFS(KickStarter!$D:$D,”>=5000”,KickStarter!$D:$D,"<=9999",KickStarter!$F:$F,"failed",KickStarter!$R:$R,"plays")`.
This code allows me to find and filter based on parameters in multiple categories. If all parameters are met, the function increases the count. 
The SUM function and basic division were used from there to determine percentages for each category. 
<img width="717" alt="Goals_Sheet" src="https://user-images.githubusercontent.com/114126935/194795810-6f6e95fc-6e8c-4d4e-b1e5-1c296ebab227.png">

### Challenges and Difficulties Encountered
#### Months in the Pivot Table
It was a challenge to get the pivot table in the Theater Outcomes by Launch Date sheet (pictured above) to display data based on month for all years at the same time. I tried different methods of filtering and formatting the table to no avail. Eventually I figured out that I needed to remove the “years” and “quarters” fields from the “Rows” panel, leaving only “Date Created Conversion.” Excel took care of it from there.

#### Outcomes Based on Goals for Plays Only
At first I did not filter this date based on the plays subcategory. Going back to fix mistakes is often a challenge, especially once a lot of work has been done already. I first tried to filter the “KickStarter” sheet from which the data is derived. That didn’t work. I realized that the my best option was probably to write in a new field for the COUNTIFS function in my new sheet, even if that meant extra busy work. By adding `KickStarter!$R:$R,”plays”` to each function, I was able to filter successfully.

## Results
### Theater Outcomes Based on Launch Date
![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/114126935/194796148-d18a4be1-a1cf-481a-80bd-f2474e3ab2b3.png)

#### Theater KickStarter campaigns are generally successful
This is good news for Louise. A quick look at the above line chart shows us that throughout our entire data set, more campaigns in the theater parent category end “successful” than “failed” or “canceled,” regardless of the moth in which they launch. This suggests that going to Kickstarter in the first place is a good way to get a theater campaign funded. Louise can move forward with increased confidence that she is on the right track. This is a crucial element to success. 

#### May and June might offer special advantages
Prominently appearing in this line chart is the spike in successful campaigns launched in the month of May. May has both the largest number of successful campaigns and the highest ratio of successful to failed campaigns of any month. This ratio can be visualized by looking at the distance between the green and red lines on the chart. The greater the distance, the larger the ratio of successful to failed campaigns. June follows close behind May in these categories. Furthermore, Louise should beware starting her campaign in December, when the successful and failed outcomes are nearly equal (the two lines on the chart almost touch). The data here show that historically, a campaign started in December is nearly equally as likely to fail as to succeed.

### Outcomes Based on Goals
![Outcomes_vs_Goals](https://user-images.githubusercontent.com/114126935/194796254-d9f964c3-b304-4d79-a048-34db62a2c3b6.png)

#### Keep the green line above the red line
In the above chart the green line represents the percentage of successful campaigns in funding goal ranges, and the red line represents the percentage of failed campaigns in the same goal ranges. When the green line is above the red line, a campaign is historically more likely to succeed than to fail. When the red line is above the green line, however, a campaign is historically more likely to fail.

#### Where to set the goal
Based on this analysis, two ranges appear as good targets for Louise’s goal. The first is between $1 and about $15,000. Louise should be aware that in this range, the closer her goal is to $15,000, the lower her chances of success become, based on our dataset. She should increase her goal cautiously. If Louise wants a goal above $15,000, she should consider jumping to a goal as low as $35,000 but not above $44,999. In this range, there is again a historically higher percentage of successful campaigns than failed ones. Above $45,000 is the danger zone where campaigns historically are much more likely to fail than to succeed.

## Limitations of the Dataset
This dataset is limited in that it provides little to no insight about the level of engagement with or size of the team managing individual campaigns. Such information might include, the number of people working on the project, money spent on advertising, time spent on the KickStarter page, number of photos or videos used to aid the project, and any number of other things that may indicate how much work went into the campaign itself. Such factors may be crucial to a successful campaign.

## Other Tables and Graphs
A pie chart may help to visualize the importance of being a “spotlight” campaign. It could be done with only four categories by grouping all live, canceled, and failed campaigns into one “not successful” category. 

A box and whiskers chart of pledged amounts for campaigns in the plays subcategory may help Louise to visualize how much money she can expect to receive if her campaign is similar to others. 
