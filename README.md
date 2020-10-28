# EWMA


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

![Data Series](https://github.com/DiogoRibeiro7/test/blob/main/28242353-464c96bc-6977-11e7-9981-dc4e0789c7ba.png)

Now let's take the moving average of those numbers. First we set the average to the value
of the first number.

![EWMA Step 1](https://github.com/DiogoRibeiro7/test/blob/main/28242351-464abefa-6977-11e7-95d0-43900f29bef2.png)

Next we multiply the next number by alpha, multiply the current value by 1-alpha, and add
them to generate a new value.

![EWMA Step 2](https://github.com/DiogoRibeiro7/test/blob/main/28242352-464c58f0-6977-11e7-8cd0-e01e4efaac7f.png)

This continues until we are done.

![EWMA Step N](https://user-images.githubusercontent.com/279875/28242352-464c58f0-6977-11e7-8cd0-e01e4efaac7f.png)

Notice how each of the values in the series decays by half each time a new value
is added, and the top of the bars in the lower portion of the image represents the
size of the moving average. It is a smoothed, or low-pass, average of the original
series.

For further reading, see [Exponentially weighted moving average](http://en.wikipedia.org/wiki/Moving_average#Exponential_moving_average) on wikipedia.

### Choosing Alpha

Consider a fixed-size sliding-window moving average (not an exponentially weighted moving average)
that averages over the previous N samples. What is the average age of each sample? It is N/2.

Now suppose that you wish to construct a EWMA whose samples have the same average age. The formula
to compute the alpha required for this is: alpha = 2/(N+1). Proof is in the book
"Production and Operations Analysis" by Steven Nahmias.



