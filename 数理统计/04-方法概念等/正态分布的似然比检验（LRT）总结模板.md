

以下总结正态分布在不同参数已知/未知情形下，
常见单侧假设的 **似然比检验的拒绝域、势函数及无偏性判断**。

---
## 一、$\mu$ 已知，$\sigma^2$ 未知（方差检验）

设 $X_1,\dots,X_n \sim N(\mu_0,\sigma^2)$，$\mu_0$ 已知。

记统计量  
$Q=\dfrac{\sum_{i=1}^n (X_i-\mu_0)^2}{\sigma_0^2}$，  
在 $\sigma^2=\sigma_0^2$ 下有 $Q\sim\chi^2(n)$。

---

### 1️⃣ 左侧检验（小方差）

$H_0:\sigma^2\ge\sigma_0^2,\quad H_1:\sigma^2<\sigma_0^2$

**拒绝域**
$Q\le \chi^2_{\alpha}(n)$

**势函数**
$$g(\sigma^2)=
F_{\chi^2(n)}\!\left(
\dfrac{\sigma_0^2}{\sigma^2}\chi^2_{\alpha}(n)
\right)$$

**无偏检验判断**
- 当 $\sigma^2\in H_0$（$\sigma^2\ge\sigma_0^2$）：
  $g(\sigma^2)\le g(\sigma_0^2)=\alpha$
- 当 $\sigma^2\in H_1$（$\sigma^2<\sigma_0^2$）：
  $g(\sigma^2)\ge g(\sigma_0^2)=\alpha$

**结论：无偏检验**

---

### 2️⃣ 右侧检验（大方差）

$H_0:\sigma^2\le\sigma_0^2,\quad H_1:\sigma^2>\sigma_0^2$

**拒绝域**
$Q\ge \chi^2_{1-\alpha}(n)$

**势函数**
$$g(\sigma^2)=
1-
F_{\chi^2(n)}\!\left(
\dfrac{\sigma_0^2}{\sigma^2}\chi^2_{1-\alpha}(n)
\right)$$

**无偏检验判断**
- 当 $\sigma^2\in H_0$（$\sigma^2\le\sigma_0^2$）：
  $g(\sigma^2)\le g(\sigma_0^2)=\alpha$
- 当 $\sigma^2\in H_1$（$\sigma^2>\sigma_0^2$）：
  $g(\sigma^2)\ge g(\sigma_0^2)=\alpha$

**结论：无偏检验**

---

## 二、$\mu$ 未知，$\sigma^2$ 未知（方差检验）

设 $X_1,\dots,X_n \sim N(\mu,\sigma^2)$，$\mu$ 未知。

记样本方差  
$s^2=\dfrac{1}{n-1}\sum_{i=1}^n (X_i-\bar X)^2$，

统计量  
$Q=\dfrac{(n-1)s^2}{\sigma_0^2}$，  
在 $\sigma^2=\sigma_0^2$ 下有 $Q\sim\chi^2(n-1)$。

---

### 3️⃣ 左侧检验

$H_0:\sigma^2\ge\sigma_0^2,\quad H_1:\sigma^2<\sigma_0^2$

**拒绝域**
$Q\le \chi^2_{\alpha}(n-1)$

**势函数**
$$g(\sigma^2)=
F_{\chi^2(n-1)}\!\left(
\dfrac{\sigma_0^2}{\sigma^2}\chi^2_{\alpha}(n-1)
\right)$$

**无偏检验判断**
- 当 $\sigma^2\in H_0$：
  $g(\sigma^2)\le g(\sigma_0^2)=\alpha$
- 当 $\sigma^2\in H_1$：
  $g(\sigma^2)\ge g(\sigma_0^2)=\alpha$

**结论：无偏检验**

---

### 4️⃣ 右侧检验

$H_0:\sigma^2\le\sigma_0^2,\quad H_1:\sigma^2>\sigma_0^2$

**拒绝域**
$Q\ge \chi^2_{1-\alpha}(n-1)$

**势函数**
$$g(\sigma^2)=
1-
F_{\chi^2(n-1)}\!\left(
\dfrac{\sigma_0^2}{\sigma^2}\chi^2_{1-\alpha}(n-1)
\right)$$

**无偏检验判断**
- 当 $\sigma^2\in H_0$：
  $g(\sigma^2)\le g(\sigma_0^2)=\alpha$
- 当 $\sigma^2\in H_1$：
  $g(\sigma^2)\ge g(\sigma_0^2)=\alpha$

**结论：无偏检验**

---

## 三、$\sigma^2$ 已知，$\mu$ 未知（均值检验）

设 $X_1,\dots,X_n \sim N(\mu,\sigma^2)$，$\sigma^2$ 已知。

记统计量  
$Z=\dfrac{\bar X-\mu_0}{\sigma/\sqrt n}$，  
在 $\mu=\mu_0$ 下有 $Z\sim N(0,1)$。

---

### 5️⃣ 右侧检验

$H_0:\mu\le\mu_0,\quad H_1:\mu>\mu_0$

**拒绝域**
$Z\ge z_{1-\alpha}$

**势函数**
$$g(\mu)=
1-
\Phi\!\left(
z_{1-\alpha}-\dfrac{\sqrt n(\mu-\mu_0)}{\sigma}
\right)$$

**无偏检验判断**
- 当 $\mu\in H_0$：
  $g(\mu)\le g(\mu_0)=\alpha$
- 当 $\mu\in H_1$：
  $g(\mu)\ge g(\mu_0)=\alpha$

**结论：无偏检验**

---

### 6️⃣ 左侧检验

$H_0:\mu\ge\mu_0,\quad H_1:\mu<\mu_0$

**拒绝域**
$Z\le z_{\alpha}$

**势函数**
$$g(\mu)=
\Phi\!\left(
z_{\alpha}-\dfrac{\sqrt n(\mu-\mu_0)}{\sigma}
\right)$$

**无偏检验判断**
- 当 $\mu\in H_0$：
  $g(\mu)\le g(\mu_0)=\alpha$
- 当 $\mu\in H_1$：
  $g(\mu)\ge g(\mu_0)=\alpha$

**结论：无偏检验**
