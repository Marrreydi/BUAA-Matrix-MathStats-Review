---
tags:
  - 等离子体物理
  - 单粒子运动
  - 推导
---
#### 泰勒展开
在引导中心(GC)处对电场进行泰勒展开：
$$\mathbf{E}(\mathbf{r})=\mathbf{E}_0+(\mathbf{r}\cdot\nabla)\mathbf{E}+\frac{1}{2!}(\mathbf{r}\cdot\nabla)^2\mathbf{E}+\cdots$$
**展开项详细写为：**
$$\mathbf{E}(\mathbf{r})=\mathbf{E}_0+(x\frac{\partial}{\partial x}+y\frac{\partial}{\partial y})\mathbf{E}+\left(\frac{x^2}{2!}\frac{\partial^2}{\partial x^2}+\frac{y^2}{2!}\frac{\partial^2}{\partial y^2}\right)\mathbf{E}+\text{cross terms}$$
交叉项示例：$xy\frac{\partial^2}{\partial x\partial y}\mathbf{E}$

### 回旋轨道平均

**粒子轨道参数：**
$$\mathbf{r}=r_L(\cos\theta,\sin\theta,0)$$
$$\theta=\Omega t$$

**计算各阶矩：**
-$\langle x\rangle=\langle r_L\cos\theta\rangle=0$
-$\langle y\rangle=\langle r_L\sin\theta\rangle=0$
-$\langle x^2\rangle=\langle r_L^2\cos^2\theta\rangle=\frac{r_L^2}{2}$
-$\langle y^2\rangle=\langle r_L^2\sin^2\theta\rangle=\frac{r_L^2}{2}$
-$\langle xy\rangle=\langle r_L^2\cos\theta\sin\theta\rangle=0$
**交叉项平均为零**
#### 平均电场结果
**各项平均：**
-零阶项：$\langle\mathbf{E}_0\rangle=\mathbf{E}_0$
-一阶项：$\langle(\mathbf{r}\cdot\nabla)\mathbf{E}\rangle=0$
-二阶项：$\langle\frac{1}{2}(\mathbf{r}\cdot\nabla)^2\mathbf{E}\rangle\approx\frac{r_L^2}{4}\nabla^2\mathbf{E}$
**最终平均电场：**
$$\langle\mathbf{E}(\mathbf{r})\rangle\simeq\mathbf{E}_0+\frac{r_L^2}{4}\nabla^2\mathbf{E}$$
### 有限拉莫尔半径修正的E×B漂移

代入漂移速度公式：

$$\mathbf{v}_{E\times B}=\frac{\langle\mathbf{E}(\mathbf{r})\rangle\times\mathbf{B}}{B^2}=\left(1+\frac{r_L^2}{4}\nabla^2\right)\frac{\mathbf{E}\times\mathbf{B}}{B^2}$$

**修正后的漂移速度：**
$$\mathbf{v}_{E\times B}=\left(1+\frac{r_L^2}{4}\nabla^2\right)\frac{\mathbf{E}\times\mathbf{B}}{B^2}$$
