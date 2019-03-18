| Sampler | ON LDA | Maybe on DMM |
| ------ | ------ | ------ |
| Gibbs| $p(z_i=k\mid \vec{Z}_{\urcorner i},\vec{W} )$ | | 中等文本 |
| SparseLDA-Gibbs优化 | 利用$n_m^k \And n_k^t$的稀疏性质 将Gibbs采样式子拆解为$r\ \ s \ \ t$|  |
| Alias-Method | 将Gibbs采样式子分解为$u\ \ v$|  | 
| Elliptical Slice Sampling | |  |
| Adapation Rejection Sampling($log(p(x))$是凸函数) | |  |
| Importance Sampling | |  |
| Variational Inference | |  |
| Hybrid M-H | |  |