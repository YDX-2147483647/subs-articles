---
title: 载流子浓度公式记忆技巧
description: 用了一点儿数学，没有一点儿数学。

math: true
---

> 2022 年 4 月 16—17 日。

## 示例

<figure>
    <img src="{{ '/assets/articles/carrier-concentration/basics.svg' | relative_url }}" alt=''>
</figure>

欲用 $E_i$ 表示 $E_F$，则观察图中从 $E_i$ 到 $E_F$ 的位移，发现是 $n_0 / N_c$“箭头”减去 $n_i / N_c$“箭头”，所以 $E_i - E_F = k_B T \ln(n_0 / n_i)$。下面是另一种步步为营的写法。

$$
\begin{split}
E_F
&= E_i - k_B T \ln\frac{n_i}{N_c} + k_B T \ln\frac{n_0}{N_c} \\
&= E_i + k_B T \ln\frac{n_0}{n_i}.
\end{split}
$$

欲用 $E_g \coloneqq E_c - E_v$ 表示 $n_i$，则找寻图中的 $n_i$，发现两个含 $n_i$ 的“箭头”加起来是从 $E_c$ 到 $E_v$ 的位移（即 $-E_g$），故

$$
\frac { {n_i}^2} {N_c N_v} = \exp\frac{-E_g}{k_B T}.
$$

然后闭着眼都能挪出 $n_i = \sqrt{N_c N_v} \exp(-E_g / (2k_B T))$。

---

涉及杂质能级上的浓度时也可这样处理。

<figure>
    <img src="{{ '/assets/articles/carrier-concentration/saturated.svg' | relative_url }}" alt=''>
</figure>

几乎饱和电离时，给定 $D_- \coloneqq n_D / N_D$，求 $N_D$ 范围。

含 $n_D$ 的“箭头”从 $E_D$ 到 $E_F$，而 $E_F$ 未知；注意 $\Delta E_D \coloneqq E_c - E_D$ 已知，如图想办法转换到它。再利用 $n_0 \approx N_D$，得

$$
\exp\frac{-\Delta E_D}{k_B T}
= \left. \frac{n_0}{N_c} \middle/ \frac{n_D}{g_D N_D} \right.
= \frac{g_D N_D}{N_c D_-}.
$$

于是 $g_D N_D = N_c D_- \exp(-\Delta E_D / (k_B T))$。

## 数学原理

### 结构

$\R$、加法、乘法，$\R^+$、乘法、幂构成 $\R$ 上的两个一维向量空间。

-   向量和的交换律：$1 + 2 = 3 = 2 + 1$，$3 \times 5 = 15 = 5 \times 3$。

-   零元：$0 + x = x$，$1 \times v = v$。

-   数乘对向量和的分配律：$\lambda(x + y) = \lambda x + \lambda y$，$(u \times v)^\mu = u^\mu \times v^\mu$。

-   ……

### 记号

一维向量空间当然同构，可以构造一系列保持结构的双射—— $\exp$、$\ln$ 便是一对。

我们后面区别对待这两个向量空间，记 $\vec v \in \R$，其中 $v \in \R^+$。因而允许这样写：$\vec u + \vec v = \overrightarrow{u \times v}$，$2 \vec u = \overrightarrow{u^2}$。这记号确实很拙劣，但掩藏了具体细节，有时更容易理解。

后面我们选取的双射是下面这对，其中 $k_B$ 是 Boltzmann 常数，$T$ 是热力学温度。

$$
\begin{aligned}
\vec u &= k_B T \ln u \in \R. \\
u &= \exp\frac{\vec u}{k_B T} \in \R^+. \\
\end{aligned}
$$

### 图示

画图时只画 $\R$ 不画 $\R^+$，让 $\R^+$ 寄生在 $\R$ 上。

<figure>
    <img src="{{ '/assets/articles/carrier-concentration/vector.svg' | relative_url }}" alt=''>
    <figcaption>$\R$ 及 $\R^+$ 的图示</figcaption>
</figure>

后面我们只给 $\vec u$ 标 $u$，不再写那么多；而且还把数轴竖过来。

---

有些东西需要强调一下。

-   向量是自由向量，不是固定的有向线段。

    电子分布在导带中，$n_0 / N_c$ 可以画在 $E_F$ 与 $E_c$ 之间，二者无关。

-   向量有方向（正负）。

    比较向量 $\vec u$ 与 $\vec v$ 时，可以比在 $\R$ 中的象（$u$ 和 $v$），也可以比图示有向线段的长度（$\abs{\vec u}$ 和 $\abs{\vec v}$）。不过比后者就没必要搞向量了。

-   $\vec u < 0$ 时仍然 $u > 0$。

    只是 $u < 1$ 而已。类似地，$\vec 1 = 0$。

-   写下 $\vec u$ 前，应确保 $u$ 的量纲是一。

-   $\vec u = x_\text{final} - x_\text{initial}$ 暗示了 $x$ 绝对，$\vec u$ 相对。

    后面的 $x$ 对应能级（取决于势能零点），实际是相对值；而 $u$ 对应浓度，实际是绝对值。这么说，$x$ 是“字面上是绝对值的相对值”，$u$ 是“作为相对值的绝对值”……`(@_@)`

## 分布律

<details markdown='1'>
<summary>记号</summary>

-   浓度（体数密度）

    -   $n_0$：电子。（negative，$0$ 指热平衡）
    -   $p_0$：空穴。（positive）
    -   $n_i$：本征（intrinsic）下的电子（或空穴）。
    -   $N_D$：施主（donor）。
    -   $N_A$：受主（acceptor）。
    -   $n_D$：施主能级上的电子。
    -   $p_A$：受主能级上的空穴。
    -   $n_D^+$：电离施主。
    -   $p_A^-$：电离受主。

-   能级

    -   $E_c$：导带（conduction）底。
    -   $E_v$：价带（valence）顶。
    -   $E_F$：Fermi（能级）。
    -   $E_i$：本征下的 $E_F$。
    -   $E_D$：施主。
    -   $E_A$：受主。

-   有效状态密度

    -   $N_c$：导带（底）。
    -   $N_v$：价带（顶）。

-   简并因子

    -   $g_D$：施主。
    -   $g_A$：受主。

</details>

### Fermi–Dirac 分布律

能带中：

$$
\begin{aligned}
n_0 &=  N_c \operatorname{F}_{1/2}\frac{E_F - E_c}{k_B T}. \\
p_0 &=  N_v \operatorname{F}_{1/2}\frac{E_v - E_F}{k_B T}. \\
\end{aligned}
$$

> 其中 $\operatorname{F}\_{k/2}$ 是 Fermi–Dirac 积分 $\eta \mapsto \frac{1}{(k/2)!} \int_{\R^+} \sqrt{x}^k / (1 + \exp(x-\eta)) \dd{x}$。

杂质能级上：

$$
\begin{aligned}
n_D &= g_D N_D \frac{1}{g_D + \exp\frac{E_D - E_F}{k_B T}}. \\
n_D^+ &= \frac{N_D}{g_D} \frac{1} { {g_D}^{-1} + \exp\frac{E_F - E_D}{k_B T}}. \\
\\
p_A &= g_A N_A \frac{1}{g_A + \exp\frac{E_F - E_A}{k_B T}}. \\
p_A^+ &= \frac{N_A}{g_A} \frac{1} { {g_A}^{-1} + \exp\frac{E_A - E_F}{k_B T}}. \\
\end{aligned}
$$

——这些玩意<sub>儿</sub>退化成 Maxwell-Boltzmann 分布后才与我们的向量空间有关。

### Maxwell-Boltzmann 分布律

$x \to -\infty$ 时，

$$
\exp x
\sim \frac{1}{c + \exp(-x)}
\sim \operatorname{F}_{k/2} x.
$$

注意只有 $x \to -\infty$ 时才是那个向量空间，平常都只是近似成立。如果 $\vec u > 0$（即 $ u > 1$），那这近似肯定不能用了。因此后面所有“天然”向量都向下，只有人为构造的向量可能向上。

非简并下，能带中有

$$
\begin{aligned}
\overrightarrow{\frac{n_0}{N_c}} &= E_F - E_c. \\
\overrightarrow{\frac{p_0}{N_v}} &= E_v - E_F.
\end{aligned}
$$

本征下 $n_0 = p_0 = n_i$，$E_F = E_i$。这四个式子综合起来就是最开始的图。

<figure>
    <img src="{{ '/assets/articles/carrier-concentration/basics.svg' | relative_url }}" alt=''>
    <figcaption>能带中</figcaption>
</figure>

杂质能级上同理，但电离了的和未电离的浓度退化条件互斥。

<figure>
    <img src="{{ '/assets/articles/carrier-concentration/n-trap.svg' | relative_url }}" alt=''>
    <figcaption>施主能级上</figcaption>
</figure>

<figure>
    <img src="{{ '/assets/articles/carrier-concentration/p-trap.svg' | relative_url }}" alt=''>
    <figcaption>受主能级上</figcaption>
</figure>
