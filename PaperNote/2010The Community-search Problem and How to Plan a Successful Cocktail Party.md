
<h5>
    《The Community-search Problem and How to Plan a Successful Cocktail Party》
</h5> 
  
**Problem 1**:给出一个联通无向图，$G=(V,E)$，以及一系列的query点集$Q\subseteq V$，还有一个评估函数$f$，我们去找一个$G$的子图$H=(V_H,E_H)$，有如下
$(i)V_H$包含了$Q$;
$(ii)H$是联通的;
$(iii)H$是在所有可选的$H$中使得$f(H)$最大的。
关于$f(H)$可从边的角度考虑，但是从边考虑一个图的稀疏程度是一个$NP-hard$问题，考虑从子图中的节点平均度数或者最小度数来作为$f(H)$的度量；

**Problem 2**:在上述问题１的基础上再多加一条限制:
$(iv)D_Q(H)\leq d$
$(D_Q(G)=\mathop{max}\limits_{v\in V(G)} \left\{ D_Q(G,v)\right\}$,$D_Q(G,v)=\mathop{\sum}\limits_{q\in Q}d_G{(v,q)}^2)$；

**Problem 3**:对问题二关于约束函数做了一个泛化；

**Problem 4**:在问题２的基础上加一条对于集合大小的限制：
$(v)\left|V_H\right|\leq k$ (表示H最多包含k个结点)
$np-hard\ problem$

斯坦纳树(Steiner-tree):给出图$G$以及一个点集$T$，还有一个整数$k$，找出一个子树，包含$T$中所有结点且边数不超过$k$，而其实边不超过$k$这个问题其实就相当于限制条件为点不超过$k+1$。

$k-core$问题是$G$中的最大联通子图同时所有的节点的度都要大于等于$k$。

数据集：
DBLP 226K nodes 1.4M edges
BIOMINE 16K nodes 491K edges
tag 38K nodes 1.3M edges

EXPERIMENTS:Query无法保证是联通的，先跑一趟SteinerTree
Experimental framework:$q=\left|Q\right|$,$l$表示query nodes点之间的距离小于$l$(每个变量至少跑50词取平均)