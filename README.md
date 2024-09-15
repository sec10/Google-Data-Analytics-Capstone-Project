# Google-Data-Analytics-Capstone-Project
Case Study in Final Course of the Google Data Analytics Professional Certificate Program.


## Introduction  
_____________________________________________________________________________________________________________________________________________________________________________________________
This case study will be for the fictional bike sharing company Cyclistic. I will be acting as a Junior Data Analyst with marketing team. The steps for this data analysis will follow the process of: Ask, Prepare, Process, Analyze, Share, and Act.


## About Company and Goals
_____________________________________________________________________________________________________________________________________________________________________________________________
Cyclist is a bike-share company based out of Chicago. They have 5,824 bicycles with 692 stations throughout Chicago. The bikes are geotracked and can be dropped off or picked up from any station at any time. They believe that the future of their company will have better success if they can convert casual riders into annual members.


## Ask  
______________________________________________________________________________________________________________________________________________________________________________________________
To answer the question of how to convert casual riders into annual riders the team needs to better understand how annual members and casual riders differ. I have been assigned to answer the question: How do annual members and casual riders use Cyclist biked differently?

Questions to ask: 
  * Frequency of different users on each day of the week.
  * Ride length differences of different users
  * What day of the week is most popular for different users
  * Average age of riders
  * Gender of riders
  * What casual and members use bikes in different seasons
  * Most popular times of day

## Prepare  
_____________________________________________________________________________________________________________________________________________________________________________________________
The .csv data files can be found [here](https://divvy-tripdata.s3.amazonaws.com/index.html). The data has been made availableby Motivate International Inc. under this [license](https://divvybikes.com/data-license-agreement)

### Organize and Standarize
The data is organized into the four quarters of the 2019 year in .csv files. Some of the files are too large to open in excel so I decided to upload them into Microsoft SQL Server Management Studio.  Once all the files are uploaded, I familiarize myself with the data and find inconsistencies with column names and data types so I standardize the data column names and data types within all four tables.


### Combining Data
I then create a new table with the standardized column names and data types and then combine all four of the tables into my new table. 
 [Combining Data](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/Data%20Combining%20SQL)
 
### Adding Two New Columns
I then added two new columns, day_of_week and ride_length, based off the start_time and tripduration columns. 
 [Add New Columns](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/New%20Columns)

 ## Process
 ___________



