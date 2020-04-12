## 命令行运行R script

```shell
R --no-save -q < terminalR.R > out.txt
R --no-save --slave < terminalR.R
```

## R中的数据结构

*   数据集：由数据构成的一个矩形数组，行表示观测（observation），列（variable）表示变量。
*   R中的数据结构：标量、向量、数组、数据框、列表
*   R中的数据类型：数值型、字符型、逻辑型（布尔型）、复数型（虚数）、原生型（字节）。

![image-20200104132857173](C:\Users\ThinkToKnow\AppData\Roaming\Typora\typora-user-images\image-20200104132857173.png)

### 向量

*   创建

```R
a<-c(1,2,3,4,5,6,-1,-2)
b<-c("one","w","cs")
d<-c(TRUE,FALSE,TRUE,FALSE)
```

当个向量中的数据必须拥有相同的类型或模式。最不要使用c作为对象名，否则可能与c()函数混淆。

*   访问

``` R
a[1] # R中向量的index从1开始
a[c(3,5)]
a[1:4] # 等价于a[c(1,2,3,4)]
```

### 矩阵

*   创建

```R
y<-matrix(1:20,nrow=5,ncol=4)

cells<-c(1,26,24,68)
rnames<-c("R1","R2")
cnames<-c("C1","C2")
mymatrix<-matrix(cells,nrow=2,ncol=2,byrow=TRUE,dimnames=list(rnames,cnames)) # 按行填充，默认按列填充
```

*   访问

```R
y[2,]
y[,2]
y[1,4]
y[1,c(2,3)]
```

### 数组

*   创建

```R
dim1<-c("A1","A2")
dim2<-c("B1","B2","B3")
dim3<-c("C1","C2","C3","C4")
z<-array(1:24,c(2,3,4),dimnames=list(dim1,dim2,dim3))
```

