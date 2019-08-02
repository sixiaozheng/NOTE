# scipy.stats

```python
from scipy import stats
from scipy.stats import norm
import numpy as np

stats.norm.__doc__ # docstring

norm.a, norm.b # upper and lower bound of the distribution

np.random.seed(1234) # seed a global variable
norm.rvs(size=5, random_state=1234) # seed a local variable
```



```python
fig = plt.figure(figsize=(8, 6))
ax = fig.add_subplot(111)

ax.plot(x2, np.zeros(x2.shape), 'b+', ms=12)
ax.plot(x_eval, kde(x_eval), 'k-', label="Scott's Rule")
ax.plot(x_eval, kde2(x_eval), 'b-', label="Silverman's Rule")
ax.plot(x_eval, kde3(x_eval), 'g-', label="Scott * 0.2")
ax.plot(x_eval, kde4(x_eval), 'c-', label="Scott * 0.5")
ax.plot(x_eval, bimodal_pdf, 'r--', label="Actual PDF")

ax.set_xlim([x_eval.min(), x_eval.max()])
ax.legend(loc=2)
ax.set_xlabel('x')
ax.set_ylabel('Density')
ax.set_title("xxxx")
plt.show()
```



## 绘制一维正态分布概率密度图
```python
from scipy import stats
import matplotlib.pyplot as plt
x = np.linspace(stats.norm.ppf(0.01), stats.norm.ppf(0.99), 100)
plt.plot(x, stats.norm.pdf(x), 'r-', alpha=0.6, label='norm pdf')
plt.show()
```



## 绘制2维高斯分布图

```python
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
fig = plt.figure()
ax = Axes3D(fig)
rv = stats.multivariate_normal([0, 0], cov=1)
x, y = np.mgrid[-3:3:.15, -3:3:.15]
ax.plot_surface(x, y, rv.pdf(np.dstack((x, y))), rstride=1, cstride=1)
ax.set_zlim(0, 0.2)
# savefig('../figures/plot3d_ex.png',dpi=48)
plt.show()
```

## 多维情况下固定一维绘制一维高斯分布

```python
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
fig = plt.figure()
ax = Axes3D(fig)
rv = stats.multivariate_normal([0, 0], cov=1)

x, y = np.meshgrid(np.linspace(0, 0, 400), np.linspace(-3, 3, 400))
ax.plot_surface(x, y, rv.pdf(np.dstack((x, y))), rstride=1, cstride=1)
ax.set_zlim(0, 0.2)
# savefig('../figures/plot3d_ex.png',dpi=48)
plt.show()
```





