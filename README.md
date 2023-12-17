# Google_Data_Analytics_Cyclistic_Analyze
This is the capstone analysis project of the [Google Data Analytics course](https://www.coursera.org/learn/google-data-analytics-capstone).

I have uploaded a more comprehensive version of the project in [PDF format](https://github.com/bmkarakaya/Google_Data_Analytics_Cyclistic_Analyze/blob/main/Cyclistic.pdf). Please download and read it, especially to gain a deeper understanding of the Process and Analyze, Share phases. I opted not to extend the README section to cover every detail extensively.

All visualizations: [Tableau](https://public.tableau.com/views/Google_data_analytics_bicycle_app/Usersstartendlocationsdensitymap?:language=en-US&:display_count=n&:origin=viz_share_link)
All the processes related to the data: [Python](https://github.com/bmkarakaya/Google_Data_Analytics_Cyclistic_Analyze/blob/main/Cyclistic%20-%20Process%2C%20Analyze.ipynb)

## Introduction
In this case study, I will be responding to the company in the assessment phase with various methods to address the three questions they have asked me. Other than the scenario and information about the company, we have six important subheadings: Ask, Prepare, Process, Analyze, Share, and finally, the subheading where I find a solution, Act.



---
### Scenario
You are a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, your team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, your team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve your recommendations, so they must be backed up with compelling data insights and professional data visualizations.

### About the company
Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.

### Ask
Three questions will guide the future marketing program:
1. How do annual members and casual riders use Cyclistic bikes differently?
2. Why would casual riders buy Cyclistic annual memberships?
3. How can Cyclistic use digital media to influence casual riders to become members?

### Prepare
I will use Cyclistic’s historical trip data to analyze and identify trends from January 2023 to March 2022(First Quarter) which can be downloaded from [divvy_tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html). The data has been made available by Motivate International Inc. under this license.

This is public data that can be used to explore how different customer types are using Cyclistic bikes. But note that data-privacy issues prohibit from using riders’ personally identifiable information. This means that we won’t be able to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes.

Three files follow the naming convention YYYYMM-divvy-tripdata, each containing data for one month. The information in these files includes details such as ride ID, bike type, start time, end time, start station, end station, start location, end location, and membership status. The corresponding column names are ride_id, rideable_type, started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, and member_casual.

Upon examination, all three files exhibit consistency in terms of the number and names of columns. The data types are uniform across all files. The source of the data is Cyclist's first-party data, ensuring a low likelihood of bias. The credibility of the data is exceptionally high since it originates from the company itself.

The data also adheres to the ROCCC criteria: it is Reliable, Original, Comprehensive, Current, and Cited. This further reinforces the trustworthiness of the dataset.

### Process
Throughout the Process phase, I completed my tasks using Python. Generally, I performed operations such as merging datasets, deriving statistical insights about the data, changing data types to make them suitable, adding new columns, detecting and removing anomaly data from the dataset, and preparing the dataset for analysis, followed by exporting it.

### **Analyze & Sharing**
In this phase, I utilized Tableau to visualize the dataset that I had cleaned and prepared, further enhancing the understanding of the data, establishing connections, and conducting analysis. Particularly through visualization, my dataset, which I explored from different perspectives, became a more meaningful whole, making it much easier for me to answer the questions posed in the Ask phase. For instance, I was able to provide answers to the following question through the visualizations I created and the connections between them.

>**How do annual members and casual riders use Cyclistic bikes differently?**

|Member|Casual|
|---|---|
|Members typically ride bicycles during weekdays, including the start and end times of work or school, as well as during lunch breaks.|Casual users enjoy cycling after work or school on weekdays.|
|They generally maintain a consistent duration of cycling throughout the weekdays.|On weekends, their riding durations are significantly longer compared to weekdays.|
|The popular starting and ending points are located near schools, workplaces, and commercial buildings.|The popular starting and ending points are close to parks, museums, aquarium and tourist attractions.|

### Act
In this section, I am describing the solutions I found for the questions in the Ask phase.

•	Increase annual membership by offering special discounts and introducing winter-specific bikes through marketing campaigns during the winter months.

•	Since casual users prefer riding on weekends, create special campaigns and advantageous memberships for them during weekends.

•	Highlight stations in tourist locations (museums, historical sites, natural attractions, cinemas, popular places) in social media advertisements. People are more likely to choose us when they know we have stations in such locations.

•	Review membership and single-use pricing. Conduct A/B testing with Decoy Effect research and revise pricing strategies.

•	Evaluate the winter compatibility of our bikes in challenging conditions, such as January and February. Assessing features like wheels and the power of electric bikes, we can encourage the use of winter-specific bikes during the winter months, potentially increasing our user base.

