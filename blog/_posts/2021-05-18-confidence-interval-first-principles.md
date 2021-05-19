---
layout: post
type: post
title: "Confidence Intervals from first principles!"
date: 2021-05-18
category: blog
comments: true
author: "Priyanka Kukreja"
tags: [Machine Learning, statistics, ML @ scale]
---
You would often hear Confidence Interval thrown around casually when your
product metrics are too noisy or varying so much day over day that it looks
nothing short of spooky wizardry. Well, stabilizing and understanding those
metrics are a job for another day. For now, let's delve deeper into what
Confidence Interval (CI) really means and how you can apply it for your
sprawling large scale Machine Learning application.

Imagine yourself standing right next to The love of your life (TLOYL) in the
middle of a lush green apple orchard where the fruity smell hangs in the air.
TLOYL turns to you and asks the most romantic question, "My love, what is the
mean weight of an apple in this orchard?"

At a loss of words, you could either weigh every single apple, and add them up
and divide by number of apples to get the mean weight of the apple for TYOYL.
Or, you could simply pick a "small" sample from these apples, weigh them and
give TLOYL an "estimate". This first mean is what we call the population
parameter, since it is the attribute of the entire population of apples. The
second is what we call an "estimate" of a sample.

TLOYL questions, "are you sure?". So you go and get another batch of apples,
weigh them and duly report back. Alas, the mean weight is different this time.
What do we do? This difference in estimates obtained by using different samples
is termed as "sampling error". It is the tendency of every sample to behave
differently from each other. Note that, if all apples were the same, this
sampling error would be less.

In order to see how different samples behave, you pick many different apple
samples and obtain the mean weight for all of them. If you have picked more
than 30 samples, you will notice that the mean weight for all these samples
lines up neatly along a bell curve for normal distribution. Is that a
coincidence? No! The Central Limit Theorem (discussed in another article)
provides us this guarantee.

TLOYL is still looking at you with loving eyes, waiting for the answer to the
fundamental question she asked. Though you are now armed with the distribution
of the means, you still cannot say with 100% conviction what the mean is.
However, given that the bulk of the normal distribution values lie around
its mean (note that, this mean is different from the population mean we intend
to find), you can find out the range within which the mean is "likely" to
occur.

So, to get the range in which the population mean can lie, we first ask: how
sure we want to be that the mean lies in the given range? Say, we want to be
95% sure. This is termed as the "Level of confidence". So, we compute the area
of the normal distribution curve that would cover 95% of values, and exclude
the remaining 2.5% values on either end of the tail. Given that the normal
distribution is symmetric about its mean, we can simply add and subtract this
area to get a range.
### CI for Pop mean = sample mean +- z at 0.025
Are we done? Not so soon! This z value only provides us with the area for a
normal distribution with a variance of 1. However, that is not guaranteed for
the apples population in the orchard we have chosen. So, we will need to
scale the z-value at 0.025 by the standard deviation for the sample.
Hence, the CI becomes:
### CI for Pop mean = sample mean +- s.d * z at 0.025

Are we done now? Not yet, unfortunately. We still need to scale down by the
sqrt. <TODO: Add explanation for why>

---

Summary
1. Confidence Interval is the range of values within which we are x% sure the
population parameter lies. x% provides how sure we are that the population
parameter lies in the given range. For every 100 samples we collect from data, 95 of them will have their mean in the given range and 5 will not.


2. Sampling error: every sample would lead to different estimate for a
population statistic. Hence the error between each sample is called sampling error.

3. Width of CI

    i. variation within a sample: if most items within a sample have similar
    weights, then the sample would also have similar weights.

    ii. Sample size: if we have less information on which to base the
    interval, the intervals will be wider. In larger samples, the effects by
    some unusual values is evened out by other values in the sample. Larger
    samples will be more similar to each other.

    iii. Hence, the more confident we want to be (90%, 95%, 99%), the larger
    our CI will be. More level of confidence => wider interval for same sample
    size.

4. Calculating mean

    i. Use standard deviation in the sample as a measure of variation in the population. Standard Deviation (SD) = avg distance from the mean

    ii. Estimate for variance = SD / sqrt(n)

    iii. This means, the additional info we can get by increasing sample size
    from 100 to 110 is less than the additonal info we get by increasing
    sample size from 10 to 20, thus tightening the interval.

5. If the size of your sample is small (less than 30), use the t-distribution
instead of z-distribution.




<!-- Cant compute population param directly, so estimate them. But this number will vary from sample to sample. This is what Confidence Interval tells us: if I were to take repeated samples, 95 % of the time the estimate for the population param would lie between A to B
Sample mean can be a point data, however population param is expressed as CI
 -->
