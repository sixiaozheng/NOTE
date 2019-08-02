# Part 2: Statistical Extreme Value Theory for Visual Recognition

## The Statistical Extreme Value Theory (EVT)

Why EVT for visual recognition problems?
- Powerful explanatory theory (Scheirer et al. T-PAMI 2011)
- Effective tool for statistical modeling of decision boundaries (Broadwater et al. IEEE T. Signal Processing 2010, Fragoso and Turk CVPR 2013)
    - Calibration models (Scheirer et al. ECCV 2010)

## The Extreme Value Theorem

![1563632759012](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563632759012.png)

$n\to\infty$ **or $x\to\infty$ ?**

## The Weibull Distribution

![1563632924357](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563632924357.png)

## Fitting an EVT Distribution

![1563632953026](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563632953026.png)

## Is there a difference between central tendency modeling and EVT?

- Sample set of 1,000 values from a standard normal distribution
- Compute means over 10,000 trials

![1563633201692](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563633201692.png)

- Sample set of 1,000 values from a standard normal distribution
- Retain the maximums over 10,000 trials

![1563633991430](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563633991430.png)The peak is now at 3.2, and there is noticeable skew

## A good alternative to central tendency modeling

![1563682349854](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563682349854.png)

## Example two-category discrimination task along a parametric stimulus axis

![1563682380891](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563682380891.png)

## Meta-Recognition Theory

Meta-recognition is **recognizing when a recognition system is working or failing**. It is important for threshold selection, failure prediction and improving fusion.

![1563684105930](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563684105930.png)

## Failure Prediction

Can we recognize, in some automated fashion, if a recognition system result is a success or a failure?
If so, can we quantify the probability of success or failure?

## Meta-Recognition as failure prediction

![1563684163436](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563684163436.png)

## Predicting Failures of Vision Systems

Zhang et al. CVPR 2014
Learn conditions that cause a target algorithm to fail

![1563684221061](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563684221061.png)

## Statistical EVT Failure Prediction 

- Get scores, sort and take top N
- Fit an extreme value distribution to get model of non-match distribution, exclude top score
- Determine if top score is outlier from distribution, If so predict success. Else predict failure
- Detect outlier using fraction CDF below the potential outlier. 99.99999% is a good test! 

## Statistical EVT Failure Prediction

![1563684317753](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563684317753.png)

## What else can Meta-Recognition do?

-   Decision fusion (fuse only those that are not predicted to fail) or weighted score fusion.

-   For statistical EVT prediction use: w-score fusion where:
    	w-score(x) = CDFWeibull(x)

-   Use w-score to weight data for fusion, i.e., compute average w-score over different algorithms/modalities.

## w-score normalization

![1563684513128](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563684513128.png)

## Fusion Performance

![1563684667499](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563684667499.png)

w-score fusion outperformed z-score with sum (or product) fusion on all experiments. In general, the lower the performance the greater the differential gain.

## Support Vectors

![1563685491268](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563685491268.png)

## Calibration for decision boundaries

![1563686017117](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563686017117.png)

## Fusion after normalization

![1563686950613](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563686950613.png)

## Utility of the calibration model

![1563686972691](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563686972691.png)

## Sequential Score Adaptation with Extreme Value Theory

![1563687366634](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563687366634.png)

## Sampling and feature correspondence