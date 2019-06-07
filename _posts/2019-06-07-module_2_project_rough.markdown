---
layout: post
title:      "Module 2 Project (Rough)"
date:       2019-06-07 20:49:24 +0000
permalink:  module_2_project_rough
---

## Generating Hypotheses to Test, Execution Process, Extracting Business Value

To illustrate the process of how the hypothesis tests were generated, executed, and how conclusions were taken from them, I will be explaining the using my second question of "Does an employee's age have a significant effect on their performance?" as a case study.

### What to Analyze?
The first step was to select the hypothesis for testing. This was done from a business perspective by proposing a question whose answer could provide an insight to help the company perform more efficiently given the information at hand. 

### Data extraction
The second step was to extract the relevant information for our test from the database - employee ages and orders processed. To determine employee ages, each row in the BirthDate column of the employee table was subtracted by the current year of the company's operation (determined by the most recent order shipped). This was done by using a SQL query to select the relevant information from the database, passing the results to a dataframe, slicing out the year from each row in the BirthDate column, passing it to a list, and finally looping through this list of birth years to perform the substractions to calculate age, each of which was appended to a seperate list to have readily accessible for the next step. Steps 1, 2 and 4 of the aforementioned process were repeated for the orders column, with a notable exception of using the COUNT operator on the Id column in the SELECT clause of our SQL query in to get the total amount of orders from each employee in our new column.

### What Hypothesis test to use?
Two options were considered on how to best test this hypothesis. The first option considered was to perform multiple cohen's d tests to determine whether there is a significant difference in the mean number of orders processed between each age. This option is more rigorous for selecting for each individual age, however is very limited by sample size. The second option considered was to use an ANOVA test, which would better account for variance but require the data to be separated into groups which could potentially limit the granularity of the analysis.

To properly weigh the pros and cons of each, a close look was taken at the data:

Ages: [16, 19, 19, 22, 24, 27, 30, 34, 45] 
Orders: [127,  67,  43, 42, 72, 104, 123, 96, 156]

From this we can see that performing Cohen's d for each would be quite unfeasible because of the extremely small sample size of each age population of 1 which would make the results highly subject to noise from variance. For this reason it was determined that the loss in granularity is outweighed by the ANOVA test's ability to account for variance, so ANOVA was chosen.

### Execution of Hypothesis Test

