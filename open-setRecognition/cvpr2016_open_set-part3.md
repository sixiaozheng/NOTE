## Part 3: Algorithms that Minimize the Risk of the Unknown

## Slab Model

![1563687650865](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563687650865.png)

## Base Linear 1-vs-Set Machine

![1563687788134](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563687788134.png)

## Generalization

![1563687818784](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563687818784.png)

## Specialization

![1563687860126](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563687860126.png)

## Open space risk for linear slab model

![1563690612725](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563690612725.png)

## Open space risk for linear slab model

![1563690654794](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563690654794.png)

## Training and testing data

![1563690793239](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563690793239.png)

## Sketch of the 1-vs-Set Machine training algorithm

![1563691429722](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563691429722.png)

## 1-vs-Set Machine Plane Refinement

![1563691607827](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563691607827.png)

## 1-vs-Set Machine Prediction

![1563692339666](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563692339666.png)

## What could be better about the 1-Vs-Set Machine?

-   Does not inherently support multi-class open set recognition
-   Does not support non-linear kernels
-   Does not contain a CAP model
-   Lack of calibrated probability scores

## $P_I$-SVM: Modeling Probability of Inclusion

- Fit a robust single-class probability model over the positive class scores from a discriminative binary classifier
    - Binary (RBF) classifier helps discriminate the positive class from the known negative classes
    - Single-class probability model adjusts decision boundary to avoid misclassification of “unknowns”

## Consider a kernelized SVM

![1563694252096](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563694252096.png)

## Fit model to tail of positive side of decision boundary

![1563694388253](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563694388253.png)

## Probability model for inclusion

![1563694891650](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563694891650.png)

## Unnormalized Posterior Estimate

If all classes and priors are known, then Bayes’ theorem yields: 

![1563695028165](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563695028165.png)

But this isn’t true for open set recognition, so we let ξ = 1 and treat the posterior estimate as unnormalized

## Multi-class Open Set Recognition with $P_I$-SVM

![1563695177428](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563695177428.png)

## Tail Size Estimation

- EVT tells us how to model extrema, but says nothing about how many samples to model
    - The difference between a tail size of 5% and a tail size of 20% can produce a difference in recognition accuracy of 15-20%

    - Need automatic estimation

## Support Vectors as Extrema

-   Support vectors are a type of extreme sampling that effectively describes the class boundary
    -   Is there a known parametric relationship between training data size, dimensionality, and the number of support vectors? No
    -   Alternative: consider extrema to be the points close to the original decision boundary and count them

## Tail size estimation

![1563696849062](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563696849062.png)

![1563696876725](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563696876725.png)

## Normalized decision scores for $P_I$-SVM

![1563696918908](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563696918908.png)

## Is $P_I$-SVM what we’re looking for for open set recognition?

- Pros:
+Supports multi-class open set recognition
+Better generalization than the 1-vs-Set Machine
- Cons:
-One-sided calibration model (just probability of inclusion)
-Does not make use of a CAP model

## NN+CAP

![1563697921602](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563697921602.png)

- Pros:
+With sufficiently dense sampling, NN+CAP reduces to NN
+Limiting error of no more than twice the Bayes error rate
+Simple to train

- Cons:
-Weak probability model

## The Weibull-calibrated SVM (W-SVM)

- Binary SVMs are better than 1-Class SVMs - how do they fit into the context of CAP models?
- Unfortunately, the decision score isn’t a canonical sum. But calibration is possible (Hoffman et al. Annals of Stat. 2008):
1. Collect all positive coefficients in one sum
2. Collect all negative coefficients into another sum
3. Split the bias between them
4. View SVM as applying a decision rule over which is more similar

## Binary RBF SVM incorporating a CAP model

-   Combine probabilities computed for both 1-class and binary RBF SVMs
-   1-class SVM CAP model is a conditioner

![1563698410974](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563698410974.png)

## Dual tail fitting

![1563698455817](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563698455817.png)

![1563698472672](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563698472672.png)

![1563699147836](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563699147836.png)

## EVT Parameters

![1563699177857](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563699177857.png)

## Two independent estimates for $P(y|f(x))$

![1563699249412](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563699249412.png)

## Combining probability estimates

![1563699350099](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563699350099.png)

## Multi-class W-SVM recognition

![1563699384292](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563699384292.png)

## Training a W-SVM Step-by-Step

![1563699485164](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563699485164.png)

![1563699943076](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563699943076.png)

![1563699969139](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563699969139.png)

![1563699983221](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563699983221.png)

## Specialized Support Vector Machine (SSVM)

![1563700026625](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563700026625.png)

![1563700272428](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563700272428.png)

![1563700342879](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563700342879.png)

## How can we evaluate open set recognition in a controlled manner?

## Accuracy as a statistic for open set problems 

![1563701445871](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563701445871.png)

## F-measure as a statistic for open set problems 

Consistent point of comparison across inconsistent precision and recall numbers:

![1563701515815](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563701515815.png)

## Open Set Object Recognition

![1563701742071](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563701742071.png)

## Features

![1563701808003](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563701808003.png)

## Score Distributions

![1563702052178](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563702052178.png)

## Open World Evaluation

![1563702589506](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563702589506.png)

## Nearest Non-Outlier (NNO) Algorithm

![1563702645521](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563702645521.png)

## NCM – Metric Learning

![1563702690701](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563702690701.png)

## Nearest Non-Outlier (NNO) Algorithm

![1563702815163](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563702815163.png)

## Training for Open World

![1563702892335](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563702892335.png)

## Learning Novel Concepts

![1563702928500](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563702928500.png)

![1563703056627](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563703056627.png)

![1563703077530](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563703077530.png)

## Opening Deep Networks

- Softmax always has a “winner” and re-weights scores
- Networks are easily fooled with high confidence
- “Fooling” images are obviously “open set” and should be rejected
- Adversarial images are more problematic -visually close but often far in label space
**A. Bendale and T. Boult “Towards Open Set Deep Networks” CVPR 2016 (Short oral)**

## MAV and OpenMax

• Insight: A class is represented not just by its output, but by its Mean Activation Layer (scores for all classes)
• MAV is just the average in penultimate layer
• “EVT distances” from MAV is a CAP model
• Given MAV, estimate probability of “unknown” via EVT and OpenMax = Softmax type normalized probability including probability of unknown