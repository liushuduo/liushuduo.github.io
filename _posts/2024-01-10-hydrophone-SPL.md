---
layout:     post
title:      "声波声压级的计算"
subtitle:   "On calculation of sound level"
date:       2024-01-10 10:00:00
header-style: text
author:     "Shuduo"
mathjax:  true
tags:
  - 科研
  - 信号处理
  - 阵列信号处理
---

声波强度的计算根据不同的公式定义有着不同的计算方法，常用的计算方式包括**声压级（sound pressure level，SPL）**、**等效声级（equivalent continous sound pressure level）**、**声暴露级（sound exposure level，SEL）**、**声压峰级（peak level）**。

其中比较常用的量为SPL，其定义为：

$$
SPL=20\log(p/p_0)
$$

在实际应用中声压是随时间变化的量，等效声级描述声波在一定时间内的平均效果，因此更为常用，其计算公式为：

$$
L_{\rm eq} = 10 \log \left(\frac{1}{T}\int_0^T\frac{p^2(t)}{p_0^2}\right)
$$

其中 $p(t)$ 代表时间，$p_0$ 代表参考声压（在水声学中常以 $1~\mu Pa$ 为参考声压），$T$ 代表了计算等效声压的平均时间。

水听器将声波带来的压强变化以电压 $v(t)$ 的形式记录下来，通过电压计算声压需要得知水听器的基本参数**灵敏度**，其定义为水听器输出端开路电压 $U$ 和输入端自由场声压 $p$ 的比值：

$$
M=U/p
$$

其单位为 $V/Pa$ 。由上式定义可知，水听器的灵敏度是刻画其感知声压变化的能力。一般而言，灵敏度也是以分贝形式来表征的，即将上面计算得到的灵敏度值比上一个基准值，取对数，再乘以 $20$ 得到：

$$
HM=20\log(M/M_0)
$$

其中 $M_0$ 为参考灵敏度，按照惯例一般取 $M_0 =1~V/\mu Pa$。因此灵敏度的单位记作 $dB\ \text{ref}\ 1~V/\mu Pa$ 。

因此水听器记录的电压变化与对应的声压变化有以下关系：

$$
p(t)=\frac{v(t)}{M}=\frac{v(t)}{M_0\cdot 10^{HM/20}}
$$

将上式代入到等效声级的计算公式中得到

$$
\begin{aligned}
L_{\rm eq} &=10\log\left(\frac{1}{T}\int_0^T\frac{v^2(t)}{p_0^2M_0^210^{HM/10}}\right)\\
&=10\log\left(\frac{1}{T}\int_0^Tv^2(t)\right)-HM
\end{aligned}
$$

即声压级可以通过计算某段时间内的电压等效功率级，再减去水听器的灵敏度得到。
