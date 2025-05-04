## Planning a business trip from New York City to San Francisco.
- Suppose there is a meeting scheduled at a specific time. How early should you plan to arrive to avoid being late due to flight delays?
- Assume the 336,776 flights in the nycflights13 package represent the population

### Find the longest flight delay and adjust the travel schedule to accommodate it.

### Of the 25 flights to SFO:
- Most were not late, and were ahead of schedule.
- But a few were very late, up to 72 minutes.
- The time spread was quite large (standard deviation 29 minutes).

### Calculating the 98th Quantile of a Sample of 25 Rows (sf_25)
This means that 98% of the arrival delays in this sample sf_25 were less than 67.20 minutes.

### Arrival Delay Distribution (True/False for arr_delay < 90)
Groups data based on whether the arrival delay (arr_delay) is less than 90 minutes or not (True/False).

### If you planned to arrive 90 minutes early, how effective would that plan be in achieving the goal of being late to the meeting no more than 2% of the time?
- 95.1% of flights were delayed less than 90 minutes.
- 4.86% of flights were delayed more than 90 minutes.

### Calculating the 98th Quantile of All Data (SF)
That means 98% of flights to SFO are delayed less than 153 minutes.

### Taking a Random Sample of 25 Rows for 500 Trials
The result is a DataFrame sf_25_means that stores the average arrival delays of 500 trials of 25 random rows each.
- The mean_arr_delay column shows the average arrival delay for each random trial.
- The n column shows that each trial involves 25 rows.

From 500 trials with 25 random rows per trial, the average arrival delays show a fairly varied distribution, with most average delays being around 3 minutes.

The average delays tend to be positive, although there is quite a large variation, as the standard deviation reaches 9.85.

### Calculating Confidence Intervals for Mean Delays
This means we can say with 95% confidence that the average delay across the population of flights to SFO is in the range of -16.64 minutes to 22.76 minutes. Since this range includes negative numbers, it shows that the data has a fairly varied distribution, including early flights.

### Calculating the Average for a Sample of 100 Rows
We take 500 random samples of 100 rows each from the SF data and calculate the average arr_delay for each sample.

### Combining Average Results from 25 and 100 Row Samples for Visualization
This histogram will show how the distribution of mean delays changes as the sample size increases from 25 to 100.

### Displaying 3 random flights, with departure time information for each selected flight.

### Bootstrap vs. Sampling Acak Biasa (n = 200)
- Taken from bootstrap samples 500 times (with a return of 1 sample size 200).
- More suitable for measuring the uncertainty of estimates from 1 sample.

### Bootstrap q98 (500 times)
- Taking the 98th quantile 500 times from resampling 1 bootstrap sample.
- The distribution is wide, because arr_delay tends to have a long right tail (right-skewed).
- This makes q98 unstable and very sensitive to outliers.

### Ordinary Random Sampling – Mean arr_delay
Taken from 500 independent random samples from the population, each of size 200.

The mean is lower, indicating the original bootstrap sample likely had a higher lag than the population mean.

### Percentile ke-98 (q98) – arr_delay
Just 1 number, namely the 98th quantile of 1 bootstrap sample of size 200.

### Bootstrap q98 (500 times)
- Taking the 98th quantile 500 times from resampling 1 bootstrap sample.
- The distribution is wide, because arr_delay tends to have a long right tail (right-skewed).
- This makes q98 unstable and very sensitive to outliers.

### Estimate the distribution of the 98th quantile (q98) of arr_delay using bootstrap sampling based on a large initial sample size (n = 10,000), then repeat this process 500 times → resulting in 500 q98 values.
- Mean of 98th percentile (q98) from bootstrap results: 159.31 minutes
- Standard deviation of q98 estimates: 4.67
- The range of q98 distribution ranges from 140.02 (minimum) to 171.00 (maximum)
- Provides uncertainty estimates of q98 based on bootstrap

98% of the arr_delay data has a value less than or equal to 153.

Only 2% of the data has an arr_delay value greater than 153.

### Interpretation 1:
- This shows 7 flights with extreme delays of over 7 hours (420 minutes)
- Most flights are not late or only slightly late.
- There is a long tail to the right (right-skewed), indicating a small percentage of flights are extremely late (>100 minutes, even up to >400 minutes).
- The months with the highest number of long delays were June (X6) and July (X7)— this could be due to the holiday season, weather, or airport congestion.
- UA (United Airlines) appears to have the most flights overall and also has the highest number of long delays (492).
However that could also be because they have a much larger flight volume than other airlines.
- Peak flight hours are 7:00 and 10:00, with the most flights.
- Delays tend to increase over time, likely due to the cumulative effect of previous flights (e.g. a plane arriving late and affecting the next flight).
- Morning schedules (dawn to 8 am) are relatively safe to avoid delays.
- The later the departure schedule, the higher the potential for delay.
- Morning schedules (5–8 a.m.) tend to have lower and more stable delay distributions.
- Outliers (black dots above) appear more in the afternoon–evening schedule.

### Linear regression analysis is used to see the factors that influence aircraft arrival delays (arr_delay)
- If the plane departs exactly at 00:00, the model estimates that the plane will arrive 22.93 minutes earlier.
- Every 1 hour later departure → delay increases by 2.01 minutes.
- Std. Error: The smaller it is, the more precise the estimate is.
- Statistic (t-statistic): A measure of how far the coefficient is from zero statistically. A t-statistic of 22.01 is very high → meaning the hour effect is very strong.
- P-Value: The likelihood that the relationship between variables occurs simply by chance. A very small p-value (e.g. 1.78e-105) → means it is highly statistically significant.

### Details :
- day: only date (without hour) from time_hour
- dow: day name (Monday, Tuesday, ...)
- season: if June/July → summer, otherwise → other month
- hour (departure time)
- origin (origin airport)
- carrier (airline)
- dow (day of the week)

### Interpretation 2:
- Intercept -24.64 Delay at baseline conditions (e.g. Monday, non-summer season, reference airline)
- Hour = 1 hour delay more → add 2.08 minutes delay
- OriginJFK = From JFK → 4.12 minutes slower than baseline origin
- CarrierDL = Delta Airlines is 18.41 minutes faster than reference airline
- Seasonsummer 25.27 Summer season → 25.27 minutes delay longer than other seasons
