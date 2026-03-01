---
tags:
  - 矩阵
  - 分解
---

对 $A$ 的列 $a_1, \dots, a_n$ 逐列正交化：
1. 令 $u_1 = a_1$，$q_1 = u_1 / |u_1|$
2. 对 $k = 2, \dots, n$：
    - $u_k = a_k - \sum_{j=1}^{k-1} \langle q_j, a_k \rangle q_j$
    - $q_k = u_k / |u_k|$
得到的 $Q = [q_1, \dots, q_n]$，$R$ 的元素 $r_{jk} = \langle q_j, a_k \rangle$（$j < k$）$=q_{j}^Ta_{k}$，$r_{kk} = |u_k|$。

### 例子
设

$A = \begin{bmatrix} 1 & 1 \\ 1 & 0 \\ 0 & 1 \end{bmatrix}$

Gram–Schmidt 过程：

1. $u_1 = \begin{bmatrix} 1 \ 1 \ 0 \end{bmatrix}$，$|u_1| = \sqrt{2}$，$q_1 = \frac{1}{\sqrt{2}} \begin{bmatrix} 1 \ 1 \ 0 \end{bmatrix}$
2. $r_{12} = q_1^T a_2 = \frac{1}{\sqrt{2}}$  
    $u_2 = \begin{bmatrix} 1 \ 0 \ 1 \end{bmatrix} - \frac12 \begin{bmatrix} 1 \ 1 \ 0 \end{bmatrix} = \begin{bmatrix} \frac12 \ -\frac12 \ 1 \end{bmatrix}$  
    $|u_2| = \sqrt{3/2}$  
    $q_2 = \sqrt{\frac{2}{3}} \begin{bmatrix} \frac12 \ -\frac12 \ 1 \end{bmatrix} = \begin{bmatrix} \frac{1}{\sqrt{6}} \ -\frac{1}{\sqrt{6}} \ \sqrt{\frac{2}{3}} \end{bmatrix}$

于是

$Q = \begin{bmatrix} \frac{1}{\sqrt{2}} & \frac{1}{\sqrt{6}} \\ \frac{1}{\sqrt{2}} & -\frac{1}{\sqrt{6}} \\ 0 & \sqrt{\frac{2}{3}} \end{bmatrix}$  
$R = \begin{bmatrix} \sqrt{2} & \frac{1}{\sqrt{2}} \\ 0 & \sqrt{\frac{3}{2}} \end{bmatrix}$

验证：$A = QR$。