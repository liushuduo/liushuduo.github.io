---
layout:     post
title:      "主动声学系统中时延估计的CRB"
subtitle:   "CRB for time delay estimation in active acoustic systems"
date:       2024-02-13 22:00:00
header-style: text
author:     "Shuduo"
mathjax:  true
tags:
  - 科研
  - 信号处理
---

在声学领域，通过主动发射声信号来获取目标信息的方法成为主动声学方法。其中一个常见的应用是定位目标的距离，此时在声速已知的条件下可以通过估计声信号的**传播时间**来确定目标的距离。传播时间作为一个估计量，确定其估计的准确度是非常重要的。CRB给出了所有无偏估计量的方差下界，也就是一个估计量能给出的最好结果。主动声学系统中时延 $\tau$ 的CRB由以下公式给出：
$$
\sigma_\tau^2\geq \frac{1}{d^2\beta^2}\tag{1}
$$
其中 $d^2=2E/N_\text{0}$ ，$E$ 代表了**已知确定信号** $s(t)$ 的能量，$N_\text{0}$ 是白噪声功率。$\beta^2$ 代表了信号带宽的某种度量，由以下公式给出：
$$
\beta^2 = \frac{\int_{-\infty}^{\infty}\omega^2|F(\omega)|^2d\omega}{\int_{-\infty}^{\infty}|F(\omega)|^2d\omega}\tag{2}
$$
其中 $F(\omega)$ 是发射信号 $s(t)$ 的频谱。从以上公式可以基本看出，主动声学系统中的时延估计的精确度与信号的能量、频率、带宽有关，这三者的数值越大，能量估计的方差越小。

为了得出进一步结论，我们假设 $s(t)$ 的功率谱在 $f_1$ 和 $f_2$ 之间均匀分布（假设为双边谱），其谱密度为 $S_0/2$ ，带入公式 $(2)$ 可以得到

$$
\begin{aligned}
\beta^2 & =\frac{2 \int_{f_1}^{f_2}(2 \pi f)^2 S_0 / 2\cdot2 \pi d f}{2 \int_{f_1}^{f_2} S_0 / 2\cdot2 \pi d f} \\
& =(2 \pi)^2\left(f_2^2+f_1 f_2+f_1^2\right) / 3
\end{aligned}
$$
进一步带入公式 $(1)$ 可得时延估计的下限为：
$$
\begin{aligned}
\sigma_D^2 & \geqslant \frac{1}{\frac{2 E}{N_0} \frac{4 \pi^2}{3}\left(f_2^2+f_1 f_2+f_1^2\right)} \\
& =\frac{1}{\frac{2 S T}{N_0\left(f_2-f_1\right)} \frac{4 \pi^2}{3}\left(f_2-f_1\right)\left(f_2^2+f_1 f_2+f_1^2\right)} \\
& =\frac{3}{8 \pi^2 T} \frac{1}{\operatorname{SNR}} \frac{1}{\left(f_2^3-f_1^3\right)}
\end{aligned}
$$
其中 $S = S_0(f_2 - f_1)$ 代表信号功率，$N=N_0(f_2 - f_1)$ 代表噪声功率，$T$ 代表信号的观测时间，$SNR$ 为信号的信噪比。用信号的中心频率 $f_0$ 和信号的带宽 $W$ 来表示时延估计的标准差有
$$
\sigma_D\geq\left(\frac{1}{8 \pi^2}\right)^{1 / 2} \frac{1}{\sqrt{\mathrm{SNR}}} \frac{1}{\sqrt{T W}} \frac{1}{f_0} \frac{1}{\sqrt{1+W^2 / 12 f_0^2}}
$$
由此可以看出，时延估计的精确度与以下三个因素有关：
1. 信号的信噪比，信噪比越高，估计的精度越高；
2. 信号的时间带宽积，时间带宽积越大，估计精度越高；
3. 信号的中心频率，以及中心频率与带宽的乘积，中心频率越高，估计精度越高。