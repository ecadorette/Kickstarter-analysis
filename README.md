# KickstarterAnalysis
Module1-performing analysis on kickstarter data to uncover trends

## Overview of Project
The purpose of this analysis is to assist Louise with her research on campains funded through Kickstarter from 2009-2017, specifically for plays. Various factors have been evaluated including country of origin, pledged amounts, the initial goal, and the ultimate outcome of the campaigns.

## Analysis and Challenges
### A Broader View
Investigation initially began with the categories and subcategories of the campaigns. Noting that campaign success changed drastically between countries was useful information but ultimately not enough to help Lousie. 

Louise is looking to raise money for a play, her main concerns are:
1. What time of the year the most successful campaigns began
2. How much capital she can ask backers for 

### Digging Deeper
At this stage in the game it was time for some data cleanup. The "deadline" and "launched_at" columns contained Unix timestamps. These timestamps were converted to human-readable dates by using the following formula.
```
=(((J2/60)/60)/24)+DATE(1970,1,1)
```
Now the data can be charted to see when the sucessfull campaigns started. Reviewing the below graph, we can determine that the largest number of successful campaigns started around May-June. 

![Outcomes Based on Launch Date](https://user-images.githubusercontent.com/114450503/197663146-2fd1c88d-ea00-4c39-bfdb-421c26ee3386.png)

### Next Steps
The "when" has been answered. Now for "how much?". In order to find that out more anaysis was needed. It started with some statistical analysis between successful and failed campaigns to see if backers weren't willing to spend above a certain threshold. Some basic measures were used, including:
- Mean
- Mode
- Median
- Standard Deviation
- Reviewing of Outliers

![Descriptive Statistics](https://user-images.githubusercontent.com/114450503/197663324-d3e3f5db-1784-4b85-a801-fd9e40a9678a.png)

The final piece was reviewing the successful and failed campaigns based on price. This was done by filtering the data by successful, failed, and canceled campagins by banded goal amounts. The filtering was completed using `sumifs` functions. The percentages of successful/failed/canceled outcomes was then calculated and we could produce the resulting graph. 

![Outcomes_vs_ Goals](https://user-images.githubusercontent.com/114450503/197664822-c1852aef-1ec8-4923-a87f-9aff05a54a3e.png)

While there were no roadblocks during this analysis there were some opportunities for miscalculations. When working with banded amounts and greater/less than symbols, there always runs a chance of one small typo in the banded $$ amounts or the <> carrots that can cause all sorts of downstream issues. 

## Results

#### Two Conclusions from the "Theater Outcomes by Launch Date" Chart:
1. Late spring/early summer does seem to be the best time to launch a campaign. 
2. When reviewing the data by year instead of as a whole, the data becomes more skewed as the majority of campaigns captured in this dataset are from 2014-2016. If Louise is looking to launch in 2018 and only 10 campaigns ran the year prior, that seems like a potential risk and room for error in the overall analysis. 

#### A Conclusion from the "Outcome based on Goals" Chart:
This chart suggests Louise's best chance of success is to set her goal at 1000 or less. However, the Outcome based on Goals chart is very misleading. It suggests campaigns that ask for less than 1000 and between 35000 and 39999 have had the most success. If I was Louise, the 35000 to 39999 bracket would intrigue me, maybe I would get greedy and shoot for a larger campaign goal than less than 1000. It isn't until you look at the raw data that you see the 35000 to 39999 bracket only consists of 6 campaigns and the less than 1000 bracket includes 186. This chart would only be useful if the data it's based on was also included. 

#### Limitations to the Dataset:
There is a lack of marketing data provided. I would imagine a large factor of campagining is the medium(s) used to market the campaign (social media, newspapers, mail, etc.) and who actually pledged (millennials, boomers, urban dwellers, gym-junkies, etc.). Louise will want to be sure she is targeting the correct demographic and reaching out to those people in a way that will get their attention. 

#### Other tables that could be useful...
-Comparing the duration of the campaign to the success of the campain. For instance, maybe the May-June campaigns did so well because they had the longest run-times. 

-Mapping out successful campaigns by location/country. Maybe there's an opportunity for plays in France that she hasn't considered.
