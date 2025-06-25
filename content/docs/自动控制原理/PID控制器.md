---
title: "PID控制器"
date: 2025-06-25T13:13:25.746Z
draft: false
math: true
---

第十章 仅掌握设计方法（表示肯定不考，设计方法应该是出在）  
PID要考，有且仅有：ZN整定，λ整定。其他整定必不考  
作图：根轨迹和bode必画  
Nyquist图画概要图，三个重要的点为频率0和频率∞对应的点，以及与实轴交点  

## PID 控制器  

PID控制器传递函数

$$
 \begin{aligned}G_c(s)&=K_P+\frac{K_I}s+K_Ds=\frac{K_I\left(\frac{K_D}{K_I}s^2+\frac{K_P}{K_I}s+1\right)}{s}\\&=\frac{K_I\left(\tau s+1\right)\left(\frac\tau\alpha s+1\right)}{s}\end{aligned}
$$

可调参数可选 $K_P, K_I, K_D,$ 或者 $K_I,\tau,\alpha$

### ZN 整定  

### λ整定  

#### 记忆  

| 被控对象                             | $K_P$                        | $K_I$                        | $K_D$                        |
| -------------------------------- | ---------------------------- | ---------------------------- | ---------------------------- |
| $\dfrac{K}{Ts+1} e^{-\tau s}$    | $\dfrac{T}{K(\lambda+\tau)}$ | $\dfrac{1}{K(\lambda+\tau)}$ | -                            |
| $\dfrac{K}{s} e^{-\tau s}$       | $\dfrac{1}{K(\lambda+\tau)}$ | -                            | -                            |
| $\dfrac{K}{s(Ts+1)} e^{-\tau s}$ | $\dfrac{1}{K(\lambda+\tau)}$ | -                            | $\dfrac{T}{K(\lambda+\tau)}$ |

根据闭环系统过渡过程时间 $T_s$ 的要求，选择λ，满足  

$$
 T_s{=}\tau{+}4\lambda 
$$

#### 原理

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