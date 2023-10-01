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

After downloading the data sets and storing in the cloud on my RStudio workspace, I wanted to know how the data was organized, as well as its structure. So, I used the structure and n_distinct functions in R to better understand this.

    # Determining structure of each data set
    
    str(daily_activity)
    str(daily_calories)
    str(daily_intensities)
    str(daily_sleep)
    str(daily_steps)
    str(hourly_calories)
    str(hourly_intensities)
    str(hourly_steps)
    str(weight_logs)


From the structure function, I was able to determine that all the data is in long format since it is organized by time. The data sets where data was tracked each day were also  organized by day, with each day corresponding to a single row. The other data sets where data was tracked and collected hourly had each hour of the specific day corresponding to a single row. I also determined that the various data sets had a combination of numeric. integer, and string types of data stored within them.

    # Determining the number of FitBit users by counting the number of unique IDs

    n_distinct(daily_activity$Id)
    [1] 33
    n_distinct(daily_calories$Id)
    [1] 33
    n_distinct(daily_intensities$Id)
    [1] 33
    n_distinct(daily_sleep$Id)
    [1] 24
    n_distinct(daily_steps$Id)
    [1] 33
    n_distinct(hourly_calories$Id)
    [1] 33
    n_distinct(hourly_intensities$Id)
    [1] 33
    n_distinct(hourly_steps$Id)
    [1] 33
    n_distinct(weight_logs$Id)
    [1] 8


Finally, from the n_distinct function, I determined that there was a total of 33 unique ID numbers for all the different data sets except for two of them. This means that there was a total of 33 different FitBit users' information collected, which tracked their steps taken, calories burned, and so on. However, the data sets that users' logging their weights on a given day and their daily sleep had only 8 and 24 unique ID numbers respectively.

## 3c. Credibility of the Data

Since there are only a total of 33 users whose information was collected for the data, it is likely that there may be some level of sampling bias for this data. There are no pieces of identifiable, demographic information about our users. Therefore, we have no way of knowing if our sample represents the overall population of FitBit's users. One of two things might have occcurred. Most users may have refused to participate in the study, which then lead to non-response bias. Or, this data could have undercoverage bias if certain members of the population were not represented as much as they should be. 

Finally, this data was not collected recently. It was done over a few months back in the year 2016. 

# 4. Cleaning Phase

## 4a. Deciding on RStudio

To clean and analyze the data, I decided to use RStudio. RStudio is able to work easily with much larger data sets than simple spreadsheets can. And, after inputting some simple code, R can perform many types of data analysis in only a matter of seconds. 

## 4b. Fixing the Formatting of Dates

After using the head functions, I noticed that the specific day and time for each data sets where information of users was tracked hourly had both organized into one column. So, I reformatted these in those files and made two, new columns called 'date' and 'time'. I also made a new column in the daily sleep file called 'ActivityDay' that contained only the specific day in which the user slept. I did this because all of the other files which tracked users' activities on a daily basis had the time column named 'ActivityDay' and only told the specific day.  

    # Cleaning of each data set
    # Reformatting dates
    #daily_sleep
    daily_sleep$SleepDay = as.POSIXct(daily_sleep$SleepDay, format = "%m/%d/%Y  %I:%M:%S %p",tz=Sys.timezone())
    daily_sleep$ActivityDay <- format(daily_sleep$SleepDay, format = "%m/%d/%Y")
 
    # hourly_calories
    hourly_calories$ActivityHour = as.POSIXct(hourly_calories$ActivityHour, format = "%m/%d/%Y  %I:%M:%S %p",tz=Sys.timezone())
    hourly_calories$date <- format(hourly_calories$ActivityHour, format = "%m/%d/%Y")
    hourly_calories$time <- format(hourly_calories$ActivityHour, format = "%H/%M/%S")

    # hourly_intensities
    hourly_intensities$ActivityHour = as.POSIXct(hourly_intensities$ActivityHour, format = "%m/%d/%Y  %I:%M:%S %p",tz=Sys.timezone())
    hourly_intensities$date <- format(hourly_intensities$ActivityHour, format = "%m/%d/%Y")
    hourly_intensities$time <- format(hourly_intensities$ActivityHour, format = "%H/%M/%S")

    # hourly_steps
    hourly_steps$ActivityHour = as.POSIXct(hourly_steps$ActivityHour, format = "%m/%d/%Y  %I:%M:%S %p",tz=Sys.timezone())
    hourly_steps$date <- format(hourly_steps$ActivityHour, format = "%m/%d/%Y")
    hourly_steps$time <- format(hourly_steps$ActivityHour, format = "%H/%M/%S")

    # weight_logs
    weight_logs$Date = as.POSIXct(weight_logs$Date, format = "%m/%d/%Y  %I:%M:%S %p",tz=Sys.timezone())
    weight_logs$date <- format(weight_logs$Date, format = "%m/%d/%Y")
    weight_logs$time <- format(weight_logs$Date, format = "%H/%M/%S")

# 5. Analyze Phase

## 5a. Determining Breakdown of Users' Daily Activities and Amount of Sleep
Now that the data was cleaned, I began my analysis. I started by getting a summary of both the daily_activity and daily_sleep data sets because I wanted to determine the following two things:
- What the breakdown was for how active (or how inactive) users were.
- Whether or not users on average were getting an adequate amount of sleep each night. 

First, I viewed the summary for both data sets.

     # Summary of daily_activity Data Set
    
       Id            ActivityDate         TotalSteps    TotalDistance   
     Min.   :1.504e+09   Length:940         Min.   :    0   Min.   : 0.000  
     1st Qu.:2.320e+09   Class :character   1st Qu.: 3790   1st Qu.: 2.620  
     Median :4.445e+09   Mode  :character   Median : 7406   Median : 5.245  
     Mean   :4.855e+09                      Mean   : 7638   Mean   : 5.490  
     3rd Qu.:6.962e+09                      3rd Qu.:10727   3rd Qu.: 7.713  
     Max.   :8.878e+09                      Max.   :36019   Max.   :28.030  
     
     TrackerDistance  LoggedActivitiesDistance VeryActiveDistance
     Min.   : 0.000   Min.   :0.0000           Min.   : 0.000    
     1st Qu.: 2.620   1st Qu.:0.0000           1st Qu.: 0.000    
     Median : 5.245   Median :0.0000           Median : 0.210    
     Mean   : 5.475   Mean   :0.1082           Mean   : 1.503    
     3rd Qu.: 7.710   3rd Qu.:0.0000           3rd Qu.: 2.053    
     Max.   :28.030   Max.   :4.9421           Max.   :21.920    
     
     ModeratelyActiveDistance LightActiveDistance SedentaryActiveDistance
     Min.   :0.0000           Min.   : 0.000      Min.   :0.000000       
     1st Qu.:0.0000           1st Qu.: 1.945      1st Qu.:0.000000       
     Median :0.2400           Median : 3.365      Median :0.000000       
     Mean   :0.5675           Mean   : 3.341      Mean   :0.001606       
     3rd Qu.:0.8000           3rd Qu.: 4.782      3rd Qu.:0.000000       
     Max.   :6.4800           Max.   :10.710      Max.   :0.110000       
     
     VeryActiveMinutes FairlyActiveMinutes LightlyActiveMinutes SedentaryMinutes
     Min.   :  0.00    Min.   :  0.00      Min.   :  0.0        Min.   :   0.0  
     1st Qu.:  0.00    1st Qu.:  0.00      1st Qu.:127.0        1st Qu.: 729.8  
     Median :  4.00    Median :  6.00      Median :199.0        Median :1057.5  
     Mean   : 21.16    Mean   : 13.56      Mean   :192.8        Mean   : 991.2  
     3rd Qu.: 32.00    3rd Qu.: 19.00      3rd Qu.:264.0        3rd Qu.:1229.5  
     Max.   :210.00    Max.   :143.00      Max.   :518.0        Max.   :1440.0  
    
        Calories   
     Min.   :   0  
     1st Qu.:1828  
     Median :2134  
     Mean   :2304  
     3rd Qu.:2793  
     Max.   :4900  

When looking at the summary for the daily activity data set, I found that both the maximum and mean number of minutes for sedentary minutes were both significantly higher than the other types of minutes. This told me that users, on average, were not particularly active in their day to day.

Then, I wrote code to perform a quick summary for the daily_sleep data set in R. 

     # Summary of daily_sleep Data Set
       Id               SleepDay                      TotalSleepRecords
     Min.   :1.504e+09   Min.   :2016-04-12 00:00:00.00   Min.   :1.000    
     1st Qu.:3.977e+09   1st Qu.:2016-04-19 00:00:00.00   1st Qu.:1.000    
     Median :4.703e+09   Median :2016-04-27 00:00:00.00   Median :1.000    
     Mean   :5.001e+09   Mean   :2016-04-26 12:40:05.80   Mean   :1.119    
     3rd Qu.:6.962e+09   3rd Qu.:2016-05-04 00:00:00.00   3rd Qu.:1.000    
     Max.   :8.792e+09   Max.   :2016-05-12 00:00:00.00   Max.   :3.000    
     
     TotalMinutesAsleep TotalTimeInBed  ActivityDay       
     Min.   : 58.0      Min.   : 61.0   Length:413        
     1st Qu.:361.0      1st Qu.:403.0   Class :character  
     Median :433.0      Median :463.0   Mode  :character  
     Mean   :419.5      Mean   :458.6                     
     3rd Qu.:490.0      3rd Qu.:526.0                     
     Max.   :796.0      Max.   :961.0 

        mean(daily_sleep$TotalMinutesAsleep/60)
        6.991122

The piece of information that was of interest to me in this data was the average amount of sleep users had each night. According to the summary, the average in minutes was 419.5. When I converted this to hours, it was a little less than 7 hours. This piece of information is concerning because it tells me that many of the users in this study were not getting a recommended 8 or more hours of sleep each night. 

## 5b. Determining Time Periods at Which Users Were Most Active

Next, I wanted to determine the time periods at which users in the study were most active. I decided to utlize the hourly_steps data set and made a column chart comparing the hours of the day with the total steps taken for all users.   

    #Determining times of the day at which users are typically are more active
    ggplot(data=hourly_steps, aes(time,StepTotal)) + geom_col() + labs(x ="Time (hours)", y ="Total Steps Taken (all users)") +            
    theme(axis.text.x=element_text(angle=90,hjust=1,vjust=0.5)) + ggtitle("Time vs. Total Steps")

![Time vs  Total Steps Column Chart](https://github.com/nightowl8908/Case_Study_1-Bellabeat_Smart_Device_Usage/assets/146215343/ec0aa626-427d-4dea-8bc8-67b6104dfd64)


From the chart, I was able to determine that the total steps for all users peaks at around 12:00 - 2:00pm, and then does so again from at roughly 4:00-7:00pm. This makes sense for the 12:00 - 2:00pm time period since people are more mobile at this time for a number reasons, such as to grab lunch from a nearby restaurant or to do some exercise if they are working remotely from home. The same goes for the 4:00 - 7:00pm time period. Users are likely in commute from work back to home during this time period. The really active users may also use this time period to get a work out done in the late afternoon before dinner and bed time.    

## 5c. Determining the Correlation of Calories with Other Variables

Next, I wanted to know if there was a strong correlation between the number of calories burned and two other variables from the daily_activity data set: "very active minutes" and "total distance". The code and plots for each are below.

    # Determining correlation of Calories to Very Active Minutes
    ggplot(data=daily_activity, aes(VeryActiveMinutes, Calories)) + geom_point(fill="blue") + stat_cor(method = "pearson", x.label = 500, y.label = 175) + labs(x=”Very Active Minutes",y="Calories") + 
    ggtitle("Correlation of Calories to Very Active Minutes") + geom_smooth()


![Scatterplot - Correlation of Calories to Very Active Minutes](https://github.com/nightowl8908/Case_Study_1-Bellabeat_Smart_Device_Usage/assets/146215343/f7fff51a-73ee-4e4f-a7ad-ddce8bb4dd68)




    # Determining correlation of Calories to TotalDistance
    ggplot(data=daily_activity, aes(TotalDistance, Calories)) + geom_point(fill="blue") + stat_cor(method = "pearson", x.label = 500, y.label = 175) + labs(x="Total Distance",y="Calories") + 
    ggtitle("Correlation of Calories to Total Distance") + geom_smooth()


![Scatterplot - Correlation of Calories to Total Distance](https://github.com/nightowl8908/Case_Study_1-Bellabeat_Smart_Device_Usage/assets/146215343/99b0abbd-3fdc-47b8-aaba-9bb32d2de7e9)



# 6. Share Phase: Summary of Conclusions

From my analysis for this data, I was able to come to the following conclusions:

- The majority of users for this data are not very active since most minutes were counted as "sedentary".
- The average amount of sleep in hours for users was less than 7 hours, which is less than the amount recommended.
- The times at which users tend to be most active are 12:00-2:00pm and 4:00 - 7:00pm.
- There is a positive, moderate relationship between calories burned with both very active minutes and total distance. 


# 7. Act Phase

Based on my conclusions, I would give the following recommendations to Bellabeat and its stakeholders:

- Installing Bellabeat smart devices with a reminder app that is able to remind users about the time they need to go to bed in order to get an adequate amount of sleep would be beneficial.
- Stakeholders should make its smart devices to allows users to track their total distance, the level of intensity at which they are exercising, and the amount of calories that they burn. Allowing users 
  to see a combination of the effort they are putting in and their reults would be a great motivator for users to continue doing exercise in order to meet their health goals. 
- Having smart devices come with a function that gives users free, daily tips about health and fitness would be a nice feature and would do well in marketing strategies for the product. These daily health         tips would do especially well for commuters who live and work in major urban areas. If you look on any bus or train in a city like Chicago, you will find most people looking at their smart phone or a            similar electronic device. Thus, smart device users for Bellabeat could use the times of commute in the morning and afternoon (before and after work) to read these bits of advice about health and fitness 
  and get great value out of them.  










    
