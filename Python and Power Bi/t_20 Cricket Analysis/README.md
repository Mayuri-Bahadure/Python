# T_20 Cricket Analysis

### Dashboard Link : https://drive.google.com/file/d/1QSqBpqziDOtx7pZdDI7qwTY9sgqlxJE-/view?usp=drivesdk

## Problem Statement

This projects finds the best 11 players on the basis of T 20 Cricket performance 2022. The players are selected on the basis of top 12 teams which perform well. The players are selected on the basis of their speciality in playing and on the basis of batting order. 

## Data Prepration using Python
For data preparation their is 4 different JSON files which was converted to the csv. Following steps are followed to data prepration:
- Step 1: Import necessary libraries : 
In this step pandas and json libraries are imported. Then JSON file uploaded to the jupyter notebook.
- Step 2: Process Match results:
In this step the Match results JSON file processed to csv. In this step the column name 'scorecard' is used to link the tables. The dictionary was created to create unique match ids. And then the file converted to csv.
- Step 3: Process Batting Summary:
In this step the JSON file name batting summary is processed. The new column out/not_out is created in this step. Then some column contains weired character that character was removed. And then it connected to the match result table using match id column.
- Step 4: Process bowling summary:
- Step 5: Process Players Information

## Data Visualization using Power Bi
### Steps followed 

## Data Transformation:
- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor and Make dupliacte files to crate four different tables, rename the tables as "dim-players", "dim-match_summary", "fact_bowling_sumary", "fact_batting_summary" .
- Step 3 : Run the operations to remove duplicates from the columns and rows from the dim_players table.
- Step 4 : Create new column with conditional formatting named as stage on the basis of match date in table dim_match_summary. This column help to connect with other tables. 
- Step 5 : In fact_bowling_summary table rename few columns. For calculating different statics for bowling performance their is need to do some transformation to do that create new column called balls.
- Step 6 : In fact_batting_summary, the transformation is done on out/not_out column if player is out then value is 1 and if player is not out then value is 0.
- Step 7 : In fact_batting_summary remove extra characters from the players name. 

### Data Modeling:
- In this step to connect dim_player table with other tables the bowler name in the fact_bowling_summary table contains bowlername column same as column called as name in dim_player table.
- And to connect dim_player table with fact_batting_batting_summary table contains column batsmanname same as column called as name in dim_player table.

### Building parameters using DAX:
- Step 1: Create a folder called as key measures. In this folder for visuallization following measures are calculated.
#### Measures in table fact_Batting_summary using DAX formulas:
1) Total Runs = SUM(fact_batting_summary[runs]).
2) Total Innings Batted = COUNT(fact_batting_summary[match_id]).
3) Total Innings Dismissed = SUM(fact_batting_summary[out]).
4) batting Average = DIVIDE([Total Runs],[Total Innings Dismissed],0).
5) total balls faced =  sum(fact_batting_summary[balls])
6) strike rate = divide([total runs],[total balls faced],0}*100)
7) Batting Position = ROUNDUP(AVERAGE(fact_batting_summary[batting_pos]),0)
8) Batting Position = ROUNDUP(AVERAGE(fact_batting_summary[batting_pos]),0)
9) Average Balls Faced = AVERAGE(fact_batting_summary[balls])

#### Measures in table fact_Bowling_summary using DAX formulas:
1) wickets = SUM(fact_bowling_summary[wickets])
2) balls Bowled = SUM(fact_bowling_summary[balls])
3) Runs Conceded = SUM(fact_bowling_summary[runs])
4) Economy = DIVIDE( [Runs Conceded], ([balls Bowled]/6),0)
5) Bowling Strike Rate = DIVIDE([balls Bowled], [wickets],0)
6) Bowling Average = DIVIDE([Runs Conceded],[wickets],0)
7) Total Innings Bowled = DISTINCTCOUNT(fact_bowling_summary[match_id])
8) Dot ball % = DIVIDE(SUM(fact_bowling_summary[zeros]), SUM(fact_bowling_summary[balls]),0)

#### Other Measures:
1) Player Selection = if(ISFILTERED(dim_player[name]),"1","0")
2) Display Text = if([Player Selection] = "1", " " ,"Select Player(s) by clicking 
the player’s name to see their individual or combined strength.")
3) Color Callout Value = if([Player Selection]="0", "#D0CF1D","#1D1D2E")

### Visualization:
#### Raw Visuals: 
- Power Hiters Page: This page shows 5 best openers.
- Step 1 : To create the table on this page apply following criterias on parameters:
1) Batting Average > 30
2) Strike Rate > 140
3) Innings Batted > 3
4) Boundary % > 50
5) Batting Position < 4
- Step 2: Create a Scattered graph for better visuallization.
- Step 3: Add button Qulifier or Super 12 for more interactive visualization
- Step 4: Add Card visualization of batting avg, avg balls faced, batting s/r, boundry%

- Anchors/ Middle Order Page : 
- Step 1 : To create the table on this page apply following criterias on parameters:
1) Batting Average > 40
2) strike rate > 125
3) innings batted > 3
4) avg. balls faced > 20
5) batting position > 2
- Step 2: Create a Scattered graph for better visuallization.
- Step 3: Add button Qulifier or Super 12 for more interactive visualization
- Step 4: Add Card visualization of batting avg, avg balls faced, batting s/r, boundry%

- Finisher/ Lower Anchor Page:
- Step 1 : To create the table on this page apply following criterias on parameters:
1) Batting Average > 25
2) Strike Rate > 130
3) Innings Batted > 3
4) Avg. Balls Faced > 12
5) Batting Position > 4
6) Innings Bowled > 1
- Step 2: Create a Scattered graph for better visuallization.
- Step 3: Add button Qulifier or Super 12 for more interactive visualization
- Step 4: Add Card visualization of batting avg, avg balls faced, batting s/r, bowling s/r

- All- Rounders/ Lower Order Page:
- Step 1 : To create the table on this page apply following criterias on parameters:
1) Batting Average > 15
2) Strike Rate > 140
3) Innings Batted > 2
4) Batting Position > 4
5) Innings Bowled > 2
6) Bowling Economy < 7
7) Bowling Strike Rate < 20
- Step 2: Create a Scattered graph for better visuallization.
- Step 3: Add button Qulifier or Super 12 for more interactive visualization
- Step 4: Add Card visualization of bowling avg, economy, batting s/r, bowling s/r

- Specialist Fast Bowlers page:
- Step 1 : To create the table on this page apply following criterias on parameters:
1) Innings Bowled > 4
2) Bowling Economy < 7
3) Bowling Strike Rate < 16
4) Bowling Style = %fast%
5) Bowling Average < 20
6) Dot Ball % > 40
- Step 2: Create a Scattered graph for better visuallization.
- Step 3: Add button Qulifier or Super 12 for more interactive visualization
- Step 4: Add Card visualization of bowling avg, economy,bowling s/r, dot ball %

- final team page:
This page contain slicer and table visualization. This is hidden page in this dashboard and it will help to intractive visualization later.

#### Interactive Dashboard:
For interactive dashoard the buttons are added on the top of first page to create nevigation between pages.
The tool tip was added to all visualization to get more information about players. The tool tip is connected to the report pages.

### Analysis and Selecting Final 11 Players:
- 1) Openers:
From the openers performance the two players are selected Jos Buttler and Rilee Rossouw. Acoording to their performance the partnership of both if they face 120 balls they will give 180 runs. And they can stand atleast four hours on an average. And they score runs 60% in Boundries.

- 2) Anchors:
From the Anchors performance Virat Kohli and Suryakumar Yadav are best player for 3rd and 4th position. Their partnership can contribute more runs. And for 5th position Glein Phillips he ha sstrike rate of 160 and he scores at an average 40.

- 3) Batting Allrounder:
For the 6th position Marcous Stoinis is good player beacause he has also good strike rate.He will also help to impeove batting average of allover team.

- 4) All Rounder:
Sikandar Raza is good player for the number 7th positionbecause his strike rate is 147 and he also has very high batting average.
Shabab Khan is the best player for 8th position he was good at bowling as well as in batting too.

- 5) Fast Bowlers:
On the 9th position their is need of good bowler so Sam Curran is best for this position because his economy is 6.53, and his bowling average is 11.38. On an average he gets wickets on every 11 runs.
For number 10th Position Anrich Nortje he has got 11 wickets at an economy of 5.37 and he gives less than six runs in over.
Shaheen Shah Afridi is should be on 11th position he also a good bowler and he can also a good batsman too.
