---
title: 无限长带电圆柱面
description: 电荷均匀分布于无限长圆柱面，“绕轴匀速转动”和“沿轴匀速平移”是两个典型模型。

math: true
---

# 无限长带电圆柱面

> 2022年11月6日，2022年11月16–17日。
>
> 本文的其它版本：[WriteBug.com](https://www.writebug.com/explore/article/RtU7vqDH)。

## 情景

有一无限长均匀带电圆柱面，绕轴转动，请问管内外磁场分布怎样？

> 电荷均匀分布于无限长圆柱面，“绕轴匀速转动”（无限长载流直密绕螺线管）和“沿轴匀速平移”（无限长空心直导线）是两个典型模型，结课后最好达到“做梦都能梦清楚”的程度。
> 
> 这里只讨论前者。

## 极限过程

> 另请参考教材206页 §3.4.3 例3–9。（iCourse 教材，胡海云等《大学物理·（第三卷）电磁学》，高等教育出版社）

无限长圆柱面是**有限长**圆柱面的极限，密绕螺线管是几匝导线环的极限。

<figure>
  <img src='{{ '/assets/articles/solenoid/VFPt_Solenoid_correct2.svg' | relative_url }}' style='max-width: 60%;' >
  <figcaption markdown='1'>7匝导线环｜[Wikimedia Commons](https://commons.wikimedia.org/wiki/File:VFPt_Solenoid_correct2.svg)
  </figcaption>
</figure>

1. 考虑几匝导线环。在原来管壁附近，相邻导线环的磁场相互抵消，于是磁感线不会穿过管壁。
2. 考虑有限长圆柱面。由于磁感线只能绕着管壁走，圆柱内外的磁感线同样多，而圆柱外空间无限，所以圆柱变长时，有限的磁感线在外部要分布于无限的空间，外部磁场会趋于零。

这种方法从极限过程分析的，逻辑少，容易理解；然而未免夹杂插科打诨。下面我们再从对称性严格分析一下。（对称性是电磁学的一大主题，在平时多思考思考无碍。）

## 对称性

> 对称性有两种论证思路。
>
> - 找对称的两点，考虑它们作用之和。
> - 做某种对称操作，考虑操作前后的变化。
>
> 这里按第二种来。

> 电流分布有柱对称性，下面所说的径向、切向、轴向分别指 $\hat \rho$、$\hat \varphi$、$\hat z$。

- 切向：

  1. <u>绕轴旋转</u>对称性 ⇒ $\rho,z$ 相同时，切向分量与 $\varphi$ 无关。
  2. **安培环路定律**（环路取 $\rho = \rho_0$，$z = z_0$） ⇒ $\oint \vbi{B} \vdot \vbi{\dd{l}} = 0$ ⇒ 切向分量为零。

- 径向：

  1. 绕轴旋转对称性 ⇒ $\rho,z$ 相同时，径向分量与 $\varphi$ 无关。

  2. 对称性：<u>电流反向</u>，再<u>绕任意半径旋转</u>半周后，场景不变。

     电流反向 ⇔ $\vbi{B}$ 反向；由 1. 绕任意半径旋转半周相当于没变。

     因此这一对称性 ⇒ 无径向分量。

- 轴向：

  - 沿轴<u>平移</u>对称性 ⇒ $\rho,\varphi$ 相同时，轴向分量与 $z$ 无关。
  
  - 如下图中的 a、c，在 $\varphi$ 平面找一矩形环路，但不跨越圆柱面（不能是 b），运用**安培环路定律** ⇒ $\rho,\varphi$ 相同时，轴向分量在管内外分别与 $\rho$ 无关。
  
    <figure>
      <img src='{{ '/assets/articles/solenoid/Solenoid_with_3_loops.svg' | relative_url }}' style='max-width: 60%;' >
      <figcaption markdown='1'>三种矩形环路｜[Wikipedia](https://en.wikipedia.org/wiki/File:Solenoid_with_3_loops.svg)
      </figcaption>
    </figure>

以上推理说明：

- 无论在管内管外，$\vbi{B}$ 都最多有轴向分量。
- $\vbi{B}$ 在管内、管外分别匀强。

至此，$\vbi B$ 在全空间只有管内、管外强度两个变量待定。

## 物理实际

上面只考虑了对称，下面来考虑一点物理实际。（也就是207页剩下的部分）

### 管外磁感应强度为零

取特殊点 $\rho \to +\infty$。因为远离所有电流，磁感应强度为零。

> 由 BSL 定律，$\abs{\vbi{B}}$ 最差也是按 $1/\rho$ 衰减的。

再根据管外匀强，整个管外 $\vbi{B}$ 都是零。

### 管内磁感应强度为 $\mu_0 I_s$

> $I_s$ 是面电流线密度。

在 $\varphi$ 平面找一矩形环路，但**跨越圆柱面**（前面图中的 b），运用安培环路定律 ⇒ 管内管外磁感应强度之差是 $\mu_0 I_s$。

结合上一节可得结论。

## 联想

请读者思考以下各情景分别打破哪部分逻辑，哪些结论仍然适用。

- 矩形无限长载流密绕螺线管。
- 一双无限大平行平面，分别均匀载有等大反向电流。
- 单个无限大平面，载有均匀电流。
- 均匀密绕螺线环。
- 无限长载流密绕螺线管，不过沿轴的整体电流不可忽略。