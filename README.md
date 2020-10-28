# Historical Time in Bed

## Introduction

Sleep plays a vital role in brain function and systemic physiology across many body systems. Problems with sleep are widely prevalent and include deficits in quantity and quality of sleep.

Sleep is a biologic process that is essential for life and optimal health. Sleep plays a
critical role in brain function and systemic physiology, including metabolism, appetite
regulation, and the functioning of immune, hormonal, and cardiovascular systems.
Normal healthy sleep is characterized by sufficient duration, good quality, appropriate
timing and regularity, and the absence of sleep disturbances and disorders.

sleep problems that impact the continuity of sleep are collectively referred to as sleep disruptions. Numerous factors contribute to sleep disruption, ranging from lifestyle and environmental factors to sleep disorders and other medical conditions.

### Shifting Sleep Patterns

Sleep patterns can be affected by many factors, including age, the amount of recent sleep or wakefulness, the time of the day or night relative to an individual’s internal clock, other behaviors prior to sleep such as exercise, stress, environmental conditions such as temperature and light, and various chemicals.

Sleep history—the quantity and quality of an individual’s sleep in recent days—can also have dramatic effects on sleep patterns. Repeatedly missing a night’s sleep, an irregular sleep schedule, or frequent disturbance of sleep can result in a redistribution of sleep stages. 

### Daytime Naping 
Although it is common for people in many western societies to sleep in a single consolidated block of about eight hours during the night, this is by no means the only sleep pattern. In fact, following this schedule and foregoing an afternoon nap would seem highly abnormal to many people around the world.

Afternoon naps for most people typically last between 30 and 60 minutes. Any longer and there is a risk of falling into deep sleep and having a difficult time waking. Following a nap, having dissipated some of the accumulated sleep drive, many people report feeling better able to stay awake and alert in the late afternoon and evening. This increased alertness typically causes people to go to bed later and generally to sleep less at night than people who do not take naps.

According to sleep experts, napping can be a good way for people who do not sleep well at night to catch up. They do caution, however, that people with insomnia may make their nighttime sleep problem worse by sleeping during the day. Otherwise, they generally recommend naps for people who feel they benefit from them.

## The Algorithm 

Exponentially Weighted Moving Average (EWMA) and Simple Moving Average (SMA) are similar in that they each measure trends. The two averages are also similar because they are interpreted in the same manner and are both commonly used by analysts to smooth out value fluctuations.
There are some differences between the two measurements, however. The primary difference between an EWMA and an SMA is the sensitivity each one shows to changes in the data used in its calculation.
SMA calculates the average of the data values, while EMA gives more weight to current data values. The newest data value will impact the moving average more, with older data values having a lesser impact.
More specifically, the EWMA gives a higher weighting to recent values, while the simple moving average assigns equal weighting to all values.

So, we choosen EWMA cause we want to analyze the most recent behavior, and EWMA as gives more weight to recent values, it's the best choice.

### Objective 

The goal is to calculate exponentially weighted moving average of the time in bed for each user using time spans of 3, 7, and 28 days.

The 3 day span it's to see the behavior in the really short term, the 7 day span it's for the behavior for that week. And the 28 day is for the long term behavior. 

### Cleaning Data

We choose to clean zero values from our analysis because it can inflate the expected value for time in bed, as the EWMA its a model that reflects the expected time in bed, and zero values will shift that value greatly. 

The zero values were substitude by the median as is the best value that reflects the user behaviour. 

### Goal

The aim is to detect changes in bedtime behavior patterns, such as more or less time, and whether that change is statistically significant. 




