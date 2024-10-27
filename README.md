# Google-Data-Analytics-Capstone-Project
Case Study in Final Course of the Google Data Analytics Professional Certificate Program.


## Introduction  
_____________________________________________________________________________________________________________________________________________________________________________________________
This case study will be for the fictional bike sharing company Cyclistic. I will be acting as a Junior Data Analyst with marketing team. The steps for this data analysis will follow the process of: Ask, Prepare, Process, Analyze, Share, and Act.  

Tools Used: Excel, Microsoft SQL Sever, Power Bi Desktop


## About Company and Goals
_____________________________________________________________________________________________________________________________________________________________________________________________
Cyclist is a bike-share company based out of Chicago. They have 5,824 bicycles with 692 stations throughout Chicago. The bikes are geotracked and can be dropped off or picked up from any station at any time. They believe that the future of their company will have better success if they can convert casual riders into annual members.


## Ask  
______________________________________________________________________________________________________________________________________________________________________________________________
To answer the question of how to convert casual riders into annual riders the team needs to better understand how annual members and casual riders differ. I have been assigned to answer the question: How do annual members and casual riders use Cyclist bikes differently?

Questions to ask: 
  * Types and counts of users
  * What days of the week are users most likely to ride? Ride the least?
  * What months are the busiest for different types of users? Least busiest?
  * Median ride length of users
  

## Prepare  
_____________________________________________________________________________________________________________________________________________________________________________________________
The .csv data files can be found [here](https://divvy-tripdata.s3.amazonaws.com/index.html).  The data is organized into the four quarters of the 2019 year in .csv files. Some of the files are too large to open in excel so I decided to upload each of them seperatley into Microsoft SQL Server Management Studio.

The data has been made availableby Motivate International Inc. under this [license](https://divvybikes.com/data-license-agreement)

 ## Process
 ____________________________________________________________________________________________________________________________________________________________________________________________
### Organize and Standarize

Once all the four files are uploaded, I familiarize myself with the data and find inconsistencies with column names and data types so I standardize the data column names and data types within all four tables.

### Combining Data
I then create a new table with the standardized column names and data types and then combine all four of the tables into my new table. 
 [Combining Data](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/Data%20Combining%20SQL)
 
### Adding Two New Columns
I then added two new columns, day_of_week and ride_length, based off the start_time and tripduration columns. 
 [Add New Columns](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/New%20Columns)
 
### Duplicates
The first steps I took to clean the data was to see if there are any duplicates. Since the trip_id is the primary key I set my query up to make sure each record is unique. There were no duplicates in the trip_id column. 
[Duplicates and Null Values](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/Duplicates%20and%20Null%20Values)

### NULL Values
I then checked for NULL values. In all the columns. 
[Duplicate and Null Values](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/Duplicates%20and%20Null%20Values)

Null values only show up in the gender and birthyear. This data is not crucial to answering the question "How do annual members and casual riders use Cyclist bikes differently?" so I left them in. 

![image](https://github.com/user-attachments/assets/39274c0c-8cd9-4a5a-b06d-c2f9b3ba67fd)


## Analyze 
_____________________________________________________________________________________________________________________________________________________________________________________________
Now it is time to analyze the data and answer the question "How do annual members and casual riders use Cyclistic bikes differently?". 

1. Types and counts of users: <br />

![image](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/images/PercentofRiders.JPG)  

There are more customers than subscribers with there being 880,637 Customers and 2,937,367 Subscribers. 


 2. The frequency of the different users on each day of the week for the year 2019: <br />

![image](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/images/UserTypeCountByDayOfWeekFor2019.jpg)  

Monday thru Fridays are the busiest times for subscribers, with Tuesdays being the busiest. The weekends are the busiest times for casual (customers) riders, with Saturdays being the busiest. 

3. Total trips per month:<br />

![image](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/images/UserTypeCountByMonth2019.jpg)
![image](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/images/ByMonth.jpg)  

For both groups the most trips were taken in September with the least trips taken in February. 


<b>4. Median Ride Length By Month and User:</b>

![image](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/images/MedianGraph.jpg)  
![image](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/images/medianRideLengthGraph.jpg)

The median ride length were the longest in April and May for customers and June, July, and August for subscribers.  

<b>5. Top 5 pick up locations and drop off locations of customers and subscribers:</b>

![image](https://github.com/sec10/Google-Data-Analytics-Capstone-Project/blob/main/images/.jpg)  








