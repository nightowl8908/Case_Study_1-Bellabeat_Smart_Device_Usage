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

# COMMENT ON DATA'S CREDIBILITY HERE!!

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
2. 1 duplicate row for game titles in xbox1 games file was found and removed.
3. No duplicates rows for game title was found in the PC Games spreadsheet file.

There were 208 PS4 game title rows that had no year the game was released, as well as not having the name of the publisher in its information for each game when a search was done by organizing the data sheet in order by publisher. So, these data rows were deleted. 

### 3d. Editing of Column Names and Creation of New Columns for Publisher, Genre, and Total Copies Sold
1.	All column titles for names of games were renamed to "Game Title"
2.	All other titles to be used for data analysis were checked and edited to make sure all had the exact same names (including to check for capitalization).
3.	A new column was created for each data set that read "Total_Copies_Sold (mil)" where all used the same formatting of the numbers.

## 4. Analyze Phase


