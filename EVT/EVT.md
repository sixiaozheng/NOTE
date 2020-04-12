# Extreme Value Theory

>   An Introduction to Extreme Value Theory
>
>   Petra Friederichs

## Applications of EVT

-   Finance

    风险价值:每日最大损失

-   Hydrology（水文学）

    Q100:预计每100年一次的最大流量

-   Meteorology（气象学）

    飓风
    极端降水事件
    极端气候变化

## Application

![1563068011001](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563068011001.png)

-   In classical statistics: focus on AVERAGE behavior of stochastic process
    **central limit theorem**

-   In extreme value theory: focus on extreme and rare
    events
    **Fisher-Tippett theorem**


## Extreme Value Theory

-   Block Maximum
    $$
    M_n=\max\{X_1,\dots,X_n\}
    $$
    for $n\to\infty$

    $M_n$ follows a **Generalized Extreme Value (GEV)** distribution

    ![1563076501901](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563076501901.png)

-   Peak over Threshold (POT)
    $$
    \{X_i-u|X_i>u\}
    $$
    very large threshold $u$ follow a **Generalized Pareto Distribution (GPD)**
    ![1563076662898](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563076662898.png)

-   Poisson-Point GPD Process

    combines POT with Poisson point process

## GEV – Fisher-Tippett Theorem

The distribution of  $M_n=\max\{X_1,\dots,X_n\}$ converges to $(n\to\infty)$
$$
\xi \neq 0 \quad G(y)=\exp(-[1+\xi(\frac{y-\mu}{\sigma})]^{-\frac{1}{\xi}})\\
\xi = 0 \quad G(y)=\exp(-\exp(-\frac{y-\mu}{\sigma}))
$$
which is called the **Generalized Extreme Value (GEV)** distribution.
It has three parameters

-   $\mu$ location parameter
-   $\sigma$ scale parameter
-   $\xi$ shape parameter

## GEV – Types of Distributions

GEV has 3 types depending on shape parameter $\xi$ 
$$
x=\frac{y-\mu}{\sigma}
$$
![1563075371590](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563075371590.png)

![1563075453366](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563075453366.png)

![1563076058882](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563076058882.png)

![1563076105392](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563076105392.png)

![1563076129743](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563076129743.png)

## GEV – return level

![1563076346139](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563076346139.png)

## Peak over Threshold

The distribution of $Y_i:=X_i-u|X_i>u$ exceedances over large threshold $u$ are asymptotically distributed following a
**Generalized Pareto Distribution (GPD)**
$$
H(y|X_i>u)=1-(1+\xi\frac{y}{\sigma_u})^{-\frac{1}{\xi}}
$$
two parameters
    $\sigma$ scale parameter
    $\xi$ shape parameter

advantage: more efficient use of data
disadvantage: how to choose threshold not evident

## POT – Types of Distribution

GDP has same 3 types as GEV depending on shape parameter $\xi$

![1563077333487](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563077333487.png)

## Poisson Point – GPD Process

Poisson point – GPD process with intensity
$$
\Lambda(A)=(t_2-t_1)[1+\xi(\frac{y-u}{\sigma_u})]^{-\frac{1}{\xi}} \quad \text{on} \quad A=(t_1,t_2)\times(y,\infty)
$$
![1563085431024](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563085431024.png)

## Estimation and Uncertainty

![1563086001457](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563086001457.png)

## Maximum Likelihood Method

![1563086118811](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563086118811.png)

## To Take Home

![1563086210185](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563086210185.png)

## References

![1563086274183](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563086274183.png)



## Fisher–Tippett–Gnedenko theorem

$$
X_{1},X_{2}\ldots ,X_{n}\ldots \\
M_{n}=\max\{X_{1},\ldots ,X_{n}\} \\
(a_n, b_n) \quad  a_{n}>0\\
\lim _{{n\to \infty }}P\left({\frac  {M_{n}-b_{n}}{a_{n}}}\leq x\right)=F(x)
$$

limit distribution ![F](https://wikimedia.org/api/rest_v1/media/math/render/svg/545fd099af8541605f7ee55f08225526be88ce57) belongs to either the [Gumbel](https://en.wikipedia.org/wiki/Gumbel_distribution), the [Fréchet](https://en.wikipedia.org/wiki/Fréchet_distribution) or the [Weibull](https://en.wikipedia.org/wiki/Weibull_distribution) [family](https://en.wikipedia.org/wiki/Location-scale_family). These can be grouped into the [generalized extreme value distribution](https://en.wikipedia.org/wiki/Generalized_extreme_value_distribution).

## Generalized extreme value distribution

Using the standardized variable $s=(x-\mu )/\sigma$, where $\mu \in \mathbb {R}$ is the location parameter and $\sigma >0$ is the scale parameter, the cumulative distribution function of the GEV distribution is
$$
{\displaystyle F(s;\xi )={\begin{cases}\exp(-(1+\xi s)^{-1/\xi })&\xi \neq 0\\\exp(-\exp(-s))&\xi =0\end{cases}}}
$$
where $\xi \in \mathbb {R}$ is the shape parameter, called the **tail index**, models the distribution tails.

*μ* ∈ **R** — [location](https://en.wikipedia.org/wiki/Location_parameter),
*σ* > 0 — [scale](https://en.wikipedia.org/wiki/Scale_parameter),
*ξ* ∈ **R** — [shape](https://en.wikipedia.org/wiki/Shape_parameter).

*x* ∈ [ *μ* − *σ / ξ*, +∞)   when *ξ* > 0,
*x* ∈ (−∞, +∞)   when *ξ* = 0,
*x* ∈ (−∞, *μ* − *σ / ξ* ]   when *ξ* < 0.

-   [Gumbel](https://en.wikipedia.org/wiki/Gumbel_distribution) or type I extreme value distribution $\xi =0$

$$
F(x;\mu,\sigma,0)=e^{-e^{-(x-\mu)/\sigma}}\;\;\; \text{for} \;\; x\in\mathbb R.
$$

-   [Fréchet](https://en.wikipedia.org/wiki/Fréchet_distribution) or type II extreme value distribution, if $\xi =\alpha ^{-1}>0$ and $y=1+\xi (x-\mu )/\sigma$
    $$
    F(x;\mu,\sigma,\xi)=\begin{cases} e^{-y^{-\alpha}} & y > 0 \\ 0 & y \leq 0. \end{cases}
    $$

-   Reversed [Weibull](https://en.wikipedia.org/wiki/Weibull_distribution) or type III extreme value distribution, if $\xi =-\alpha ^{-1}<0$ and $y=-\left(1+\xi (x-\mu )/\sigma \right)$

$$
F(x;\mu,\sigma,\xi)=\begin{cases} e^{-(-y)^{\alpha}} & y<0 \\ 1 & y\geq 0 \end{cases}
$$

-   The probability density function of the standardized distribution is

$$
{\displaystyle f(s;\xi )={\begin{cases}(1+\xi s)^{(-1/\xi )-1}\exp(-(1+\xi s)^{-1/\xi })&\xi \neq 0\\\exp(-s)\exp(-\exp(-s))&\xi =0\end{cases}}}
$$

again valid for ![{\displaystyle s>-1/\xi }](https://wikimedia.org/api/rest_v1/media/math/render/svg/505682aae27709b6f31cd3dd3740ccc54b059ad6) in the case ![\xi>0](https://wikimedia.org/api/rest_v1/media/math/render/svg/973be61089b52fdb5da82587ce45d0febc1aedac), and for![{\displaystyle s<-1/\xi }](https://wikimedia.org/api/rest_v1/media/math/render/svg/f43d325dfeaff7bccb87fd965f1c5edba275df12) in the case ![\xi<0](https://wikimedia.org/api/rest_v1/media/math/render/svg/e9d724a5e116e041411f59b3ad16db58de2e688f). The density is zero outside of the relevant range. In the case ![\xi =0](https://wikimedia.org/api/rest_v1/media/math/render/svg/da5354e193004a0e2f16e7d4a76ea499ffcca225) the density is positive on the whole real line.

Remark I: The theory here relates to data **maxima** and the distribution being discussed is an extreme value distribution for maxima. A generalized extreme value distribution for data **minima** can be obtained, for example by **substituting (−*x*) for *x*** in the distribution function, and **subtracting from one**: this yields a separate family of distributions. 将表达式中的x替换成-x，然后1-F(-x)就得到建模minima的pdf，如W-SVM中的Weibull。

Remark II: The ordinary Weibull distribution arises in reliability applications and is obtained from the distribution here by using the variable $t=\mu -x$, which gives a strictly positive support - in contrast to the use in the extreme value theory here. This arises because the Weibull distribution is used in cases that deal with data minima rather than data maxima. The distribution here has an addition parameter compared to the usual form of the Weibull distribution and, in addition, is reversed so that the distribution has an upper bound rather than a lower bound. Importantly, in applications of the GEV, the upper bound is unknown and so must be estimated, while when applying the Weibull distribution the lower bound is known to be zero.

![1564038771899](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564038771899.png)

**极值分布的类型完全由形状参数$\xi$来确定， 与位置参数$\mu$和尺度参数$\sigma$无关**

![1564038495787](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564038495787.png)

![1564038537049](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564038537049.png)

![1564038550176](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564038550176.png)

$x\to\infty$时，

-   Gumbel，I型分布的pdf呈指数趋势下降，右偏
-   Fréchet，II型分布的pdf呈多项式趋势下降，右偏，较长尾部，呈厚尾
-   Weibull，III型分布具有有限的上端点，左偏，细尾分布

当$\alpha\to\infty$时，Fréchet和Weibull分布即为Gumbel分布

样本
$$
X_1,X_2,\dots,X_T
$$
区间长度：$n$

区间数：$m=\frac{T}{n}$
$$
[X_1,\dots,X_n|X_{n+1},\dots,X_{2n}|\dots|X_{(m-1)n+1}\dots,X_{mn}]
$$
区间最大值序列：$D_{BMM}=\{M^{(1)}_n,\dots,M^{(m)}_n\}$

似然函数:
$$
L_n(\xi,\mu,\sigma)=-m\log(\sigma)-(1+\frac{1}{\xi})\sum^m_{i=1}\log(1+\xi(\frac{M^{(i)}_n-\mu}{\sigma}))-\sum^m_{i=1}(1+\xi(\frac{M^{(i)}_n-\mu}{\sigma}))^{-\frac{1}{\xi}}, \quad \xi\neq0 \\
L_n(\mu,\sigma)=-m\log(\sigma)-\sum^m_{i=1}(\frac{M^{(i)}_n-\mu}{\sigma})-\sum^m_{i=1}\exp(-(\frac{M^{(i)}_n-\mu}{\sigma})), \quad \xi=0
$$


## Pickands–Balkema–de Haan theorem

$$
{\displaystyle F_{u}(y)=P(X-u\leq y|X>u)={\frac {F(u+y)-F(u)}{1-F(u)}}}
$$

$$
0\leq y\leq x_{F}-u
$$

$F_{u}$ well approximated by the [generalized Pareto distribution](https://en.wikipedia.org/wiki/Generalized_Pareto_distribution). 
$$
F_{u}(y)\rightarrow G_{{k,\sigma }}(y),{\text{ as }}u\rightarrow \infty
$$

## The Generalised Pareto Distribution (GPD)

![1563516619208](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1563516619208.png)

-   $G_1$,type I,指数分布，$\xi=0$, 细尾
-   $G_2$,type II,Pareto分布，$\xi>0$，$\xi$越大，尾越大
-   $G_3$,type III,Beta分布，$\xi<0$，$\xi$越小，GPD集中在有限域$[0,-\frac{1}{\xi}]$内，负数越小范围越窄。

$x=\{x_1,\dots,x_n\}$

似然函数
$$
L(x;\sigma,\xi)=n\log\xi-n\log\sigma-(1+\frac{1}{\xi})\sum^n_{i=1}\log(1+\frac{\xi}{\sigma}x_i), \quad
\xi>0, x_i\geqslant0, \quad \xi<0, 0\leqslant x_i\leqslant-\frac{\sigma}{\xi} \\
L(x;\sigma)=-n\log\xi-\sigma^{-1}\sum^n_{i=1}x_i, \quad \xi=0
$$


PDF

![Gpdpdf](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d7/Gpdpdf.svg/1024px-Gpdpdf.svg.png)

CDF

![Gpdcdf](https://upload.wikimedia.org/wikipedia/commons/thumb/5/55/Gpdcdf.svg/1024px-Gpdcdf.svg.png)

如果极大值$M_n（n\to \infty）$近似服从GEV分布$H(x;\mu,\sigma,\xi)$,则超出量X-u近似服从GPD分布$G(y;\beta(u),\xi)$,且具有相同的形状参数$\xi$.

## Implementation

-   GEV

    **scipy.stats.genextreme**

    A generalized extreme value continuous random variable.

    For c=0, [`genextreme`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.genextreme.html#scipy.stats.genextreme) is equal to [`gumbel_r`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.gumbel_r.html#scipy.stats.gumbel_r). The probability density function for [`genextreme`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.genextreme.html#scipy.stats.genextreme) is:

    ![1564038979032](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564038979032.png)

    Note that several sources and software packages use the opposite convention for the sign of the shape parameter c.

    [`genextreme`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.genextreme.html#scipy.stats.genextreme) takes `c` as a shape parameter for c.

-   Gumbel type I

    **scipy.stats.gumbel_r**

    A right-skewed Gumbel continuous random variable.

    The probability density function for [`gumbel_r`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.gumbel_r.html#scipy.stats.gumbel_r) is:

    ![1564039104153](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564039104153.png)

    The Gumbel distribution is sometimes referred to as a **type I** Fisher-Tippett distribution. It is also related to the extreme value distribution, log-Weibull and Gompertz distributions.

    ![../_images/scipy-stats-gumbel_r-1.png](https://docs.scipy.org/doc/scipy/reference/_images/scipy-stats-gumbel_r-1.png)

-   Fréchet type II

    **scipy.stats.invweibull**

    An inverted Weibull continuous random variable.

    This distribution is also known as the Fréchet distribution or the **type II** extreme value distribution.

    The probability density function for [`invweibull`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.invweibull.html#scipy.stats.invweibull) is:

    ![1564039220797](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564039220797.png)

    ![1564039251957](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564039251957.png)

    [`invweibull`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.invweibull.html#scipy.stats.invweibull) takes `c` as a shape parameter for c.

    ![../_images/scipy-stats-invweibull-1.png](https://docs.scipy.org/doc/scipy/reference/_images/scipy-stats-invweibull-1.png)

-   Reversed Weibull type III

    **scipy.stats.weibull_max**

    Weibull maximum continuous random variable.

    The probability density function for [`weibull_max`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.weibull_max.html#scipy.stats.weibull_max) is:

    ![1564039377650](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564039377650.png)

    ![1564039390323](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\1564039390323.png)

    [`weibull_max`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.weibull_max.html#scipy.stats.weibull_max) takes `c` as a shape parameter for c.
    
    ![../_images/scipy-stats-weibull_max-1.png](https://docs.scipy.org/doc/scipy/reference/_images/scipy-stats-weibull_max-1.png)

*   Weibull 

    **scipy.stats.weibull_min**

    Weibull minimum continuous random variable.

    The probability density function for [`weibull_min`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.weibull_min.html#scipy.stats.weibull_min) is:

    ![image-20191204175348728](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\image-20191204175348728.png)

    ![image-20191204175435136](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\image-20191204175435136.png)

    [`weibull_min`](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.weibull_min.html#scipy.stats.weibull_min) takes `c` as a shape parameter for c.

    ![../_images/scipy-stats-weibull_min-1.png](https://docs.scipy.org/doc/scipy/reference/_images/scipy-stats-weibull_min-1.png)