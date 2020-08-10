# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Project 1: SAT & ACT Analysis by Vikas Kalia

### Problem statement
There are still many states in the USA which have very low to negligible rate of SAT participation among high schoolers. There is a need for a focussed approach, to improve state level SAT participation across the nation.

### Executive Summary

Objective of this project is to analysis past data of SAT and ACT participation rates across all the states, subject level performance of these test over 2017 & 2018 as well as conduct external research on SAT and ACT participation and state administration and schools's view about the SAT test and its value for their high school students. Extract the trends and insights to device and recommend an approach which is driven by data and successful best practices in the states with higher SAT participation rate, to improve SAT participation rate, state by state.

Contents table below provides the framework used to conduct this study and provide recommendations.

#### Contents:
- 2017 Data Import & Cleaning]
- 2018 Data Import and Cleaning
- Exploratory Data Analysis
- Data Visualisation
- Descriptive and Inferential Statistics
- Outside Research](#Outside-Research)
- [Conclusions and Recommendations

#### Datasets used:
For this project, following datasets were available in the .data/ folder of this project:
- 2017 SAT Scores - /data/sat_2017.csv
- 2017 ACT Scores - /data/act_2017.csv
- 2018 SAT Scores - /data/sat_2018.csv
- 2018 ACT Scores - /data/act_2018_updated.csv

These datasets give average SAT and ACT scores by state, as well as participation rates, for the graduating class of 2017.

**Following steps were taken to prepared a final dataset to conduct exploratory statistical analysis:**
1) First, 2017 SAT and 2018 ACT datasets were converted into pandas DataFrames.
2) Looked for any missing values in these datasets.
3) Explored and compared summary .info() information for number of rows or unexpected data types.
4) Compared this data with the data at the source for any data capture or conversion errors. Kinks to the source data for SAT (https://blog.collegevine.com/here-are-the-average-sat-scores-by-state/ and the source for the ACT data https://blog.prepscholar.com/act-scores-by-state-averages-highs-and-lows
5) A standard naming convention was used to rename the columns.
6) 2017 SAT and 2018 DataFrame  were merged into one DataFrame called called sat_act_2017, with State name as a common key.
7) This sat_act_2017 DataFrame was saved as combined_2017.csv file in ../data/ folder.
8) Then 2018 SAT and 2018 ACT datasets were converted into DataFrames and column names were changed the standard naming convention.
8) After conducting the initial checks and corrections of 2018 SAT and 2018 ACT DataFrames those were merges into one DataFrame called sat_act_18.
9) Finally, sat_act_17 and sat_act_2018 were merged in state name as key into sat_act_final DataFrame which was used for statistical exploration. This DataFrame as also stored as final.csv file in ../data/ folder.     

#### Datasets Created
- ../data/combined_2017.csv - [contains combined SAT and ACT data for 2017]
- ../data/final.csv [contains combined 2017 & 2018 data for both SAT and ACT]

#### Data Dictionary
|Feature|Type|Dataset|Description|
|---|---|---|---|
|state|object|sat_17|Name of the state with SAT score|
|sat17_participation|float|sat_17|Overall SAT participation rate for the state|
|sat17_erw|int|sat_17|Average score for evidence based English - reading and writing in SAT for the state |
|sat17_math|int|sat_17|Average score for math in SAT for the state|
|sat17_total|int|sat_17|Average total SAT score for the state|
|act17_participation|float|act_17|Overall ACT participation rate for the state|
|act17_english|float|act_17|Average score for English in ACT for the state|
|act17_math|float|act_17|Average score for Math in ACT for the state|
|act17_reading|float|act_17|Average score for Reading in ACT for the state|
|act17_science|float|act_17|Average score for Science in ACT for the state|
|act17_composite|float|act_17|Average Composite score in ACT for the state|

**Note: Same naming convention can be used to call these columns for 2018 data.**

**Following steps were taken to conduct exploratory Data Analysis, Data Visualisation & Descriptive and Inferential Statistics:**
- Initial analysis of states, their participation rates, their SAT and ACT scores where reviewed. Using .sort_values and masking methods of pandas, listed states with highest, lowest rate of participation. Also, compared the rate of change from 2017 to 2018 for the SAT participation in each state where some state with interesting statistics emerged.
- Seaborn heatmap graph was plotted to explore correlation among all numerical columns and some interesting corrections were noted for further analysis.
- Next, histograms, scatter plots, box plots and bar charts with distribution curve were plotted and analysed for all participation and test scores, using matplotlib and seaborn libraries.

**External research was also conducted for the news and articles around SAT and ACT specially with those few states of interest in view. Summary of insights from that research was documented.**

#### Conclusions & Recommendations:
As a College Board person responsible for improving the SAT participation across the nation,I have completed the analysis of the past SAT & ACT state level data and conducted an external research. While I don't have sufficient data samples to conduct experiments and provide statistical driven conclusions, however I am documenting following key observations and recommendations.

**Key Observations**


- States with higher SAT participation rate have low ACT participation rate and vice versa.
- The number of states with high ACT participation are much more than number of state with high SAT participation rate
- Number of states with low ACT participation are much fewer than number of states with low SAT participation rate
- States with higher participation rates of SAT or ACT have lower average Total or Composite test scores.
- There are two set of states who are low in their participation rate:
    - States with participation rate below 10%, so in those states their is recognition at the value of SAT test for their high schoolers and
    - States with participation rate ranges between 40 to 60 percent, it would means that some schools are promoting their students to take test and like Florida, they are probably subsiding them as well.
- Two of the key drivers for some recent growth in SAT participation are a) state's sponsorship and b) and school's realisation of the value of SAT test for their students.

**Recommendations**

I recommend a three prong approach and try it on a state like Oregon.

First, college board should work with Oregon state government to help them understand how SAT test will help their high schoolers to get into the better colleges and hence they should support schools to offer SAT for free to their students.

Secondly, work with individual schools in Oregon to encourage them to make it easier for their students to take this test like some school districts did in Florida i.e. to have the SAT test taken during the weekday rather than Saturday. Also, work with schools to increase the alignment of their curriculum with SAT subject tests to give students better chance to score well.

Third, work with colleges in Oregon state to educate and/or convince them on how SAT could improve their student selection process to bring in students with right aptitude and set them up for success in their college education.

Learnings from working with Oregon state should be recorded to adjust our approach for state where there is very very low participation rate.
