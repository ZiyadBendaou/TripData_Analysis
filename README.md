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


## Insights

### Average Ride Length per User Category

- Casual riders have an average ride length of 21 minutes, while members have an average ride length of 12 minutes.

### Ride Length per Weekday

- The average ride length varies slightly throughout the week, with longer rides on weekends (Sunday and Saturday) and shorter rides during weekdays.

### Rides per Day

- The number of rides peaks on weekends, with Sunday having the highest number of rides followed by Friday and Saturday. Weekdays see fewer rides, with Monday having the lowest number of rides.

### Rides per Hour of the Day

- The peak hours for rides are in the late afternoon and early evening, with 5 PM being the busiest hour. There's also significant activity during midday hours, with a drop in the early morning and late night.

### Rides per User Category

- Members account for a larger number of rides compared to casual riders, with over 3.6 million rides recorded for members and around 2.1 million rides for casual riders.


## Recommendations Based on Analysis

### 1. Average Ride Duration Insights:
- **Tailored Membership Packages:** Offer membership packages that cater to different user preferences and ride durations. For casual riders who tend to take longer rides, consider offering flexible membership options with extended ride durations or discounted rates for longer trips. For members who prefer shorter rides, focus on promoting convenience and accessibility through shorter-duration memberships.

### 2. Ride Length Variation by Weekday:
- **Targeted Promotions:** Adjust marketing efforts and promotions based on weekday ride patterns. For example, offer weekday-specific promotions to incentivize ridership during days with lower average ride lengths. Consider implementing targeted discounts or perks for members who ride during peak hours on weekdays to encourage consistent usage throughout the week.

### 3. Rides Per Day Analysis:
- **Weekend Engagement Initiatives:** Recognize the higher ride counts on weekends and leverage this insight to develop weekend-focused engagement initiatives. Organize special events, group rides, or community activities on weekends to attract riders and promote membership conversion. Highlight the benefits of weekend rides, such as leisurely exploration or fitness activities, to encourage casual riders to become members.

### 4. Rides Per Hour Analysis:
- **Peak Hour Marketing:** Capitalize on peak ride hours by launching marketing campaigns or promotions targeting these specific time slots. Offer time-limited incentives or discounts for rides taken during peak hours to drive membership sign-ups and increase overall ridership. Highlight the convenience and availability of bikes during peak hours to attract both casual riders and potential members.

### 5. Rides Per User Category:
- **Conversion Strategies:** Focus on converting casual riders into members by highlighting the advantages of membership, such as unlimited rides and cost savings. Implement targeted marketing strategies aimed at casual riders, emphasizing the value proposition of membership and addressing common barriers to conversion, such as perceived upfront costs or commitment concerns.
