---
title: "PID控制器"
date: 2025-06-25T18:36:51.724Z
math: true
---

$$
 \begin{aligned}G_c(s)&=K_P+\frac{K_I}s+K_Ds=\frac{K_I\left(\frac{K_D}{K_I}s^2+\frac{K_P}{K_I}s+1\right)}{s}\\&=\frac{K_I\left(\tau s+1\right)\left(\frac\tau\alpha s+1\right)}{s}\end{aligned}
$$

可调参数可选 $K_P, K_I, K_D,$ 或者 $K_I,\tau,\alpha$

$K_P,K_I, K_D$ 分别为比例、积分、微分控制参数

## ZN 整定

### 临界比例带法Ziegler-Nichols tuning method

可获得良好的干扰抑制，但未必获得良好的设定值响应性能

闭环控制下，令 $K_I{=}0,\quad K_D{=}0$，将 $K_P$ 从小开始往上调，直到在阶跃输入下达到临界稳定，产生幅值和周期不变的持续震荡，记录比例增益 $K_U$ 为临界增益，$T_U$ 为临界振荡周期

按以下整定规则配制

| 控制器类型| $K_P$ | $K_I$| $K_D$|
| ---------------- | ----------- | -------------------------- | -------------------------- |
| **比例控制 P** | $0.5K_{U}$| -| -|
| **比例积分控制 PI**| $0.45K_{U}$ | $\dfrac{0.54K_{U}}{T_{U}}$ | -|
| **比例微分控制 PD**| $0.8K_{U}$| -| $0.1K_{U}T_{U}$|
| **比例积分微分控制 PID** | $0.6K_{U}$| $\dfrac{1.2K_{U}}{T_{U}}$| $0.6\dfrac{K_{U}T_{U}}{8}$ |

与控制器的公式相像，比例是乘常数，积分是两者除，微分是两者乘

### 开环Ziegler-Nichols整定规则

| 控制器类型 | $K_P$| $K_I$ | $K_D$|
| ----------- | ------------------------ | --------------------------- | ---------------- |
| 比例控制P | $\dfrac{1}{R\Delta T}$ | - | -|
| 比例积分控制PI| $\dfrac{0.9}{R\Delta T}$ | $\dfrac{0.27}{R\Delta T^2}$ | -|
| 比例积分微分控制PID | $\dfrac{1.2}{R\Delta T}$ | $\dfrac{0.6}{R\Delta T^2}$| $\dfrac{0.6}{R}$ |

使用条件，输出信号如下图所示：$R$ 为斜率，$\Delta T$ 是纯滞后时间

![|281](https://image.huarenjian.cn/image/20250625231512805.png)

近似模型

$$
 G\big(s\big)=M\bigg[\frac{p}{s+p}\bigg]e^{-\Delta Ts}
$$

## λ整定

### 记忆

| 被控对象 | $K_P$| $K_I$| $K_D$|
| -------------------------------- | ---------------------------- | ---------------------------- | ---------------------------- |
| $\dfrac{K}{Ts+1} e^{-\tau s}$| $\dfrac{T}{K(\lambda+\tau)}$ | $\dfrac{1}{K(\lambda+\tau)}$ | -|
| $\dfrac{K}{s} e^{-\tau s}$ | $\dfrac{1}{K(\lambda+\tau)}$ | -| -|
| $\dfrac{K}{s(Ts+1)} e^{-\tau s}$ | $\dfrac{1}{K(\lambda+\tau)}$ | -| $\dfrac{T}{K(\lambda+\tau)}$ |

根据闭环系统过渡过程时间 $T_s$ 的要求，选择λ，满足

$$
 T_s{=}\tau{+}4\lambda 
$$

### 原理

期望传递函数具有以下形式

$$
 T\left(s\right)=\frac{1}{\lambda s+1}e^{-\tau s}
$$

λ为设定的期望闭环系统时间常数，τ为纯滞后

考虑闭环系统传递函数：

$$
 T\left(s\right)=\frac{Y\left(s\right)}{R\left(s\right)}=\frac{G_{c}\left(s\right)G\left(s\right)}{1+G_{c}\left(s\right)G\left(s\right)}=\frac{1}{\lambda s+1}e^{-\tau s}
$$

简单变换后得到：

$$
 G_c\left(s\right)=\frac1{G\left(s\right)}\frac{T\left(s\right)}{1-T\left(s\right)}=\frac1{G\left(s\right)}\frac{e^{-\tau s}}{\lambda s+1-e^{-\tau s}}
$$

再对 $G_c (s)$ 进行运算（需要用到泰勒展开近似，此处不展开）

## \*手动整定法

据我们老师所说，每个人用的都不一样，且结论大多为经验总结，只可做参考，不能当作一般性结论

| **参数调整**| **百分比超调量** | **调整时间** | **稳态误差** |
| --------- | ---------- | -------- | -------- |
| 增大 $K_P$​ | 增大 | 影响很小 | 减小 |
| 增大 $K_I$​ | 增大 | 增大 | 稳态误差为 0|
| 增大 $K_D$​ | 减小 | 减小 | 没有影响 |
