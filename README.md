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
  * What casual and members use bikes in different seasons
  * Most popular times of day

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


## Analyze and Share 
_____________________________________________________________________________________________________________________________________________________________________________________________
Now it is time to analyze the data and answer the question "How do annual members and casual riders use Cyclistic bikes differently?". 

1. Types of users there are: <br />
SELECT usertype, COUNT(*) AS count<br />
FROM dbo.divvy_trips_2019_Combined<br />
WHERE usertype IN ('customer', 'subscriber')<br />
GROUP BY usertype;<br />



 ![image](https://github.com/user-attachments/assets/b5ab9b3b-9237-44e1-b5c6-3c819a3c5f47)

 2. The frequency of the different users on each day of the week for a year: <br />
 
SELECT <br />
    day_of_week, <br />
    usertype, <br />
    COUNT(*) AS Frequency<br />
FROM <br />
    dbo.Divvy_Trips_2019_Combined<br />
GROUP BY <br />
    day_of_week, <br />
    usertype<br />
ORDER BY <br />
    CASE <br />
        WHEN day_of_week = 'Sunday' THEN 1<br />
        WHEN day_of_week = 'Monday' THEN 2<br />
        WHEN day_of_week = 'Tuesday' THEN 3<br />
        WHEN day_of_week = 'Wednesday' THEN 4<br />
        WHEN day_of_week = 'Thursday' THEN 5<br />
        WHEN day_of_week = 'Friday' THEN 6<br />
        WHEN day_of_week = 'Saturday' THEN 7<br />
    END,<br />
    usertype<br />
    
   Results:<br />

   ![image](https://github.com/user-attachments/assets/26368156-c903-4cbf-86c3-3fae7f0f3a4e)

3. Frequency of different users for each quarter:<br />
   WITH RankedRows AS (<br />
    SELECT <br />
        ride_length, <br />
        usertype,<br />
        ROW_NUMBER() OVER (ORDER BY ride_length) AS row_num,<br />
        COUNT(*) OVER () AS total_rows<br />
    FROM dbo.Divvy_Trips_2019_Q1<br />
    WHERE usertype LIKE 'Customer'<br />
)<br />
SELECT ride_length, usertype<br />
FROM RankedRows<br />
WHERE row_num = (total_rows + 1) / 2;<br />

WITH RankedRows AS (<br />
    SELECT <br />
        ride_length, <br />
        usertype,<br />
        ROW_NUMBER() OVER (ORDER BY ride_length) AS row_num,<br />
        COUNT(*) OVER () AS total_rows<br />
    FROM dbo.Divvy_Trips_2019_Q1<br />
    WHERE usertype LIKE 'Subscriber'<br />
)<br />
SELECT ride_length, usertype<br />
FROM RankedRows<br />
WHERE row_num = (total_rows + 1) / 2;<br />

Quarter 1 - January - March 2019

![image](https://github.com/user-attachments/assets/5f1785a1-0a25-4435-ae92-aa7e18c5e742)


Quarter 2 - April - June 2019

![image](https://github.com/user-attachments/assets/0331e6b6-c12a-4946-b9fa-e8d9f093d023)

Quarter 3 - July - September 2019

![image](https://github.com/user-attachments/assets/cc4024fb-bbf9-4376-805a-74033a850f8b)

Quarter 4 - October - December 2019

![image](https://github.com/user-attachments/assets/e19de5ab-d473-4ba7-ac23-337c1991d0ef)










