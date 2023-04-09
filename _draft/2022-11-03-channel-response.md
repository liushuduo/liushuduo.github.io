# 理解时变信道的单位冲激响应
在读Goldsmith的Digital communications和Tse的Fundamental of Wireless Communication时，我对时变信道（LTV）的冲击响应$c(t,\tau)$的定义感到非常困惑，准确的说是对函数自变量$t$和$\tau$的定义非常困惑。按照我的理解，$t$应当是LTV信道的geo-time，$\tau$是冲激响应的时延，比如某个LTV信道在$t$时刻有三条多径，分别是在冲击响应发出后$\tau=1$，$\tau=2$，$\tau=4$时刻到达接收端，那么
在Goldsmith的书中对这两个变量的定义如下：

>Note that $c(\tau, t)$ has two time parameters: the time $t$, when the impulse response is observed at the receiver; and the time $t − \tau$, when the impulse is launched into the channel relative to the observation time $t$. 


## 重新理解LTI信道的单位冲激响应
系统的输出$y(t)$等于系统输入$x(t)$与系统的单位冲激响应$h(t)$的卷积，这个结论对于每一个学过信号与系统的人来说都再熟悉不过了。我每天都在使用着这个公式，它对我过于熟悉以至于我从来没有想过里面的细节，也没有再去深入思考里面的intuition。

任何一个输入信号都可以表示为如下积分形式
$$\begin{equation}
\label{xtdecompose}
x(t) = \int_{-\infty}^{+\infty}x(t')\delta(t-t')\text{d}t'
\end{equation}$$
上式可以理解为把$x(t)$分解成无数个脉冲$\delta(t-\tau)$的加权组合，其权重就是在$\tau$处$x(t)$的取值。
我们可以使用线性算子$\mathbf{H}\{\cdot\}$来表示一个线性系统，此时有
$$\begin{equation}
y(t)=\mathbf{H}x(t)
\end{equation}$$
对于线性时不变系统还有
$$\begin{equation}
y(t-t')=\mathbf{H}x(t-t')
\end{equation}$$
对公式\eqref{xtdecompose}两侧同时应用信道算子$\mathbf{H}$得到
$$\begin{equation}
\mathbf{H}x(t)=\mathbf{H}\int_{-\infty}^{+\infty}x(\tau)\delta(t-t')\text{d}t'=\int_{-\infty}^{+\infty}\mathbf{H}x(\tau)\mathbf{H}\delta(t-t')\text{d}t',
\end{equation}$$
where the second equation establishes in that integral is also linear. 
$$\begin{equation}
y(t) = \int_{-\infty}^{+\infty}x(\tau)h(t-\tau)\text{d}\tau,
\end{equation}$$
which is exactly the convolution of $x(t)$ and $h(t)$. 
对于在$t'$时刻的脉冲$\delta(t-t')$，实际上有两个时间维度需要考虑，现在定义系统对于在$t'$时刻的冲激响应为$h(t, t')$
