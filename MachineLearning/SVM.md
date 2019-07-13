# SVM（支持向量机）

>   《机器学习》周志华

## 间隔与支持向量

Training dataset：$D=\{(\boldsymbol{x_1},y_1),(\boldsymbol{x_2},y_2),\dots,(\boldsymbol{x_m},y_m)\},y_i\in\{-1,+1\}$

Goal: 基于训练集$D$在样本空间中找到一个划分超平面，将不同类别的样本分开。

存在多个划分超平面将两类训练数据分开，应该选择“正中间”的划分超平面，因为该超平面对训练样本的局部扰动的“容忍性“最好，而训练集有局限性或噪声。换言之，这个划分超平面的分类结果最鲁棒，对未见示例的泛化能力最强。

在样本空间中，划分超平面的线性方程：
$$
\boldsymbol w^\mathrm T \boldsymbol x+b=0
\tag{1}\label{1}
$$
$\boldsymbol w=(w_1;w_2;\dots;w_d)$为法向量，垂直于超平面，决定超平面的方向；

$b$为位移项，决定了超平面与原点之间的距离；因此划分超平面被$\boldsymbol w$和$b$确定。

样本空间中任意点$\boldsymbol x$到超平面$(\boldsymbol w,b)$的距离可写为
$$
r=\frac{|\boldsymbol w^\mathrm T\boldsymbol x+ b|}{\|\boldsymbol w\|_2}=\frac{|\boldsymbol w^\mathrm T\boldsymbol x+ b|}{\|\boldsymbol w\|}
\tag{2}\label{2}
$$
假设超平面$(\boldsymbol w,b)$能将训练样本正确分类，即对于$(\boldsymbol x_i,y_i) \in D$，则
$$
\left\{\begin{array}\boldsymbol w^\mathrm T\boldsymbol x_i+ b\geqslant+1,\quad y_i=+1; \\
\boldsymbol w^\mathrm T\boldsymbol x_i+ b\leqslant+1,\quad y_i=+1.\end{array}\right.
\tag{3}\label{3}
$$
support vector（支持向量）：距离超平面最近的几个训练样本点使得式子*(3)*的等号成立，两个异类支持向量到超平面的距离之和称为margin（间隔）
$$
\gamma=\frac{2}{\|\boldsymbol w\|}
\tag{4}\label{4}
$$
maximum margin（最大间隔）的划分超平面就是满足式*(3)*中约束的参数$\boldsymbol w$和$b$，使得$\gamma$最大，即
$$
\begin{align*}
&\max_{\boldsymbol w,b}\quad\frac{2}{\|\boldsymbol w\|} \\
&\begin{array}{}
\text {s.t.} \quad y_i(\boldsymbol w^\mathrm T\boldsymbol x_i+ b)\geqslant 1, &i=1,2,\dots,m. \\
\end{array}
\end{align*}
\tag{5}\label{5}
$$

式*(5)*等价为
$$
\begin{align*}
&\min_{\boldsymbol w,b}\quad\frac{1}{2}\|\boldsymbol w\|^2 \\
&\begin{array}{}
\text {s.t.} \quad y_i(\boldsymbol w^\mathrm T\boldsymbol x_i+ b)\geqslant 1, &i=1,2,\dots,m. \\
\end{array}
\end{align*}
\tag{6}\label{6}
$$
这就是support vector machine（SVM）的基本型。


