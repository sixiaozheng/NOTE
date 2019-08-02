# **Statistical Methods for Open Set Recognition**

>   Walter J. Scheirer and Terrance E. Boult 

# Part 1: An Introduction to the Open Set Recognition Problem

## Open Space in Classification

![1563592400013](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563592400013.png)

## general recognition problem

Duin and Pekalska*: how one should approach multi-class recognition is still an open issue
- Is it a series of binary classifications?
- Is it a search performed for each possible class?
- What happens when some classes are ill-sampled, not sampled at all or undefined?

>   R. P. Duin and E. Pekalska, “Open Issues in Pattern Recognition,” in Computer Recognition Systems, M. Kurzynski, E. Puchala, M. Wozniak, and A. Zolnierek, Eds. Springer, 2005, pp. 27–42.

![1563592846515](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563592846515.png)

## Definitions

**Closed Set Recognition**: all testing classes are known at training time
**Open Set Recognition**: incomplete knowledge of the world is present at training time, and unknown classes can be submitted to an algorithm during testing

## A surprising finding…

![1563593325964](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563593325964.png)

## Linear separation of CNN feature representations

![1563593368128](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563593368128.png)

## Read-out layer

![1563593571241](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563593571241.png)

## Evolving images to match CNN classes

![1563593808635](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563593808635.png)

>   A. Nguyen, J. Yosinski, and J. Clune, “Deep Neural Networks are Easily Fooled,” CVPR 2015.

## But you don’t have to use tricky manipulations

![1563593851691](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563593851691.png)

**Are performance measures misleading us?**

<u>CNN很容易对一些图片错误分类，比如一些人工生成的复杂图片，或者飞机不同角度的图片。所以，性能度量是否在误导我们？</u>

## Psychophysics pipeline

![1563594856156](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563594856156.png)

Class Canonical View 类规范视图，可由其他的视图的图片，经过CNN合成规范视图，提高后续的分类结果。

![1563595281758](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563595281758.png)

## Airliner Gaussian Blur（高斯模糊） 

![1563595444402](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563595444402.png)

**What standard options do we have to solve this problem?**

## Binary Classification

![1563595524497](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563595524497.png)

## Multi-class 1-vs-All Classification

![1563595607738](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563595607738.png)

## 1-class Classification

![1563595655829](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563595655829.png)

<u>binary (1-vs-1) , multi-class (1-vs-All) and 1-class classification 对于open set problems都无法解决，都对known classes and unknown classes都分类错误</u>

>   “All positive examples are alike; each negative example is negative in its own way” Zhao and Huang (with some help from Tolstoy) CVPR 2001

## openness

![1563602988629](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563602988629.png)

## Fundamental multi-class recognition problem

![1563603795565](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563603795565.png)

## Open Space

![1563603837237](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563603837237.png)

- Open space is the space far from known data
- We need to address the infinite half-space problem of linear classifiers
- Principle of Indifference[*]

    - If there is no known reason to assign probability, alternatives should be given equal probability
    - One problem: we need the distribution to integrate to 1!

[*] J.M. Keynes, A Treatise on Probability. Macmillan & Company, Limited, 1921.

## Open Space Risk

Open Space Risk: the relative measure of open space to the full space

![1563604414118](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563604414118.png)

## The open set recognition problem

![1563604798037](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563604798037.png)

## The open set recognition problem

**Minimize open set risk:**

![1563604841357](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563604841357.png)

**The definition doesn’t tell us how to define O**

## Abating Process

• Model enforced decay of probability away from supporting evidence

![1563605356954](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563605356954.png)

## The Compact Abating Probability Model

Conceptual example: if we are labeling location data using training data only from Campinas, Brazil, it would be risky it would be risky to apply that model to South Bend, Indiana

![1563605588187](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563605588187.png)

**Idea: ensure that the recognition function is decreasing away from the training data, so that thresholding it limits the labeled region.**

## Definition of Open Space

![1563605818209](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563605818209.png)

Treat r as a problem specific parameter, be estimated via calibration, e.g. the maximum (or average) spacing between training samples.

## Abating Bound

![1563610572446](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563610572446.png)

![1563606126190](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563606126190.png)
$x_i\in K$indicates a specific positive training example, and $x\in X$ any example.

![1563606140638](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563606140638.png)

<u>空间影响随距离x*的增大而减小，A(.)就是f的bound</u>

## Abating Probabilistic Point Model

![1563606423406](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563606423406.png)

Abating Probabilistic Point Model: $p_f(s;y)$ the probability of the score s from an RBF kernel K being associated with the given class y.

For recognition we need to combine multiple data points to build an effective class model. Consider fusing the abating models from the known training data

<u>随着任意两点空间距离的增大，点间关联的概率减小。</u>

## Fused Abating Property

![1563606572540](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563606572540.png)

## Compact Abating Probability (CAP) Model

![1563606876117](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563606876117.png)

$\forall x\in X$Features beyond a given thresholded τ from the closest training point have zero probability 

## Theorem 1

![1563607473748](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563607473748.png)

如果在离xi（中心）的距离r之外的open space的M(x)>0，则存在open space risk。所以如果r>$\tau$，则在open space，M(x)一定<0.

## Proof of Theorem 1

![1563608509230](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563608509230.png)

## Corollary 1

![1563613097103](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563613097103.png)

注意，CAP属性并不保证模型在紧凑支持区域内分配正标签——它只是确保在区域外分配正标签的概率为零。

## How do we get from Corollary 1 to an algorithm?

- No guarantee that the model assigns positive labels within the compact support region
	- CAP ensures that there is a zero probability of doing so outside the region
- Quality of the CAP model depends on how well the probabilities model the actual underlying positive region
- **1-class SVM + Non-linear (RBF) kernel**

## Theorem 2

![1563614852424](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563614852424.png)

## Proof of Theorem 2

![1563614873978](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563614873978.png)

## Goal: Multi-class Open Set Recognition

![1563615728776](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563615728776.png)

## Model: Compact Abating Probability

![1563615779000](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563615779000.png)

one-class models are typically less effective than binary machines.

the decision score of a binary SVM is not a canonical sum.(sum不等于1)

## Binary RBF SVM Incorporating a CAP Model

-   a discriminative classifier estimating $P(y|x)$, trained on $x\in \mathcal K$,should be viewed as $P(y|x\in \mathcal K)$, and has no bias for prediction when $x\notin \mathcal K$. 
-   combine probabilities computed for both one-class RBF SVMs and binary RBF SVMs.
-   one-class SVM CAP model as a conditioner: if the one-class SVM predicts $P_O(y|x)>\delta_\tau$,  even with a very low threshold $\delta_\tau$, that a given input $x$ is a member of class y, then we will consider the binary classifier’s estimates of $P(y|x)$.

-   a set of known classes $\mathcal Y$
-   for a lass $y\in\mathcal Y$, we can use positive scores from $y$ to estimate $P^+(y|x)$. 
-   We also use negative scores from other known classes to estimate $P^-(\mathcal Y\backslash y|x)$. 
-   To minimize our open space risk, we only consider $P^-$ and $P^+$ when $P_O(y|x)>\delta_\tau$, when open space risk is small.

## Grounded Probability Estimation

-   reverse Weibull: the largest scores from the negative examples because they are bounded from above

-   Weibull: the smallest scores from the positive examples because they are bounded from below

![1563626332801](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563626332801.png)

-   the reverse Weibull and Weibull have three parameters: location $\nu$, scale $\lambda$, and shape $\kappa$

-   applying Maximum Likelihood Estimation to estimate the $\nu_\eta$, $\lambda_\eta$, $\kappa_\eta$that best fit $\eta$ and the $\nu_\psi$ , $\lambda_\psi$, $\kappa_\psi$  that best fit $\psi$.
-   To produce a probability score for a particular SVM decision f(x), we use the CDF defined by the parameters.
-   Weibull CDF: the probability that the input is from the positive class

![1563626621367](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563626621367.png)

-   reverse Weibull CDF: the probability that the input is NOT from any of the known negative classes

    ![1563626671903](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563626671903.png)

## Support Vector Data Description (SVDD)

D.M.J. Tax and R.P.W. Duin: Support vector data description. Machine Learning 54, 45–66
• Hypersphere with the minimum radius is estimated around the positive class data that encompasses almost all training points

![1563629829075](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563629829075.png)

- Sensitive to feature scaling (Tax and Duin ASCI 2002)
- Difficult to solve using good numerical optimization (Chang et al. NTU Tech. Report 2013)
- Far less effective than binary classifiers when some sampling of negatives is available
- Overfits the training data

## 1-Class SVM

- Only positive data at training time
- “Origin” defined by the kernel serves as the only member of a “second class”
- Training object yields a binary classifier f
- When used, usually for outlier or anomaly detection

![1563630060942](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563630060942.png)

## 1-Class SVM Objective

![1563630286559](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563630286559.png)

ν controls the upper bound on training error

## Why didn’t the 1-class SVM catch on?

Zhou and Huang Multimedia Systems 2003
- Kernel and parameter selection
‣ Gaussian kernels lead to over-fitting
‣ Parameters chosen in ad hoc fashion
‣ An issue in other domains too!

## Problems with Existing Models for Binary Problems

![1563630862433](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563630862433.png)

## Normalized decision scores for 1-Class SVM

![1563630945265](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563630945265.png)

## Normalized decision scores for Binary SVM

![1563630968950](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563630968950.png)

## Open World Recognition

![1563631488569](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563631488569.png)

![1563631582440](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563631582440.png)

## Recall the CAP Model

![1563631675760](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563631675760.png)

## Theorem on Open Space Risk for Model Combination

![1563631699954](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563631699954.png)

## Theorem: Open Space Risk for Transformed Spaces

![1563631760232](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563631760232.png)