| Sampler Method| ON LDA | Maybe on DMM |
| ------ | ------ | ------ |
| SparseLDA-Gibbs优化 | 利用$n_m^k \And n_k^t$的稀疏性质 将Gibbs采样式子拆解为$\\p(z_{di}=k\mid rest)\varpropto s+r+q \\ s=\frac{\alpha_k\beta_w}{n_k^{-di}+\vec{\beta}} \ \ r=\frac{n_{kd}^{-di}\beta_w}{n_k^{-di}+\vec{\beta}} \ \ q=\frac{n_{kw}^{-di}(n_{kd}^{-di}+\alpha_k)}{n_k^{-di}+\vec{\beta}}\\sampleX\sim\mu(0,s+r+q)\\if \ \ x<s \ \ hit \ \ the  \ \ smoothing \ \ only \ \ bucket\\if \ \ s<x<s+r \ \ hit \ \ the  \ \ document \ \ topic \ \ bucket\\if \ \ x>s+r \ \ hit \ \ the  \ \ topic \ \ word \ \ bucket$|  |
| Alias-Method-LDA | 将Gibbs采样式子分解为$u\ \ v$ $\\u$项为稀疏项$v$近似项 建立一个Alias Table采样复杂度$O(1)\\p(z_{di}=k\mid rest)\varpropto u+v\\u=\frac{n_{kd}^{-di}(n_{kw}^{-di}+\beta_w)}{n_k^{-di}+\vec{\beta}}\ \ v=\frac{\alpha_k(n_{kw}^{-di}+\beta_w)}{n_k^{-di}+\vec{\beta}}$|  | 
| F+LDA |用FenwickTree数据结构采样 $\\p_t=\frac{(n_{td}+\alpha)(n_{tw}+\beta)}{n_t+\vec{\beta}}\\doc-by-doc:p_t=\beta(\frac{n_{td}+\alpha}{n_t+\vec{\beta}})+n_{tw}(\frac{n_{td}+\alpha}{n_t+\vec{\beta}})\\word-by-word:p_t=\alpha(\frac{n_{tw}+\beta}{n_t+\vec{\beta}})+n_{td}(\frac{n_{tw}+\beta}{n_t+\vec{\beta}})$|  |
| WarpLDA |设置$D*V$矩阵 MCEM Algorithm(MC+EM)$\\$E-step:Sample $z_{dn}\sim q(z_{dn}=k)$,where$\\q(z_{dn}=k)\varpropto(C_{dk}+\alpha_k)\frac{C_{wk}+\beta_w}{C_k+\vec{\beta}}\\$M-step:Compute $C_d\And C_w$ by $Z\\q^{doc}(z_{dn}=k)\varpropto C_{dk}+\alpha_k\\q^{word}(z_{dn}=k)\varpropto C_{wk}+\beta\\$用上面两个作为proposal distributions用MH算法交替采样|  |
| LightLDA |MH+Alias Table(doc-proposal+word proposal)构建一系列$proposal\ \ function$轮流使用 $\\q(z_{di}=k\mid rest)\varpropto(n_{kd}+\alpha_k)\times\frac{n_{kw}+\beta_w}{n_k+\vec{\beta}}\\ n_{kd}+\alpha_k为doc-proposal\\ \frac{n_{kw}+\beta_w}{n_k+\vec{\beta}}为word-proposal$ | |
| LDA* |$long-documents:WarpLDA\\ short-documents:F+LDA$ | |


| Basic Sampler ||
| ------ |------|
| Importance Sampling |
| Elliptical Slice Sampling |
| Variational Inference |
| Metropolis-Hasting |
| Gibbs| $p(z_i=k\mid \vec{Z}_{\urcorner i},\vec{W} )$ |