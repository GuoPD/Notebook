## 算法原理
&emsp;&emsp;FOBOS (Forward-Backward Splitting)模型是由John Duchi和Yoram Singer提出的。在算法中，权重更新分为两步：

$$W^{(t+\frac{1}{2})} = W^{(t)}-\eta^{(t)}G^{(t)}$$

$$W^{(t+1)}=arg\ \mathop{min}_{W}\{\frac{1}{2}||W-W^{(t+\frac{1}{2})}||^2+\eta^{(t+\frac{1}{2})}\Psi(W)\}$$

&emsp;&emsp;第一步为标注梯度下降，第二步为梯度调整。第二步也可以分为两部分，第一部分使得产生的解在第一步梯度下降的解附近，第二部分则是正则项，使得解产生稀疏性。

将$W^{(t+\frac{1}{2})}$代入到第二步中，可以得到

$$W^{(t+1)}=arg\ \mathop{min}_{W}\{\frac{1}{2}||W-W^{(t)}+\eta^{(t)}G^{(t)}||^2+\eta^{(t+\frac{1}{2})}\Psi(W)\}$$

&emsp;&emsp;令$F(W)$为$W^{(t+1)}$关于$W^{(t)}$的函数，若W^{(t+1)}存在最优解，则可以确认0在$F(W)$的次梯度集合中

$$0\in\partial F(W)=W-W^{(t)}+\eta^{(t)}G^{(t)}+\eta^{(t+\frac{1}{2})}\partial\Psi(W)$$

&emsp;&emsp;若存在最优解，则最优解处，导数$\partial{F(W)}$为0，则可以得出$W^{(t+1)}$的最优解为：

$$W^{(t+1)}=W^{(t)}-\eta^{(t)}G^{(t)}-\eta^{(t+\frac{1}{2})}\partial\Psi(W^{(t+1)})$$

&emsp;&emsp;因此，由公式可以看出，$W^{(t+1)}$的取值不仅与迭代前的$W^{(t)}$有关，也与迭代后的$\Psi(W^{(t+1)})$有关，这也就是FOBOS中前向与后向名称的由来。


----------

## FOBOS的L1正则化

&emsp;&emsp;令正则项$\Psi(W)=\lambda||W||_1$，用向量$V=\{v_1,v_2...v_N\}$表示经过梯度下降的$W^{(t+\frac{1}{2})}$，令$\tilde{\lambda}=\eta^{(t+\frac{1}{2})}\lambda$，代入将公式展开，便可以得到：

$$W^{(t+1)}=arg\ \mathop{min}_{W}\sum_{i=1}^{N}\{\frac{1}{2}(w_i-v_i)^2+\tilde{\lambda}|w_i|\}$$

&emsp;&emsp;由于公式中的每一项均大于0，所以可以对每一维度进行单独优化，可以得到

$$w_i^{(t+1)}=arg\ \mathop{min}_{W}\{\frac{1}{2}(w_i-v_i)^2+\tilde{\lambda}|w_i|\}$$

&emsp;&emsp;假设$w^*$是其最优解，则存在$w^*v_i\geq0$，

&emsp;&emsp;其证明过程如下，若$w^*v_i<0$，则存在

$$\frac{1}{2}(w_i^*-v_i)^2+\tilde{\lambda}|w_i^*|>\frac{1}{2}(w_i^*)^2+\frac{1}{2}v_i^2-w_i^*v_i>\frac{1}{2}v_i^2$$

&emsp;&emsp;与当前最优解矛盾，所以，假设不成立，$w^*v_i\geq0$成立。
