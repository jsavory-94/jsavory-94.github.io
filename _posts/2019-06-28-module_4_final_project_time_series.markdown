---
layout: post
title:      "Module 4 Final Project: Time Series"
date:       2019-06-28 16:50:39 -0400
permalink:  module_4_final_project_time_series
---


**Summary**
The process for generating this time series model performed the following steps on the data, in order: 
   1. pre-processing 
   2. determining the best 5 zip codes for investment
   3. visualizing
   4. modeling
   5. interpreting results and formulating conclusions


**Step 1: Pre-Processing**
After performing the standard initial step of reading in the csv file containing the data as a dataframe, we are faced with the task of transforming it into a format that can be modeled. 

The first step of my transformation process was to ensure each column had the appropriate datatype. Noticeably, there were two important categorical variables which represented the ID and zipcode of each house in the dataset respectively that were stored as an integer datatype. To correct this each was converted to a string. 

The third instance of incorrect datatype occured in each of the data's date columns which were stored as strings. Using Pandas' datetime module, a custom function was created to convert each back to type dateTime when needed. This was especially useful for step 2 where the delta in time needed to be calculated to forumulate annual metrics on investment growth.

**Step 2: Determining the Best 5 Zip Codes for Investment**
My definition for the best zip codes for investment was - which have been most profitable historically? 

Because determinants of real estate demand such as demographic shifts, interest rates, health of the economy, and government policies are time relevant, profitability was weighted more heavily the more recently it took place. 

The measurement chosen to measure the profitability part of  our best definition was Return on Investment (ROI),  which calculates the percentage increase/decrease of an investment's value over a given time period. ROI was chosen due to how well it fits what is needed for our analysis - its benefits of being a simple and standardized measure of profitability makes it an ideal tool for efficiently comparing our different investments. Its main limitation of not accounting for the holding period is also mitigated due to the fact that the investments we're comparing are all of the same time period. 

The ROI will be implemented 
