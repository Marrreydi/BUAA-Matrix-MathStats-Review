
## 一、Jordan 标准形是什么

Jordan 标准形是把矩阵通过相似变换化成由 **Jordan 块** 组成的上三角矩阵：

$A \sim J$

其中每个 Jordan 块为：

$$J_k(\lambda)=
\begin{pmatrix}
\lambda & 1 & 0 & \cdots & 0 \\
0 & \lambda & 1 & \cdots & 0 \\
\vdots & & \ddots & \ddots & \vdots \\
0 & \cdots & 0 & \lambda & 1 \\
0 & \cdots & 0 & 0 & \lambda
\end{pmatrix}$$
## 二、整体思路（先记住这个）

> **Jordan 形由两件事决定：**
>
> 1. 特征值是多少
> 2. 每个特征值对应几个 Jordan 块、每个块多大


## 三、标准求解步骤（考试版）

### Step 1：求特征值

计算特征多项式：

$|A - \lambda I| = 0$

得到所有特征值 $\lambda_1,\lambda_2,\dots$

记录：

* **代数重数** $m_a(\lambda)$（根的重数）

### Step 2：求每个特征值的几何重数

对每个特征值 $\lambda$，求：

$\dim \ker(A - \lambda I)$

也就是解：

$(A - \lambda I)x = 0$

得到：

* **几何重数** $m_g(\lambda)$

### Step 3：判断是否可对角化

* 若对所有特征值都有
  $m_g(\lambda) = m_a(\lambda)$
  → $A$ 可对角化（Jordan 形就是对角阵）

* 若存在
  $m_g(\lambda) < m_a(\lambda)$
  → 需要 Jordan 块

### Step 4：确定 Jordan 块的个数

**结论：**

> Jordan 块的个数 = 几何重数

即：

* 对特征值 $\lambda$，有 $m_g(\lambda)$ 个 Jordan 块

### Step 5：确定 Jordan 块的大小（关键）(求秩序列)

对特征值 $\lambda$，计算：

$\dim \ker (A - \lambda I)^k,\quad k = 1,2,\dots$

直到维数不再增长。

记：

* $d_k = \dim \ker (A - \lambda I)^k$

则：

* 块大小 $\ge k$ 的 Jordan 块个数为
  $d_k - d_{k-1}$

其中规定：

* $d_0 = 0$

## 四、如何从 $d_k$ 读出 Jordan 块（口诀）

> **“一阶核给块数，二阶核给 ≥2 的块数，三阶核给 ≥3 的块数”**


## 五、典型例子（简版）

设某特征值 $\lambda$ 的代数重数为 4：

* $\dim \ker(A-\lambda I)=2$
* $\dim \ker(A-\lambda I)^2=3$
* $\dim \ker(A-\lambda I)^3=4$

则：

* Jordan 块个数：2
* 大小 ≥2 的块数：$3-2=1$
* 大小 ≥3 的块数：$4-3=1$

👉 Jordan 形为：

$J_3(\lambda)\oplus J_1(\lambda)$

---

## 六、考试中常见快判技巧

### 1️⃣ 快速判断是否存在 Jordan 块

* 若
  $\dim \ker(A-\lambda I)=1$ 且 $m_a(\lambda)>1$
  → 一定有 Jordan 块

---

### 2️⃣ 二阶矩阵常见结论

若 $A$ 为 $2\times2$ 矩阵：

* 特征值不同 → 可对角化
* 特征值相同：

  * 几何重数 2 → 可对角化
  * 几何重数 1 → 一个 $2\times2$ Jordan 块

---

## 七、常见易错点（必看）

* Jordan 块个数 ≠ 代数重数
* $\ker(A-\lambda I)$ 是解齐次方程，不是算行列式
* $(A-\lambda I)^k$ 一定要真的算，不要想当然

---

## 八、和考试题型的关系

* 出现：

  * “求 Jordan 形”
  * “判断是否可对角化”
  * “求 $A^n$”
* 几乎必然要用 Jordan 分解

