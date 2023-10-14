# Analysis of Video Game Data to Inform Decisions for a Start Up Company
## Overview of Scenario
You are a junior data analyst and a video game start up has approached you requesting your aid. They want to create and sell a video game of their own to customers in order to make a profit. However, the company is unable to come a decision as to which type of game they should sell in order to generate the most revenue. Furthermore, they are also not sure of which business model they should use in order to sell the game they create. So, you agree to offer them your services and start your data analysis process.
## 1. Ask Phase
You begin by asking the start up company lots of questions in order to determine how you should proceed with your analysis process. The company's executives collaborate with you and state they want to have the following questions answered:
1.	Which genres of video games are the most popular?
2.	For these genres, would they generate the most revenue for the company?
3.	Which gaming consoles should this game be made available to customers?
## 2. Prepare Phase
### 2a. Metrics Used to Answer Stakeholders' Questions
Now that you have the questions you need to answer from the start up company, you begin to figure the best courses of action to answer your stakeholders' questions. You decide to use the following metrics to help with your analysis:
1.	The number of units sold in millions and comparing this data to the genre of the game.
2.	The number of units sold in millions and comparing this data to the publisher for the game.
3.	Determining the top genres of games sold for each publisher by determining the percentage each accounted for.
### 2b. Data Sets Used, Their Sources, and Credibility
Using these metrics above, you search for the data sets that possess the information you require. You decide to use a total of 3 different data sets. These are listed and described below.
1.	Nintendo Switch Games Data: Shows the top 73 Nintendo Switch games sold from 2017-2022 in terms of year released, units in millions sold (both globallly and in different regions), genre, developer, and publisher.
2.	PS4 Games Data: Shows the data for the top 1034 games sold from 2013-2020 in terms of year released, genre, publisher, and units in millions sold (both globally and in different regions)
3.	XBOX1 Games Data: Shows data for the top 613 games sold in terms of their overall rank, year released, genre, publisher, and units in millions sold (both globally and in different regions)
All data sets used were in csv file format and could be found on the Kaggle website. Furthermore, all data sets used were public data, which means they can be downloaded, copied, and utilized without restriction.

For most of the data sets, the sample size of game titles was pretty large. However, this was not the case for Nintendo Switch Games data. This data set was significantly smaller than the others. This could mean then that the sample of game titles does not represent the overall population compared to the Playstation 4 and XBOX1 game titles. Furthermore, the data for all game titles from each console is unfortunately not as current as it could be. The latest data of game titles was in 2022, while other data sets stop at 2020. 

### 2c. How Each Data Set is Organized
Each csv file used for this analysis was in long format. This is because each row for each data set corresponds to a unique game title that was sold.
## 3. Processing Phase
### 3a. Which Tools to Use for Processing the Data
The smaller csv files contained a few hundred rows of data, while the largest contained just over a 1000 rows of game titles. Thus, to process the data sets, it was decided that Google Sheets would be used.
### 3b. Fixing the Formatting of Dates for Each Data Set
To help complete the analysis by comparing different genres, publishers, and gaming platforms for games sold, the correct year for when each game was released needed to be easily read. However, not all columns of the year release were formatted consistently. So, the following steps were taken to ensure the readability and consistency for this data:
1.	For the PS4 and XBOX1 data sets, the columns giving the release year for each game was renamed to "Year Released".
2.	For the Nintendo Switch data set, the original column, named "release_date", had the full date in the format MM/DD/YYYY. Only the year was required though. So, in a separate column, the YEAR function was used to extract only the year. And, this new column was titled "Year Released" to keep it consistent with the PS4 and XBOX1 data sets.
### 3c. Removing Duplicate Rows for Game Titles and Deleting Rows with Blank Information
For every data set, each row corresponded to a single, unique game title. However, each data set needed to be checked for duplicate rows that had the same video game title. And, some were found to have some duplicate rows. 
1. 3 duplicate rows were found for video game titles in the PS4 Game Sales file. Those duplicate rows in the data set were then removed.
2. 1 duplicate row for game titles in XBOX1 games file was found and removed.
3. No duplicates rows for game titles were found in the Nintendo Switch games spreadsheet file.

There were 208 PS4 game title rows that had no year the game was released, as well as not having the name of the publisher in its information for each game when a search was done by organizing the data sheet in order by publisher. So, these data rows were deleted. 

### 3d. Editing of Column Names and Creation of New Columns for Publisher, Genre, and Total Copies Sold
1.	All column titles for names of games were renamed to "Game Title"
2.	All other titles to be used for data analysis were checked and edited to make sure all had the exact same names (including to check for capitalization).
3.	A new column was created for each data set that read "Total_Copies_Sold (mil)" where all used the same formatting of the numbers.

## 4. Analyze Phase

Now that the data processing was complete, it was time to begin the analysis. So, the following things were used in order to have more concrete answers to stakeholders' questions:

1. A pivot table was created for each data set to determine trends for genre of video games sold and the total number of copies games sold for each genre.
2. To help visulize these data trends, a bar chart was created that showed the top genres in total games sold from each gaming console data set.

![image](https://github.com/nightowl8908/Data-Analysis-Portfolio/assets/146215343/6fb78b89-7797-4b5b-8629-8c26565ed13a)

![image](https://github.com/nightowl8908/Data-Analysis-Portfolio/assets/146215343/8f7cef6f-fb02-41b6-92dc-4c3206d2b9d0)

![image](https://github.com/nightowl8908/Data-Analysis-Portfolio/assets/146215343/93cbfd09-473a-4fd7-a38f-1fc6f80ebf82)

3. Another pivot table was created for each data set to determine trends when comparing the publishers and the total number of copies for games sold.
4. To help visualize these data trends, another bar chart was created that showed the publishers who sold the most number of games from each gaming console.

![image](https://github.com/nightowl8908/Data-Analysis-Portfolio/assets/146215343/867190cc-950a-445e-8e63-755b0261030a)

![image](https://github.com/nightowl8908/Data-Analysis-Portfolio/assets/146215343/f252f503-3440-49e3-be59-19d8d5b206c5)

![image](https://github.com/nightowl8908/Data-Analysis-Portfolio/assets/146215343/241a911e-c4bb-4226-8ca7-9744fab266bd)
   
5. Finally, a third pivot table was created for each data set that gave a breakdown of the different publishers for video games, every genre of video games that each publisher sold, and the total sum of games sold that come from each genre. 

## 5. Share Phase 
After analyzing data from the pivot tables and bar charts, the following conclusions can be drawn:

- The top 3 genres by total number of game copies sold for the Nintendo Switch (from #1 to #3) were Platformer, Role-Playing, and Action-adventure.
- The top 3 genres by total number of game copies sold for the Playstation 4 (from #1 to #3) were Action, Shooter, and Sports.  
- The top 3 genres by total number of game copies sold for the XBOX1 (from #1 to #3) were Shooter, Action, and Sports.
- The top publishers of games for the Nintendo Switch was Nintendo at #1 (by a wide margin) and then second with the Pokemon Company.
- The top publishers of games for the Playstation 4 (from #1 to #3) were Activision, Ubisoft, and Electronic Arts.
- The top publishers of games for the XBOX1 (from #1 to #3) were Microsoft Studios, Activision, and Ubisoft.

## 6. Act Phase

Based on the trends found above, an analyst could give the following recommendations to a new video game developer wishing to create a new game for the martket:

- The company should start creating an action genre video game. This genre was in the one of the top 2 spots for most video games sold for 2 of the 3 biggest gaming consoles. So, developing an video game that would fall under the action genre is the safest bet in order to create a profit.
- The company should develop their video game to be played on all 3 different gaming consoles. The rationale for this is that the majority of gamers do not possess all 3 of the current, major consoles. So, developing and marketing the game to be able to played on any of those consoles would potentially lead to a much greater profit for the new video game developer.
- Finally, it is recommended that the new developer goes to the following publishers in order to be able to sell a great many copies of their game and make a larger profit: Nintendo for the Nintendo Switch console, Activision for the Playstation 4 console, and Microsoft Studios for the XBOX1 console. All of these publishers have lots of experience selling action genre game titles and have had many successes doing so.   

