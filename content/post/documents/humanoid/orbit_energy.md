---
title: 軌道エネルギー
share: false  # Show social sharing links?
view: ["3"]
date: "2019-10-28"
markup: mmark
abstruct: ""
draft: false
categories : ["humanoid"]
tags : []
---

## 線形倒立振子

$$
\ddot{x_G} = \omega^2 x_G \tag{1}
$$

$x_G$は重心位置として，重力加速度を$g$，重心の高さ$z$で一定として$\omega^2 = \frac{g}{z}$とする.

## 軌道エネルギー

式(1)の両辺に右から$x_G$をかけて

$$
\ddot{x_G}\dot{x_G} = \omega^2 x_G \dot{x_G} \\
\frac{d}{dt} (\frac{1}{2} {\dot{x_G}}^2) = \omega^2 \frac{d}{dt}( \frac{1}{2} {x_G}^2 ) \\
\frac{d}{dt}(\frac{1}{2} {\dot{x_G}}^2 - \omega^2  \frac{1}{2} {x_G}^2 ) = 0  \\
$$

以下のように軌道エネルギー$E$を定義すると

$$
E = \frac{1}{2} {\dot{x_G}}^2 - \omega^2  \frac{1}{2} {x_G}^2 \tag{2}
$$

軌道エネルギーの時間変化は

$$
\frac{d}{dt} E = 0
$$

以上のようになるので，一定であることが分かる．

## 軌道エネルギーを用いた計算

任意の重心位置，速度で目標速度$v_d$に制御するための着地点$x_z$を求める．ここで着地点$x_z$上で重心速度が$v_d$になるように計算する．  
エネルギーが一定であることから

$$
\frac{1}{2} {\dot{x_G}}^2 - \omega^2  \frac{1}{2} (x_z - x_G)^2 = \frac{1}{2} {\dot{v_d}}^2 - \omega^2  \frac{1}{2} (x_z - x_z)^2 \\
{\dot{x_G}}^2 - \omega^2  (x_z - x_G)^2 = {\dot{v_d}}^2 \\
$$

$$
x_z = x_G + \frac{\sqrt{{\dot{x_G}}^2 - {v_d}^2}}{\omega} \tag{3}
$$

ここで$v_d = 0$とすると以下のようになりcapture pointに一致する

$$
x_z = x_G + \frac{\dot{x_G}}{\omega} \tag{4}
$$

軌道エネルギーの正負から重心がポテンシャルを超えられるか判定することが可能

## 参考文献

- S.Kajita 2005 "ヒューマノイドロボット" オーム社
