---
title: '01好题'
date: 2025-07-12T15:07:56+08:00
math: true
---

16-17-1

![](https://image.huarenjian.cn/image/20250718134206944.png)

16-17-1

![](https://image.huarenjian.cn/image/20250718144341883.png)

怎么分析二维正态分布呢？

16-17-1

![](https://image.huarenjian.cn/image/20250718150144274.png)

比较的概率怎么求

要计算两个独立指数分布随机变量 $X$ 和 $Y$ 满足 $X < Y$ 的概率，可以使用以下步骤：

---

### **1. 概率密度函数**

**$X$** 服从均值为 1 的指数分布，其速率参数 $\lambda_X = 1$，PDF 为：

$$
f_X(x) = e^{-x}, \quad x \geq 0
$$

**$Y$** 服从均值为 $\frac{1}{4}$ 的指数分布，其速率参数 $\lambda_Y = 4$，PDF 为：

$$
f_Y(y) = 4e^{-4y}, \quad y \geq 0
$$

---

### **2. 概率表达式**

由于 $X$ 和 $Y$ 独立，联合 PDF 为：

$$
f_{X,Y}(x, y) = f_X(x) \cdot f_Y(y) = e^{-x} \cdot 4e^{-4y}
$$

要求 $P(X < Y)$，即：

$$
P(X < Y) = \int_{0}^{\infty} \int_{0}^{y} f_X(x) f_Y(y) \, dx \, dy
$$

---

### **3. 积分计算**
**内层积分（关于 $x$）**：

$$
\int_{0}^{y} e^{-x} \, dx = 1 - e^{-y}
$$

**外层积分（关于 $y$）**：

$$
P(X < Y) = \int_{0}^{\infty} (1 - e^{-y}) \cdot 4e^{-4y} \, dy
$$

分解为两个积分：

$$
= \int_{0}^{\infty} 4e^{-4y} \, dy - \int_{0}^{\infty} 4e^{-5y} \, dy
$$

**计算每个积分**：

第一个积分：

$$
  \int_{0}^{\infty} 4e^{-4y} \, dy = 1
$$

第二个积分：

$$
\int_{0}^{\infty} 4e^{-5y} \, dy = \frac{4}{5}
$$

**最终结果**：

$$
P(X < Y) = 1 - \frac{4}{5} = \frac{1}{5}
$$

---

### **4. 简化方法**

对于独立的指数分布 $X \sim \text{Exp}(\lambda)$ 和 $Y \sim \text{Exp}(\mu)$，有公式：

$$
P(X < Y) = \frac{\lambda}{\lambda + \mu}
$$

代入 $\lambda = 1$、$\mu = 4$：

$$
P(X < Y) = \frac{1}{1 + 4} = \frac{1}{5}
$$

---

### **最终答案**

$$
\boxed{\frac{1}{5}}
$$

---

- [ ]目前对概率相关的运算和逻辑完全没有概念，这部分内容要总结成专题！

---

## 第一章

![](https://image.huarenjian.cn/image/20250719192906214.png)

venn 图，找出所有的不相容种类，算出来 1156 人，超了

![](https://image.huarenjian.cn/image/20250719202340188.png)

答案应该是错的，参考

![|475](https://image.huarenjian.cn/image/20250719203206517.png)

![](https://image.huarenjian.cn/image/20250719203638803.png)
可以用高中的分隔板法。不对写你吗，54 张牌 4 个人怎么玩

![](https://image.huarenjian.cn/image/20250719201003009.png)

![](https://image.huarenjian.cn/image/20250719201655626.png)

没做出来，答案是个确定的数字，这也太假了
![](https://image.huarenjian.cn/image/20250720095238550.png)

贝叶斯公式

![](https://image.huarenjian.cn/image/20250720174645124.png)
贝叶斯最好看的一集.

$$ \frac{m-2}{m-2+n}$$

- [ ] 尝试理解本质，一眼看出答案

![](https://image.huarenjian.cn/image/20250720202548582.png)
适合更快的理解本质，这种等可能分割的情况不需要考虑分割的概率

![](https://image.huarenjian.cn/image/20250720203146535.png)
这更像思维题，显然第一次出正是等可能的，考虑到后续的可能性一定是乙更容易胜，所以对乙更有利。

第一次等可能，1/2正面-输赢参半，1/2 反面-乙更优，合计，乙更优。