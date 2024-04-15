# Google Capstone Project

## Overview

In this project, I analyzed a dataset for Cyclistic, a bike sharing company in Chicago, using SQL for data analysis and Power BI for visualizations. The dataset provided insights into how annual members and casual riders use Cyclistic bikes differently. By leveraging SQL queries, I extracted, transformed, and analyzed the data to uncover trends and patterns. Additionally, I utilized Power BI for visualizations to present key insights and support decision-making.

## About the Company

Cyclistic launched a successful bike-share program in 2016, featuring over 5,800 bicycles and 600 docking stations across Chicago. The program offers various bike options, including reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive. Cyclistic aims to differentiate itself by promoting bike-share for both leisure and commuting purposes.

## Project Goals

- Analyze Cyclistic's bike trip data to understand how annual members and casual riders utilize the service differently.
- Develop marketing strategies to convert casual riders into annual members based on data insights.
- Utilize Power BI for visualizations to present key findings and support decision-making processes.

## Tools Used

- **Data Analysis**: SQL queries were used to extract and analyze the Cyclistic bike trip data.
- **Visualization**: Power BI was used for visualizations to present key insights.

## SQL Queries

### Query 1: Average Ride Length per User Category

```sql
SELECT
    member_casual,
    AVG(EXTRACT(EPOCH FROM ride_length)/60) AS avg_ride_length
FROM
    (
    SELECT member_casual, ride_length FROM trip_data_202304
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202305
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202306
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202307
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202308
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202309
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202310
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202311
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202312
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202401
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202402
    UNION ALL
    SELECT member_casual, ride_length FROM trip_data_202403
    ) AS all_rides
GROUP BY
    member_casual;
```
![](https://github.com/ZiyadBendaou/TripData_Analysis/blob/main/visualizations/avg_ride_length_by_user.png?raw=true)


### Query 2: Average Ride Length per Weekday

```sql
SELECT
    weekday,
    ROUND(AVG(EXTRACT(EPOCH FROM ride_length)/60),0) AS avg_ride_length
FROM
    (
    SELECT weekday, ride_length FROM trip_data_202304
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202305
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202306
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202307
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202308
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202309
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202310
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202311
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202312
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202401
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202402
    UNION ALL
    SELECT weekday, ride_length FROM trip_data_202403
    ) AS all_rides
GROUP BY
    weekday
ORDER BY
    weekday;
```
![](https://github.com/ZiyadBendaou/TripData_Analysis/blob/main/visualizations/avg_ride_length_by_weekday.png?raw=true)


### Query 3: Total Rides per Weekday

```sql
SELECT
    weekday,
    COUNT(*) AS ride_count
FROM
    (
    SELECT weekday FROM trip_data_202304
    UNION ALL
    SELECT weekday FROM trip_data_202305
    UNION ALL
    SELECT weekday FROM trip_data_202306
    UNION ALL
    SELECT weekday FROM trip_data_202307
    UNION ALL
    SELECT weekday FROM trip_data_202308
    UNION ALL
    SELECT weekday FROM trip_data_202309
    UNION ALL
    SELECT weekday FROM trip_data_202310
    UNION ALL
    SELECT weekday FROM trip_data_202311
    UNION ALL
    SELECT weekday FROM trip_data_202312
    UNION ALL
    SELECT weekday FROM trip_data_202401
    UNION ALL
    SELECT weekday FROM trip_data_202402
    UNION ALL
    SELECT weekday FROM trip_data_202403
    ) AS all_rides
GROUP BY
    weekday
ORDER BY
    ride_count DESC;
```
![](https://github.com/ZiyadBendaou/TripData_Analysis/blob/main/visualizations/ride_by_weekday.png?raw=true)


### Query 4: Rides per Hour of the Day

```sql
SELECT
    EXTRACT(HOUR FROM started_at) AS hour_of_day,
    COUNT(*) AS total_rides
FROM
    (
    SELECT started_at FROM trip_data_202304
    UNION ALL
    SELECT started_at FROM trip_data_202305
    UNION ALL
    SELECT started_at FROM trip_data_202306
    UNION ALL
    SELECT started_at FROM trip_data_202307
    UNION ALL
    SELECT started_at FROM trip_data_202308
    UNION ALL
    SELECT started_at FROM trip_data_202309
    UNION ALL
    SELECT started_at FROM trip_data_202310
    UNION ALL
    SELECT started_at FROM trip_data_202311
    UNION ALL
    SELECT started_at FROM trip_data_202312
    UNION ALL
    SELECT started_at FROM trip_data_202401
    UNION ALL
    SELECT started_at FROM trip_data_202402
    UNION ALL
    SELECT started_at FROM trip_data_202403
    ) AS all_rides
GROUP BY
    hour_of_day
ORDER BY
    total_rides DESC;
```
![](https://github.com/ZiyadBendaou/TripData_Analysis/blob/main/visualizations/rides_by_hour.png?raw=true)


### Query 5: Rides per User Category

```sql
SELECT
    member_casual,
    COUNT(*) AS total_rides
FROM
    (
    SELECT member_casual FROM trip_data_202304
    UNION ALL
    SELECT member_casual FROM trip_data_202305
    UNION ALL
    SELECT member_casual FROM trip_data_202306
    UNION ALL
    SELECT member_casual FROM trip_data_202307
    UNION ALL
    SELECT member_casual FROM trip_data_202308
    UNION ALL
    SELECT member_casual FROM trip_data_202309
    UNION ALL
    SELECT member_casual FROM trip_data_202310
    UNION ALL
    SELECT member_casual FROM trip_data_202311
    UNION ALL
    SELECT member_casual FROM trip_data_202312
    UNION ALL
    SELECT member_casual FROM trip_data_202401
    UNION ALL
    SELECT member_casual FROM trip_data_202402
    UNION ALL
    SELECT member_casual FROM trip_data_202403
    ) AS all_rides
GROUP BY
    member_casual;
```
![](https://github.com/ZiyadBendaou/TripData_Analysis/blob/main/visualizations/number_of_users_by_category.png?raw=true)