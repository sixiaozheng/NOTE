# EM算法 expectation maximization

EM算法用于含有隐变量（hidden variable）的概率模型参数的极大似然估计，或极大后验估计。EM算法每次迭代由两步组成：E步，求期望（expection）；M步，求极大（maximization）。

如果概率模型的变量都是观测变量（observable variable），那么给定数据，可以直接用极大似然估计，或贝叶斯估计法估计模型参数。如果概率模型含有观测变量和隐变量或潜在变量（latent variable）时，需要使用EM算法估计参数。

