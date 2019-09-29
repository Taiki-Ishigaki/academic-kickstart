---
title: 線形倒立振子
share: false  # Show social sharing links?
view: ["3"]
date: "2019-09-29"
markup: mmark
abstruct: ""
draft: false
categories : ["humanoid"]
tags : []
---
## 倒立振子の運動

地面にfree jointとして接続された長さ$h$の棒に質点(重さ:$m$)倒立振子を考える(簡単のため同一平面上を動く時を考える). 振子の傾きを$\theta$として，倒立振子の運動方程式は，

$$
(m h^2)\ddot{\theta} = mg \sin\theta \ h
$$

$ 0 \simeq \theta $のとき，$\sin\theta \simeq \theta$とすることができるので

$$
\ddot{\theta} = \omega^2 \sin\theta \quad  \omega := \sqrt{\frac{g}{h}}\tag{1}
$$

重心位置$x_G$として，$x_G = h \sin\theta \simeq h\theta$なので(1)式は

$$
\ddot{x_G} = \omega x_G \tag{2}
$$

状態変数$x = [x_G \dot{x_G}]^T$として状態方程式は

$$
\dot{x} =
\left[
\begin{array}{rr}
\dot{x_G} \\
\ddot{x_G} \\
\end{array}
\right] =
\left[
\begin{array}{rr}
0 & 1 \\
\omega^2 & 0 \\
\end{array}
\right]
\left[
\begin{array}{rr}
x_G \\
\dot{x_G} \\
\end{array}
\right] =
Ax \tag{3}
$$

状態遷移行列$A$の固有値，固有ベクトルを求めシステムの性質を調べる

$$
det(\lambda E - A ) = 0 \\
\left|
\begin{array}{rr}
\lambda & -1 \\
-\omega^2 & \lambda \\
\end{array}
\right|
= \lambda^2 - \omega^2 = (\lambda - \omega) (\lambda + \omega) = 0 \\
\lambda = \omega, -\omega
$$

固有値は$\lambda = \omega, -\omega$で固有ベクトルは  
$\lambda = -\omega < 0$ のとき $a_1 = [1, -\omega]^T$  
$\lambda = \omega > 0$ のとき $a_2 = [1, \omega]^T$
