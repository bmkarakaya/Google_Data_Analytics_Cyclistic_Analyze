**How Does a Bike-Share Navigate Speedy Success?**

**![yazı tipi, metin, logo, daire içeren bir resim Açıklama otomatik olarak oluşturuldu](media/e3f6d049daa5a9020787fb19cb14567d.PNG)**

**Prepared by**

**Burak Mustafa Karakaya**

**  
**

Scenario

You are a junior data analyst working in the marketing analyst team at Cyclistic, a bike-share company in Chicago. The director of marketing believes the company’s future success depends on maximizing the number of annual memberships. Therefore, your team wants to understand how casual riders and annual members use Cyclistic bikes differently. From these insights, your team will design a new marketing strategy to convert casual riders into annual members. But first, Cyclistic executives must approve your recommendations, so they must be backed up with compelling data insights and professional data visualizations.

About the company

Until now, Cyclistic’s marketing strategy relied on building general awareness and appealing to broad consumer segments. One approach that helped make these things possible was the flexibility of its pricing plans: single-ride passes, full-day passes, and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers who purchase annual memberships are Cyclistic members.

Cyclistic’s finance analysts have concluded that annual members are much more profitable than casual riders. Although the pricing flexibility helps Cyclistic attract more customers, Moreno believes that maximizing the number of annual members will be key to future growth. Rather than creating a marketing campaign that targets all-new customers, Moreno believes there is a very good chance to convert casual riders into members. She notes that casual riders are already aware of the Cyclistic program and have chosen Cyclistic for their mobility needs.

Moreno has set a clear goal: Design marketing strategies aimed at converting casual riders into annual members. In order to do that, however, the marketing analyst team needs to better understand how annual members and casual riders differ, why casual riders would buy a membership, and how digital media could affect their marketing tactics. Moreno and her team are interested in analyzing the Cyclistic historical bike trip data to identify trends.

Ask

Three questions will guide the future marketing program:

1\. How do annual members and casual riders use Cyclistic bikes differently?

2\. Why would casual riders buy Cyclistic annual memberships?

3\. How can Cyclistic use digital media to influence casual riders to become members?

Prepare

I will use Cyclistic’s historical trip data to analyze and identify trends from January 2023 to March 2022(First Quarter) which can be downloaded from [divvy_tripdata](https://divvy-tripdata.s3.amazonaws.com/index.html). The data has been made available by Motivate International Inc. under this license.

This is public data that can be used to explore how different customer types are using Cyclistic bikes. But note that data-privacy issues prohibit from using riders’ personally identifiable information. This means that we won’t be able to connect pass purchases to credit card numbers to determine if casual riders live in the Cyclistic service area or if they have purchased multiple single passes.

Three files follow the naming convention YYYYMM-divvy-tripdata, each containing data for one month. The information in these files includes details such as ride ID, bike type, start time, end time, start station, end station, start location, end location, and membership status. The corresponding column names are ride_id, rideable_type, started_at, ended_at, start_station_name, start_station_id, end_station_name, end_station_id, start_lat, start_lng, end_lat, end_lng, and member_casual.

Upon examination, all three files exhibit consistency in terms of the number and names of columns. The data types are uniform across all files. The source of the data is Cyclist's first-party data, ensuring a low likelihood of bias. The credibility of the data is exceptionally high since it originates from the company itself.

The data also adheres to the ROCCC criteria: it is Reliable, Original, Comprehensive, Current, and Cited. This further reinforces the trustworthiness of the dataset.

Process

I will use Python to merge, clean, and analyze three different datasets. Python, with its various libraries (e.g., pandas, numpy, datetime, statistics), makes working with data more convenient.

![](media/db6e16c564e0abc58163d46762680d24.png)First, we download the necessary libraries.

![](media/8175a537d375744bf5c986ac74825428.png)Then, we read the downloaded CSV files.

By writing a function, we merge these three different datasets into a single dataset named df0.

![](media/757a73adb01db79148fed00e823bc3f7.png)

When examining the first 5 rows of our dataset, we can see the columns and the data within them. However, this is not sufficient for understanding our dataset.

![](media/2c9483f275fb8cf63bdb442e05d3d4d8.png)

![](media/7254fba87b600902229c184398bed60f.png)

The describe() function provides total counts, unique value counts, and most frequently occurring values for all features. Let's conduct a brief review of the 'rideable_type' column.

![](media/9d51edce9881f9d87cc4662ae9d1a252.png)

![](media/eb3e242e8d50d8dfeb3ec312fadd49c9.png)In the following code block, we see the total number of missing values in our columns. It is evident that there are many missing values in the start_station_name, start_station_id, end_station_name, and end_station_id columns.

![](media/7c5e22381b7645c2b849095766f0272a.png)

![](media/b19ca2b00320d54260c351d761a6e368.png)

![](media/878efb1da96d8e2ddb610e2c7a82fff9.png)

After learning about our data types, we proceed to acquaint ourselves with our dataset. We do not want the started_at and ended_at columns to be objects because they represent date values.

![](media/fb76fc9a18030602540516c7b3858505.png)![](media/b506ab0e3402ae45394f26f7eafc9e9d.png)Now, we can clean and organize our data. First, we convert the started_at and ended_at columns from object to datetime.

![](media/7f7c1ede49b307b8054066f0c5fffcb1.png)

We add a column called ride_length, which calculates the difference between the end and start dates. This allows us to see the duration of rides.

![](media/d2f13090460cf5f8e9e2bbd663441812.png)

By adding the day_of_week column, we create a new column for the days of the week in the starting dates. The +1 in the apply() function ensures that the days are from 1 to 7 instead of 0 to 6.

![](media/c6d461eab7e2099ffa639c6f43a4ac4e.png)

![](media/fbeaea0e9ccff416dbb0504f4c806d69.png)When looking at the statistical values of the newly added columns, I see that the average value of the ride_length column is 13 minutes. However, I notice anomalies, such as a ride duration of 23 days and 8 hours, which is not realistic. There is also an anomaly in the minimum value, as the started_at date cannot be after the ended_at date. Finally, I observe that the 3rd day of the week has the highest number of rides.![](media/d2134166a3a5d6835b7ed82312e3e5c6.png)

![](media/d850d180461f2271da42796fdc3a5f0a.png)![](media/39e25041034498e1a0182d391d2bfd91.png)![](media/efc9aba7ff13a4f63db8038c4267d407.png)![](media/0a662ea643a79d2f1cfbf97abd185f48.png)To verify these anomalies, I first retrieve the minimum and maximum ride_length values. It is evident that there are incorrect date entries. Unfortunately, these anomalies will have a negative impact on our analysis. Therefore, we need to find all row values with this anomaly.

![](media/ae1716c24c6adee8d4be1ff52a8c8945.png)I want to know the count of other rows with anomaly_period_negative and anomaly_period_positive columns. ![metin, ekran görüntüsü, iş kartı, yazı tipi içeren bir resim Açıklama otomatik olarak oluşturuldu](media/02cdcb6f552def37a9b26596caae2773.png)

![](media/7cfa2d51d5721c643d2048665e76912c.png)![](media/97f393cacf19c459e61f3a9f90389f55.png)While there is a negative 1 value, there are 387 rides lasting more than 1 day.

Since removing these anomaly values will result in a more meaningful analysis, I delete them from the dataset.

![](media/4c318cf1d1b1e55c8a688d588e6dcd36.png)

![](media/793dce512b0bce7d35ac01eeb88570a4.png)![](media/f415c0281acf968a31dbeeb6795a76ba.png)I also decide to check if there are rides with 0 duration for control purposes and find 35 rides with 0 duration. I remove them from our dataset as well.

![](media/3528af7d32343ed6f6ed14364603db41.png)

![](media/422c30b80da65f65c5ec4c89262fd985.png)

![](media/aa30ba48a63170951901f734e0a7480e.png)![](media/19292e594d3f547bf39cd32d97373fa3.png)Now, our dataset is cleaned, and a total of 423 entries have been removed. When checking the data types, I see that all of them are correct. Additionally, there are now unnecessary columns that we will remove later; but before that, I want the ride_length value to be an integer instead of timedelta64.

![](media/b6ac0d1cc6cf8302ee0eab340abfe0bc.png)

First, I convert from timedelta to str, then from str to int, and during this process, I assign it to a new column named ride_duration_int.

![](media/b848105897d683b26d29d794d1f88c8b.png)

![](media/8b864408e7347d6fd1d97f6d608d77d3.png)

Next, it's time to remove the unnecessary columns from our dataset. I have removed all unnecessary columns.

![](media/00517820379b124db120eee751989103.png)

![metin, ekran görüntüsü, yazı tipi, dikdörtgen içeren bir resim Açıklama otomatik olarak oluşturuldu](media/261029fd54004909e52aec86af67b030.png)![](media/6e4a5001f8e75500fcd28993064958ed.png)

![](media/f76d4afe6b3b9d14b6357ce3e4bb4e5f.png)

Data Cleaning:

-   Data types have been adjusted ('started_at', 'ended_at').
-   Necessary columns have been added ('ride_length', 'day_of_week', 'ride_duration_int').
-   Data anomalies have been detected and removed. A total of 423 entries were deleted.

Analyze and Sharing:

![](media/78eb0b9b0f3b5a5566fd5ce7109fe61a.png)

When we look at the total number of user types, we have 494,087 members and 144,914 casual users. In terms of proportional distribution, 77.32% of users are members, while 22.68% are in the casual status.

![](media/6c6b9c025e0539f79b640d95b1c40854.png)

In terms of rideable bike types, our users prefer electric bikes the most (54.02%), while docked bikes are the least preferred (1.07%).

![](media/cecf2887878f11bad3ff463f5c59be2d.png)

We observe the density maps of starting and ending locations for member and casual user rides. While starting points are close for both user types, when looking at the ending points, we see that member users tend to finish their rides more towards the east compared to casual users.

![](media/97a08117bc0ed46c96831f4188b5cc54.png)When looking at the total ride duration by month, we see that March is the month with the most ride duration. The main reason for this is that March has milder weather conditions compared to January and February.

![metin, ekran görüntüsü, yazı tipi içeren bir resim Açıklama otomatik olarak oluşturuldu](media/afa768e9ca484a1f160f6fa676c02915.PNG)![metin, ekran görüntüsü, yazı tipi, yazılım içeren bir resim Açıklama otomatik olarak oluşturuldu](media/4a5d20ef0ec93b615c977a625cc9c831.PNG)When we look at the most preferred starting and ending stations for our member users, we see locations such as universities, workplaces, and residential areas. It can be roughly stated that member users aim for commuting to and from work or school.

![metin, ekran görüntüsü, yazılım, yazı tipi içeren bir resim Açıklama otomatik olarak oluşturuldu](media/2c1f5f74d119b86b8a64fb843baa058b.PNG)When we examine the most preferred starting and ending stations for our casual users, we observe parks, aquariums, and tourist attractions. It can be roughly said that casual users engage in cycling more for leisure purposes.![metin, yazı tipi, ekran görüntüsü içeren bir resim Açıklama otomatik olarak oluşturuldu](media/066b0adfc7ef43154a78a6c4abaefa0e.PNG)

On a daily basis, we see that on Sundays in February, both types of members ride more compared to other months. Wednesdays and Thursdays in March also show an almost 2 to 3 times increase in rides for both user types compared to other months. Additionally, the better weather conditions of March contribute positively to ride numbers on the remaining days.

![Total rides by days/months and percentage of rides](media/3118cacfee86165658e807d252ca6033.png)

When it comes to the distribution of average ride durations by day and month, we see that Sunday is the day with the longest ride duration. The days with the most rides, Wednesday, and Thursday, have average durations shorter than weekends. Especially for casual users, this difference is more pronounced. This suggests that casual users enjoy longer bike rides on weekends, possibly for recreational purposes such as city tours or sightseeing. On the other hand, member users show a more consistent distribution, indicating they use bikes for commuting purposes, such as going to work or school, regardless of the day of the week.

![Average ride duration by days/months and percentage](media/f150a809e9cb854e997205212b882c32.png)

To better understand, we examine the ride counts by hour/day. On Monday, member users prefer the hours between 8-17. This suggests the usage for school and work purposes. It could also be used for lunch breaks around 12:00, as evidenced by the number of rides, where users ride their bikes to restaurants or cafes during those hours. Casual users, on the other hand, prefer the hours around the end of school or work during the day. However, they don't seem to prefer riding bikes in the morning when going to school or work.

![Ride count by membership hour dist](media/fdf47957663a9314ef03458d1351617e.png)

![Ride count by membership hour dist](media/d0fda68a16398426fadf4227ae2edf75.png)![Ride count by membership hour dist](media/2c68d2f7942e5e853db99cc3a5b66eac.png)![Ride count by membership hour dist](media/9ee4ebef225453f1dae5ff881abf2a4a.png)![Ride count by membership hour dist](media/eb0c33fb729313fa321994c130f75abe.png)This pattern is valid for Tuesday, Wednesday, Thursday, and Friday as well.

![](media/202c125866269f950b300ee3d9125a3b.png)On Saturday, both casual and member users have peak hours at 14:00. This is because Saturday rides are likely for leisure purposes, such as sports, activities with friends or family, city tours, and tourist trips. The same applies to Sunday.

![](media/c9223536c406791090221bd5dd1ebd4a.png)

![](media/d1abb9add387697be4dfa51e93ac88bc.png)When comparing Sunday and Monday, we can understand the difference in the purpose of rides. Looking at the hours, during the weekdays, the rides are for work or school purposes, while during the weekends, they are for leisure. Although people use it more during the weekdays, the ride durations show that rides on weekends are longer.

How do annual members and casual riders use Cyclistic bikes differently?

| **Member**                                                                                                                            | **Casual**                                                                                            |
|---------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|
| Members typically ride bicycles during weekdays, including the start and end times of work or school, as well as during lunch breaks. | Casual users enjoy cycling after work or school on weekdays.                                          |
| They generally maintain a consistent duration of cycling throughout the weekdays.                                                     | On weekends, their riding durations are significantly longer compared to weekdays.                    |
| The popular starting and ending points are located near schools, workplaces, and commercial buildings.                                | The popular starting and ending points are close to parks, museums, aquarium and tourist attractions. |

Action Plan:

-   Evaluate the winter compatibility of our bikes in challenging conditions, such as January and February. Assessing features like wheels and the power of electric bikes, we can encourage the use of winter-specific bikes during the winter months, potentially increasing our user base.
-   Increase annual membership by offering special discounts and introducing winter-specific bikes through marketing campaigns during the winter months.
-   Since casual users prefer riding on weekends, create special campaigns and advantageous memberships for them during weekends.
-   Highlight stations in tourist locations (museums, historical sites, natural attractions, cinemas, popular places) in social media advertisements. People are more likely to choose us when they know we have stations in such locations.
-   Review membership and single-use pricing. Conduct A/B testing with Decoy Effect research and revise pricing strategies.
