 1核心定理：Lehmann-Scheffé 定理
🎓 定理内容概述
设 $X_1, \dots, X_n$ 是来自分布 $f(x;\theta)$ 的样本，如果：
- $T(X)$ 是参数 $\theta$ 的**充分完全统计量**。
- $g(T)$ 是一个仅依赖于 $T$ 的函数，且它是 $\theta$（或其函数 $\tau(\theta)$）的**无偏估计**。
那么，$g(T)$ 就是 $\theta$（或 $\tau(\theta)$）的**唯一 UMVUE**。

步骤1：寻找充分统计量
步骤2：构造无偏性
为了找到真正的 UMVUE，我们需要找到充分统计量 $T$ 的某个函数 $g(T)$，使得：
$$E[g(T)] = \theta$$
## 例1：指数分布 （考试很有可能！）
### 设 $X_1, X_2, \dots, X_n$ 是来自指数分布 $f(x; \theta) = \theta e^{-\theta x}$ ($x > 0$) 的独立同分布样本，求参数 $\theta$ 的 **UMVUE**。

在**指数分布**中，充分统计量 $T = \sum_{i=1}^n X_i$ 服从一个非常著名的分布——**伽马分布**，记作 $T \sim \Gamma(n, \theta)$。
对于 $T \sim \Gamma(n, \theta)$，它的概率密度函数中包含一个结论：
$$E[T^{-1}] = E\left[\frac{1}{\sum X_i}\right] = \frac{\theta}{n-1}$$
#### 步骤一：寻找完全充分统计量
1.似然函数：
$L(\theta)=\prod_{i=1}^{n}\theta e^{-\theta x_{i}}=\theta^{n}e^{-\theta \sum x_{i}}$
将$L(\theta)$拆分成$g(T(x),\theta)\cdot h(x)$
$T(x)=\sum x_{i}$为充分统计量
	ps:指数分布属于指数族分布，对于指数族分布，这种形式的统计量通常也是完全的。
#### 步骤二：寻找一个关于T的函数g(T)，使得$E[g(T)]=\theta$
在指数分布中，$\theta$ 通常出现在分母位置（例如 $E(\bar{X}) = 1/\theta$）。
✍️指数的期望计算：$$E(\bar{X})=\int xf(x)dx=\int x\theta e^{-\theta x }dx=\frac{1}{\theta}$$
	核心思路：分部积分法：$\int u dv=uv-\int vdu$
	选定$u=x,dv=\theta e^{-\theta x}$
	$\int x\theta e^{{-\theta x}}=x \cdot (-e^{-\theta x})-\int(-e^{-\theta x})dx=x \cdot(-e^{-\theta x})-\frac{1}{\theta}e^{-\theta x}$
	代入积分上下限$[0,\infty]$得到：$$E(\bar{X})=\frac{1}{\theta}$$
如果我们想让 $\theta$ 跑到分子上来，直觉告诉我们要研究 **$T$ 的倒数**，即 $T^{-1}$。
因为$T=\sum x_{i}$服从伽马分布$\Gamma(n,\theta)$，它的概率密度函数$f_{T}(x)$是：$$f_{T}(t)=\frac{\theta^n}{\Gamma(n)}t^{n-1}e^{-\theta t}$$
根据期望的定义：
	ps:如果我们要计算 $E[g(T)]$，可以直接使用 **$T$ 原本的密度函数** $f_T(t)$，只需要在积分号里把变量代换成 $g(t)$ 即可：
$$E(g(T))=\int g(t)f_{T}(t)dt$$
因为找的是$T^{-1}$的期望，所以$g(T)=T^{-1}$
$E(g(T))=\int\frac{1}{t}\frac{\theta^n}{\Gamma(n)}t^{n-1}e^{-\theta t}dt$，$=\frac{\theta^n}{\Gamma(n)}\int t^{n-2}e^{-\theta t}dt$
所以$E(T^{-1})=\frac{\theta^n}{\Gamma(n)}\int t^{n-2}e^{-\theta t}dt$
	使用伽马积分的通式：$\int_0^\infty t^{k-1} e^{-\theta t} dt = \frac{\Gamma(k)}{\theta^k}$
所以$k=n-1$,得到：$$E(T^{-1})=\frac{\theta^{n}}{\Gamma(n)}\cdot \frac{\Gamma(n-1)}{\theta^{n-1}}=\frac{\theta}{n-1}$$
回到UMVUE：
所以$E\left( \frac{1}{T} \right)=\frac{\theta}{n-1}$，为了使$E\left( \frac{1}{T} \right)=\theta$，所以令$\frac{1}{T}$前乘系数$(n-1)$，所以$E((n-1)T^{-1})=\theta$
🔍所以参数$\theta$的UMVUE为：$$\hat{\theta}_{{UMVUE}}=\frac{n-1}{n \bar{X}}$$
	ps：找$\theta$的UMVUE是指，找到一个统计量$\hat{g}_1(T)$，使得 $E[\hat{g}_1(T)] = \theta$
	如果是找$\theta^2$的UMVUE，此时 $g(\theta) = \theta^2$。我们的目标是找另一个统计量 $\hat{g}_2(T)$，使得 $E[\hat{g}_2(T)] = \theta^2$。

### 扩展：如何找$\theta^2$的UMVUE：
令$g(\theta)=\theta^2$，充分统计量仍然是$T=\sum x_{i}$
那么，只要找到一个关于T的函数，使其期望等于$\theta^2$，它就是唯一的UMVUE。
$E(T^{-2})=\int \frac{1}{t^2}f_{T}(t)dt=\frac{\theta^2}{(n-2)(n-1)}$
所以$$\hat{\theta^2}_{UMVUE}=\frac{(n-2)(n-1)}{n^2\bar{X^2}}$$
### 总结的指数分布的参数的UMVUE结果
| **目标函数 g(θ)**       | **基础统计量** | **期望结果 (会有多余常数)**                    | **最终 UMVUE (修正后)** |
| ------------------- | --------- | ------------------------------------ | ------------------ |
| **$1/\theta$** (期望) | $\bar{X}$ | $E[\bar{X}] = 1/\theta$              | $\bar{X}$ (无需修正)   |
| **$\theta$** (率参数)  | $1/T$     | $E[1/T] = \theta/(n-1)$              | $(n-1)/T$          |
| **$1/\theta^2$**    | $T^2$     | $E[T^2] = \theta^{-2} \cdot n(n+1)$  | $T^2 / [n(n+1)]$   |
| **$\theta^2$**      | $1/T^2$   | $E[1/T^2] = \theta^2 / [(n-1)(n-2)]$ | $(n-1)(n-2)/T^2$   |
### 模拟题：
题目：
设 $X_1, X_2, \dots, X_n$ 是来自指数分布总体 $X \sim Exp(\theta)$ 的简单随机样本，其概率密度函数为：
$$f(x; \theta) = \theta e^{-\theta x}, \quad x > 0, \theta > 0$$
1. **求参数 $\theta$ 的一致最小方差无偏估计（UMVUE）**；
2. **求样本所包含的参数 $\theta$ 的 Fisher 信息量 $I_n(\theta)$**；
3. **证明所得的 UMVUE 是否为参数 $\theta$ 的有效估计**。



前2题略
3.**Cramér-Rao 下界 (CRLB)**：$\frac{1}{I_n(\theta)} = \frac{\theta^2}{n}$。
- $E[\hat{\theta}] = (n-1) E[\frac{1}{T}] = (n-1) \cdot \frac{\theta}{n-1} = \theta$ 
- $E[\hat{\theta}^2] = (n-1)^2 E[\frac{1}{T^2}] = (n-1)^2 \cdot \frac{\theta^2}{(n-1)(n-2)} = \frac{n-1}{n-2} \theta^2$
那么方差就是：
$$Var(\hat{\theta}) = E[\hat{\theta}^2] - [E(\hat{\theta})]^2 = \frac{n-1}{n-2} \theta^2 - \theta^2=\frac{\theta^2}{n-2}$$

### 复习题
#### ⭐**练习一·第二大题**
题目：设总体 $X$ 的密度函数为：$$f(x;\theta)=\begin{cases}\frac{1}{\theta^{2}}xe^{-\frac{x}{\theta}},&x>0\\ 0,&x\le0\end{cases}$$
其中 $\theta > 0$。$x_1, x_2, \dots, x_n$ 是来自总体 $X$ 的简单样本。
(1) 求 $\theta$ 的一致最小方差无偏估计 (UMVUE)；
(2) 问该 UMVUE 是否是有效估计？说明理由。

答：
(1)
似然函数是$L(\theta)=\prod_{i=1}^{n} \frac{1}{\theta^2}xe^{-x/\theta}=\frac{1}{\theta^{2n}}\prod x_{i}e^{-\sum x_{i}/\theta}$
利用因子分解定理：$L(\theta)=g(T(x),\theta)\cdot h(x)$
$g(T(x),\theta)=\frac{1}{\theta^{2n}}e^{-\sum x_{i}/\theta};h(x)=\prod x_{i}$
所以$T(x)=\sum x_{i}$,为充分统计量。
$E(X)=\int xf(x)dx=\int x^2 \frac{1}{\theta^2}e^{-x/\theta}dx=x^{2}\cdot\left( -\frac{1}{\theta}e^{\frac{-x}{\theta} }\right)-\int 2x\cdot\left( -\frac{1}{\theta} e^{-x/\theta}\right)dx$
其中$\int 2x\cdot\left( -\frac{1}{\theta} e^{\frac{-x}{\theta}}\right)dx=2x\cdot e^{-x/\theta}-\int2e^{-x/\theta}dx=2x\cdot e^{-x/\theta}+2\theta e^{-x/\theta}$
$x^{2}\cdot\left( -\frac{1}{\theta}e^{\frac{-x}{\theta} }\right)-\int 2x\cdot\left( -\frac{1}{\theta} e^{-x/\theta}\right)dx=x^{2}\cdot\left( -\frac{1}{\theta}e^{\frac{-x}{\theta} }\right)-(2x\cdot e^{-x/\theta}+2\theta e^{-x/\theta})=e^{-x/\theta}\left[ -\frac{x^2}{\theta} -2x-2\theta\right]$
积分上下限为$0-\infty$，所以$E(X)=2\theta$
$E(T)=E\left( \sum X_{i} \right)=2n\theta$，所以要令$E(q(T)=\theta$，则$q(T)=\frac{1}{2n} T=\frac{1}{2n} \sum X_{i}$
由于T是充分完全统计量，且T/2n是无偏的，所以是唯一的UMVUE,$\hat{\theta}_{UMVUE}=\frac{1}{2n}\sum x_{i}$
(2)
Fisher信息量$I_{n}(\theta)=-E[二阶导]$
$\ln L(\theta)=-2n\ln(\theta)+\ln\left( \prod x_{i} \right)-\frac{\sum{x_{i}}}{\theta}=-2n\ln(\theta)+\sum \ln(x_{i})-\frac{\sum x_{i}}{\theta}$
$\frac{\partial \ln L(\theta)}{\partial \theta}=-\frac{2n}{\theta}+\frac{1}{\theta^2}\sum x_{i}$
$\frac{\partial^2 \ln L(\theta)}{\partial \theta^2}=\frac{2n}{\theta^2}-\frac{2}{\theta^3}\sum x_{i}$
$E\left( \frac{2n}{\theta^2}-\frac{2}{\theta^3}\sum x_{i} \right)=\frac{2n}{\theta^2}-\frac{2}{\theta^3}E\left( \sum x_{i} \right)=\frac{2n}{\theta^2}-\frac{2}{\theta^3}\cdot2n\theta=-\frac{2n}{\theta^2}$
所以$I_{n}(\theta)=\frac{2n}{\theta^2}$
C-R下界为：$\frac{1}{I_{n}(\theta)}=\frac{\theta^2}{2n}$
$Var(\hat{\theta})=E(\theta^2)-(E(\theta))^2$
$E(X^2)=e^{-x/\theta}\left[ -\frac{x^3}{\theta} -3x^2+6x-6\theta\right]=6\theta$
	$$E(X^2) = \int_0^\infty x^2 \cdot \frac{1}{\theta^2} x e^{-x/\theta} dx = \frac{1}{\theta^2} \int_0^\infty x^3 e^{-x/\theta} dx$$为了算出这个积分，我们先看**不定积分**部分。设 $I = \int x^3 e^{-x/\theta} dx$。
	**第一次分部积分**
	令 $u = x^3 \Rightarrow du = 3x^2 dx$
	令 $dv = e^{-x/\theta} dx \Rightarrow v = -\theta e^{-x/\theta}$
	根据 $\int u dv = uv - \int v du$：$$I = -x^3 \theta e^{-x/\theta} - \int (-\theta e^{-x/\theta}) \cdot 3x^2 dx = -x^3 \theta e^{-x/\theta} + 3\theta \int x^2 e^{-x/\theta} dx$$第二次分部积分
	对 $\int x^2 e^{-x/\theta} dx$ 再次使用分部积分（令 $u=x^2, dv=e^{-x/\theta}dx$）：$$\int x^2 e^{-x/\theta} dx = -x^2 \theta e^{-x/\theta} + 2\theta \int x e^{-x/\theta} dx$$第三次分部积分
	对 $\int x e^{-x/\theta} dx$ 最后一次使用分部积分：$$\int x e^{-x/\theta} dx = -x \theta e^{-x/\theta} + \theta \int e^{-x/\theta} dx = -x \theta e^{-x/\theta} - \theta^2 e^{-x/\theta}$$
	代回得到：$$\int x^3 e^{-x/\theta} dx = e^{-x/\theta} \left[ -\theta x^3 - 3\theta^2 x^2 - 6\theta^3 x - 6\theta^4 \right]$$现在代入定积分的上下限 $[0, \infty)$：
	当 $x \to \infty$ 时，结果为 $0$。
	当 $x = 0$ 时，结果为 $1 \cdot (-6\theta^4) = -6\theta^4$。
- **定积分结果** = 上限 - 下限 = $0 - (-6\theta^4) = 6\theta^4$。
	最后前面还有一个系数 $\frac{1}{\theta^2}$：$$E(X^2) = \frac{1}{\theta^2} \cdot 6\theta^4 = 6\theta^2$$
$E(\hat{\theta})=E\left( \frac{1}{2n} \sum x_{i}\right)=\frac{1}{2n}E\left( \sum x_{i} \right)=\theta$
$E(\hat{\theta}^2)=E\left( \left( \frac{1}{2n}\sum x_{i} \right)^2 \right)=\frac{1}{4n^2}(6n\theta^2+n(n-1)4\theta^2)=\frac{3\theta^2}{2n}+\theta^2-\frac{\theta^2}{n}$
	注意：$$E[(\sum X_i)^2] = n E(X^2) + n(n-1) [E(X)]^2$$
所以$Var(\hat{\theta})=E(\hat{\theta}^2)-(E(\hat{\theta}))^2=\frac{3\theta^2}{2n}+\theta^2-\frac{\theta^2}{n}-\theta^2=\frac{\theta^2}{2n}$
所以$Var(\hat{\theta})=\frac{1}{I_{n}(x)}$
所以是有效估计。
	$Var(\hat{\theta})$的计算：$Var(\hat{\theta}) = \left(\frac{1}{2n}\right)^2 Var(\sum X_i) = \frac{1}{4n^2} \sum Var(X_i) = \frac{n Var(X)}{4n^2} = \frac{Var(X)}{4n}$
	$Var(X)=E(X^2)-(E(X))^2$


#### **练习二-第二大题**：
设 $x_1, \dots, x_n$ 是来自总体 $f(x; \theta) = \frac{1}{\theta}x^{-(1/\theta+1)}$ ($1 \leq x$) 的样本，其中 $\theta >0$。 (1) 在参数空间$P={\theta:  \theta \geq 3}$上求$\theta$的极大似然估计 $\hat{\theta}_{MLE}$； (2) 求 $\theta$ 的一致最小方差无偏估计 $\hat{\theta}_{UMVUE}$。
(1)
似然函数：$L(\theta)=\frac{1}{\theta^{n}}\cdot \prod x_{i}^{-(1/\theta+1)}$
对数似然函数：$\ln L(\theta)=-n\ln(\theta)-\left( \frac{1}{\theta}+1 \right)\sum\ln(x_{i})$
充分统计量$T=\sum \ln(x_{i})$
求导并令其为0：
$\frac{\partial \ln L(\theta)}{\partial \theta}=-\frac{n}{\theta}-\left( -\frac{1}{\theta^2} \right)\sum \ln(x_{i})=0$
则：
$$\hat{\theta}_{MLE} = \frac{1}{n}\sum \ln(x_{i})$$
如果$\frac{1}{n}\sum \ln(x_{i})\geq 3$，则$\hat{\theta}_{MLE}=\frac{1}{n}\sum \ln(x_{i})$,如果$\frac{1}{n}\sum \ln(x_{i})$小于3，那么$\hat{\theta}_{MLE}=3$
(2)
充分统计量$T=\sum \ln(x_{i})$
需找到$E(f(T))=\theta$
$E(T)=E\left( \sum \ln(x_{i}) \right)=\sum E(\ln(x_{i}))$
令$Y=\ln X$，因为$X\geq{1}$,所以$Y\geq{0}$。利用分布函数法：
$F_{Y}(y)=P(Y\leq y)=P(\ln X<y)=P(X\leq e^y)$
$$F_Y(y) = \frac{1}{\theta} \left[ -\theta x^{-1/\theta} \right]_1^{e^y} = \left[ -x^{-1/\theta} \right]_1^{e^y}=1-e^{y/\theta}$$
	ps:
	**从密度到分布**：通过**积分**得到。 $F_Y(y) = \int_{-\infty}^{y} f_Y(t) dt$
	**从分布到密度**：通过**求导**得到。 $f_Y(y) = \frac{d}{dy} F_Y(y)$
$Y=\ln X$服从指数分布$\exp(x,\theta)$
由指数分布的性质：$E(Y_{i})=\theta,Var(Y_{i})=\theta^2$得到：
$E(T)=E\left( \sum\ln x_{i} \right)=n\theta$
所以$\hat{\theta}_{UMVUE}=\frac{1}{n}\sum \ln(x_{i})$

#### **练习三·第二大题**
设总体 $X$ 的密度函数为 $f(x; \theta) = \frac{1}{2\theta}e^{-\frac{|x|}{\theta}}$，其中 $\theta > 0$。$x_1, x_2, \cdots, x_n$ 是来自总体 $X$ 的简单样本。
1. 在参数空间 $\Theta_0 = \{\theta : 0 < \theta \leq 2\}$ 上求 $\theta$ 的极大似然估计；
2. 求 $\theta$ 的一致最小方差无偏估计。

(1)
似然函数：$L(\theta)=\frac{1}{(2\theta)^n}e^{-\sum|x|/\theta}$
对数似然函数：$\ln L(\theta)=-n\ln(2\theta)-\frac{\sum|x_{i}|}{\theta}$
求导并令其为0：$\frac{\partial \ln L(\theta)}{\partial \theta}=-\frac{n}{\theta}+\frac{\sum|x_{i}|}{\theta^{2}}$
得到：$$\hat{\theta}_{MLE} = \min(2, \bar{A}) = \min\left(2, \frac{1}{n}\sum_{i=1}^n |X_i|\right)$$
(2)
充分统计量$T=\sum|x_{i}|$
$E(X_{i})=\int xf(x)dx=\int x\frac{1}{2\theta}e^{-\frac{|x|}{\theta}}dx=\frac{1}{2\theta}2\int_{0}^\infty xe^{-x/\theta}dx=\frac{1}{\theta}[x\cdot(-\theta e^{-x/\theta})-\theta^2e^{-x/\theta}]_{0}^\infty=-\frac{1}{\theta}(-\theta^2)=\theta$
所以$E(T)=n\theta$，$\hat{\theta}_{UMVUE}=\frac{1}{n}\sum|x_{i}|$



## 例2：均匀分布
**均匀分布的 UMVUE**：
设 $X_1, X_2, \dots, X_n$ 是来自**均匀分布 $U(0, \theta)$** 的简单随机样本，其中 $\theta > 0$ 是未知参数。请推导参数 $\theta$ 的 UMVUE。
答案：
**概率密度**：$$f(x) = \frac{1}{b-a}, a \le x \le b$$
步骤一：写出似然函数：
$L(\theta)=\prod\frac{1}{\theta}=\frac{1}{\theta^n},0<x_{1},\dots x_{n}<\theta$，等价于说样本中的最大值不能超过$\theta$
定义$T=max(x_{1},\dots x_{n})$为充分统计量。
步骤二：计算期望，验证无偏性。对于$U(0,\theta)$的最大值统计量，有一个常用结论：$E(T)=\frac{n}{n+1}\theta$，所以为了使$E(T)=\theta$，给$T$乘一个系数$\frac{n+1}{n}$
所以$E\left( \frac{n+1}{n} T\right)=\theta$
则均匀分布$U(0,\theta)$的UMVUE为$\frac{n+1}{n}X_{max}$

### **$U(a,b)$的UMVUE：**
有两个位置参数，a和b
绳子模型 🧶
想象有一根长度为 $L = b - a$ 的绳子。我们在上面随机切 $n$ 刀，这对应于我们取的 $n$ 个样本点。
这 $n$ 个点把绳子分成了 **$n+1$ 段**。在概率论中，对于均匀分布来说，这 $n+1$ 段距离的**期望长度是完全相等**的。
- 每段的平均长度 = $\frac{\text{总长度}}{\text{段数}} = \frac{b - a}{n + 1}$
#### 1. 最大值 $X_{(n)}$ 的位置
最大值 $X_{(n)}$ 是从右端点 $b$ 向左数的第一段。
所以它的位置预期在 $b$ 减去一段的平均长度：
$$E(X_{(n)}) = b - \frac{b - a}{n + 1}$$
#### 2. 最小值 $X_{(1)}$ 的位置
最小值 $X_{(1)}$ 是从左端点 $a$ 向右数的第一段。
所以它的位置预期在 $a$ 加上一段的平均长度：
$$E(X_{(1)}) = a + \frac{b - a}{n + 1}$$
#### 3.把这两个等式相加：
$E(X_{(n)}) +E(X_{(1)}) = E(X_{n}+X_{1})=b - \frac{b - a}{n + 1}+a + \frac{b - a}{n + 1}=b+a$
#### 4.消掉a
在 $U(a, b)$ 中，最大值和最小值之间隔了 $n-1$ 个间隙，所以：
$$E(X_{(n)} - X_{(1)}) = \frac{n-1}{n+1}(b - a)$$
尝试把两个等式相加：
$E(X_{n}+X_{1}) +E(X_{n} - X_{1})=E(2X_{n})=2nb+2a$
a不能被消掉
从右边入手发现，如果想让$\frac{n-1}{n+1}(b-a)+(a+b)=2b$，需要让左边(b-a)系数为1
所以令$\frac{n+1}{n-1}E(X_{n}+X_{1}）=\frac{n+1}{n-1} \cdot \frac{n-1}{n+1}(b-a)=b-a$
所以$E(X_{n}+X_{1})+\frac{n+1}{n-1}E(X_{n}+X_{1}）=\frac{2n}{n+1}E(X_{n}+X_{1})=2b$
**$U(a, b)$ 分布中参数 $b$ 的 UMVUE**：
$$\hat{b}_{UMVUE} = \frac{1}{2} \left[ (X_{(n)} + X_{(1)}) + \frac{n+1}{n-1}(X_{(n)} - X_{(1)}) \right]$$


### 复习题：

