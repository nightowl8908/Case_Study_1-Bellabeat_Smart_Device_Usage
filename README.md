# Customers' Usage of Bellabeat Smart Devices

# Table of Contents


# 1. Overview of Scenario:

You are a junior data analyst working on the marketing analyst team at Bellabeat, a high-tech manufacturer of health-focused
products for women. Bellabeat is a successful small company, but they have the potential to become a larger player in the
global smart device market. The cofounder and Chief Creative Officer of Bellabeat believes that analyzing smart
device fitness data could help unlock new growth opportunities for the company. You have been asked to focus on one of
Bellabeat’s products and analyze smart device data to gain insight into how consumers are using their smart devices. The
insights you discover will then help guide marketing strategy for the company. You will present your analysis to the Bellabeat
executive team along with your high-level recommendations for Bellabeat’s marketing strategy.

As a junior analyst, I followed the 6 phases of data analytics in order to meet my stakeholders' expectations:

**Ask**, 
**Prepare**, 
**Clean**,
**Analyze**,
**Share**, and
**Act**

# 2. Ask Phase

Bellabeat's Chief Creative Officer asked me to analyze smart device usage data in order to gain some insights as how to customers use smart devices from other companies. 

My goal was to answer the following three questions:

    1. What are some trends in smart device usage?
    2. How could these trends apply to Bellabeat customers?
    3. How could these trends help influence Bellabeat marketing strategy?

# 3. Prepare Phase

## 3a. Data That was Used and Analyzed

Bellabeat's Chief Creative Officer pointed me towards the following data set to use in my analysis: FitBit Fitness Tracker Data (CC0: Public Domain, dataset made available through Mobius). These Kaggle data sets are all stored in csv files. In total, there are 18 of them.  The data is all open source, which means is freely available to anyone in the public and can be edited as needed by those who analyze and use it. So, permission from the original owner of the data is not required to use it for one's own purposes.  


## 3b. How the Data is Organized

After downloading the data sets and storing in the cloud on my RStudio workspace, I wanted to know how the data was organized, as well as its structure. So, I used the structure, head, and n_unique functions in R to better understand this.


# PASTE IMAGE OF R CODE HERE with using head function!! 

From the head function, I was able to determine that all the data is in long format since it is organized by time. The data sets where data was tracked each day were also  organized by day, with each day corresponding to a single row. The other data sets where data was tracked and collected hourly had each hour of the specific day corresponding to a single row. 

# PASTE IMAGE OF R CODE HERE with using structure function!!

From the structure function, I determined that the various data sets had a combination of numeric. integer, and string types of data stored within them.

# PASTE IMAGE OF R CODE HERE with using n_unique function!!

Finally, from the unique function, I determined that there was a total of 31 unique ID numbers within the different data sets. This means that there was a total of 31 different FitBit users' information collected, which tracked their sleep times, steps taken, calories burned, and so on. 

## 3c. Credibility of the Data

Since there are only a total of 31 users whose information was collected for the data, it is likely that there may be some level of sampling bias for this data. Not only that, but there is also no identifiable, demographic information about our users. Therefore, we have no way of knowing if our sample represents the overall population of FitBit's users. One of two things might have occcurred. Most users may have refused to participate in the study, which then lead to non-response bias. Or, this data could have undercoverage bias if certain members of the population are not represented as much as they should be. 

Finally, this data was not collected recently. It was done over a few months back in the year 2016. 

# 4. Cleaning Phase

## 4a. Deciding on RStudio

To clean and analyze the data, I decided to use RStudio. RStudio is able to work easily with much larger data sets than simple spreadsheets can. And, after inputting some simple code, R can perform many types of data analysis in only a matter of seconds. 

## 4b. Fixing the Formatting of Dates

After using the head functions, I noticed that the specific day and time for each data sets where information of users was tracked hourly had both organized into one column. So, I reformatted these in those files and made two, new columns called 'date' and 'time'. I also made a new column in the daily sleep file called 'ActivityDay' that contained only the specific day in which the user slept. I did this because all of the other files which tracked users' activities on a daily basis had the time column named 'ActivityDay' and only told the specific day.  

# PASTE IMAGE OF R CODE HERE where you reformatted the dates!!


## 4c. Merging of Data Sets

I was curious about whether there was a stronger correlation between users' daily activities with the duration of their sleep. So, I decided to merge the data set about users' daily sleep times with a few other data sets that collected information about their daily lives over the course of the study. These data sets included daily_calories, daily_intensities, daily_steps, and daily_activity. 

# PASTE IMAGE OF R CODE HERE where you merged the different data sets!!


# 5. Analyze Phase

## 5a. Determining the Correlation of Sleep Times with Other Variables

Now the data was cleaned, I began my analysis. I started with determining  











    
