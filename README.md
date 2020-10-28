# Historical Time in Bed

Sleep plays a vital role in brain function and systemic physiology across many body systems. Problems with sleep are widely prevalent and include deficits in quantity and quality of sleep.

Sleep is a biologic process that is essential for life and optimal health. Sleep plays a
critical role in brain function and systemic physiology, including metabolism, appetite
regulation, and the functioning of immune, hormonal, and cardiovascular systems.
Normal healthy sleep is characterized by sufficient duration, good quality, appropriate
timing and regularity, and the absence of sleep disturbances and disorders.

sleep problems that impact the continuity of sleep are collectively referred to as sleep disruptions. Numerous factors contribute to sleep disruption, ranging from lifestyle and environmental factors to sleep disorders and other medical conditions.

## Shifting Sleep Patterns

Sleep patterns can be affected by many factors, including age, the amount of recent sleep or wakefulness, the time of the day or night relative to an individual’s internal clock, other behaviors prior to sleep such as exercise, stress, environmental conditions such as temperature and light, and various chemicals.

Sleep history—the quantity and quality of an individual’s sleep in recent days—can also have dramatic effects on sleep patterns. Repeatedly missing a night’s sleep, an irregular sleep schedule, or frequent disturbance of sleep can result in a redistribution of sleep stages. Drugs may affect sleep stages as well. For example, alcohol before sleep tends to suppress REM sleep early in the night. As the alcohol is metabolized later in the night, REM sleep rebounds. However, awakenings also become more frequent during this time.

## Daytime Naping 
Although it is common for people in many western societies to sleep in a single consolidated block of about eight hours during the night, this is by no means the only sleep pattern. In fact, following this schedule and foregoing an afternoon nap would seem highly abnormal to many people around the world.

Afternoon naps for most people typically last between 30 and 60 minutes. Any longer and there is a risk of falling into deep sleep and having a difficult time waking. Following a nap, having dissipated some of the accumulated sleep drive, many people report feeling better able to stay awake and alert in the late afternoon and evening. This increased alertness typically causes people to go to bed later and generally to sleep less at night than people who do not take naps.

According to sleep experts, napping can be a good way for people who do not sleep well at night to catch up. They do caution, however, that people with insomnia may make their nighttime sleep problem worse by sleeping during the day. Otherwise, they generally recommend naps for people who feel they benefit from them.



The goal is to calculate exponentially weighted moving average of the time in bed for each user using time spans of 3, 7, and 28 days.

The 3 day span it's to see the behavior in the really short term, the 7 day span it's for the behavior for that week. And the 28 day is for the long term behavior. 




### Exponentially Weighted Moving Average

An exponentially weighted moving average is a way to continuously compute a type of
average for a series of numbers, as the numbers arrive. After a value in the series is
added to the average, its weight in the average decreases exponentially over time. This
biases the average towards more recent data. EWMAs are useful for several reasons, chiefly
their inexpensive computational and memory cost, as well as the fact that they represent
the recent central tendency of the series of values.

The EWMA algorithm requires a decay factor, alpha. The larger the alpha, the more the average
is biased towards recent history. The alpha must be between 0 and 1, and is typically
a fairly small number, such as 0.04. We will discuss the choice of alpha later.

The algorithm works thus, in pseudocode:

1. Multiply the next number in the series by alpha.
2. Multiply the current value of the average by 1 minus alpha.
3. Add the result of steps 1 and 2, and store it as the new current value of the average.
4. Repeat for each number in the series.

There are special-case behaviors for how to initialize the current value, and these vary
between implementations. One approach is to start with the first value in the series;
another is to average the first 10 or so values in the series using an arithmetic average,
and then begin the incremental updating of the average. Each method has pros and cons.

It may help to look at it pictorially. Suppose the series has five numbers, and we choose
alpha to be 0.50 for simplicity. Here's the series, with numbers in the neighborhood of 300.

![Data Series](https://github.com/DiogoRibeiro7/test/blob/main/28242350-463289a2-6977-11e7-88ca-fd778ccef1f0.png)

Now let's take the moving average of those numbers. First we set the average to the value
of the first number.

![EWMA Step 1](https://github.com/DiogoRibeiro7/test/blob/main/28242353-464c96bc-6977-11e7-9981-dc4e0789c7ba.png)

Next we multiply the next number by alpha, multiply the current value by 1-alpha, and add
them to generate a new value.

![EWMA Step 2](https://github.com/DiogoRibeiro7/test/blob/main/28242351-464abefa-6977-11e7-95d0-43900f29bef2.png)

This continues until we are done.

![EWMA Step N](https://github.com/DiogoRibeiro7/test/blob/main/28242352-464c58f0-6977-11e7-8cd0-e01e4efaac7f.png)

Notice how each of the values in the series decays by half each time a new value
is added, and the top of the bars in the lower portion of the image represents the
size of the moving average. It is a smoothed, or low-pass, average of the original
series.

For further reading, see [Exponentially weighted moving average](http://en.wikipedia.org/wiki/Moving_average#Exponential_moving_average) on wikipedia.

### Choosing Alpha

Consider a fixed-size sliding-window moving average (not an exponentially weighted moving average)
that averages over the previous N samples. What is the average age of each sample? It is N/2.

Now suppose that you wish to construct a EWMA whose samples have the same average age. The formula
to compute the alpha required for this is: alpha = 2/(N+1). 



