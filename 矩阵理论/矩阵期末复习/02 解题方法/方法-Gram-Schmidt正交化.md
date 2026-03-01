
### 🌟 核心公式（三步走策略）

假设我们有一组线性无关的向量 $\{\alpha_1, \alpha_2, \dots, \alpha_n\}$，我们要得到正交基 $\{\beta_1, \beta_2, \dots, \beta_n\}$：
1. 第一步（定基准）： 直接取第一个向量。
    $$\beta_1 = \alpha_1$$
2. 第二步（减投影）： 第二个向量减去它在 $\beta_1$ 上的分量。
    $$\beta_2 = \alpha_2 - \frac{(\alpha_2, \beta_1)}{(\beta_1, \beta_1)} \beta_1$$
3. 第三步（通项公式）： 第 $k$ 个向量减去它在之前所有 $\beta_j$ 上的分量。
    $$\beta_k = \alpha_k - \sum_{j=1}^{k-1} \frac{(\alpha_k, \beta_j)}{(\beta_j, \beta_j)} \beta_j$$