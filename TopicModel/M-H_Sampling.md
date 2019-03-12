<h1>
    M-H采样(Metropolis-Hastings)
</h1>

>Written by KaelThas_Infi

**M-H采样**解决了MCMC接受率过低的问题，回到MCMC采样的细致平稳条件:
$$\pi(i)Q(i,j)\alpha(i,j)=\pi(j)Q(j,i)\alpha(j,i)$$
效率低的原因是$\alpha(i,j)$太小，比如0.1，而$\alpha(j,i)$为0.2
$$\Rightarrow\pi(i)Q(i,j)*0.1=\pi(j)Q(j,i)*0.2$$
这时我们可以看到，如果两边同时扩大5倍，接受率提高到了0.5.
$$\Rightarrow\pi(i)Q(i,j)*0.5=\pi(j)Q(j,i)*1.0$$
这样我们的接受率可以做出如下改进，即:
$$\alpha(i,j)=min\lbrace\frac{\pi(j)Q(j,i)}{\pi(i)Q(i,j)},1\rbrace$$
通过这个微小的改造，我们就得到了可以在实际应用中使用的**M-H采样算法**：
$1)$输入$Q$，平稳分布$\pi(x)$，设定状态阈值$n_1$，需要样本个数$n_2$
$2)$从任意简单概率分布采样得到初始状态值$x_0$
$3)for\quad t=0\quad to \quad n_1+n_2-1$
$\quad a)$从条件概率分布$Q(x|x_t)$中采样得到样本$x_*$
$\quad b)$从均匀分布采样$u$~$uniform[0,1]$
$\quad c)$如果$u<\alpha(x_t,x_*)=min\lbrace\frac{\pi(j)Q(j,i)}{\pi(i)Q(i,j)},1\rbrace$则接受转移$x_t\rightarrow x_*$即$x_{t+1}=x_*$
$\quad d)$否则不接受转移$x_{t+1}=x_t$
样本集$(x_{n_1},x_{n_1+1},……x_{n_1+n_2-1})$即我们需要的平稳分布对应的样本集。
若我们选择的$Q$是对称的，可以进一步简化：
$$\alpha(i,j)=min\lbrace\frac{\pi(j)}{\pi(i)},1\rbrace$$
**M-H采样问题：**
$1)$当数据特征非常多时，由于$\frac{\pi(j)Q(j,i)}{\pi(i)Q(i,j)}$高维计算时算法效率低，同时$\alpha(i,j)$低于1，容易被拒绝，计算损失大。
$2)$由于特征维度大，很多时候我们甚至很难求出目标的各特征维度联合分布，但是可以方便求出各个特征之间的条件概率分布，可以尝试通过条件概率分布来方便采样。