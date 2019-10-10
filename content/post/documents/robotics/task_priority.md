---
title: 優先度付き微分逆運動学
share: false  # Show social sharing links?
view: ["3"]
date: "2019-10-09"
markup: mmark
abstruct: ""
draft: false
categories : ["robotics"]
tags : []
---

## 準備

### 順運動学と微分順運動学

$x \in \mathbb{R}^{m}$ と リンク系の状態を示す一般化座標$q \in \mathbb{R}^{n}$

順運動学

$$
x = f(q) \tag{1}
$$

微分順運動学

$$
\dot{x} = J(q) \dot{q} \tag{2}
$$

ここで$J(q) = \frac{\partial f}{\partial q} \in \mathbb{R}^{m \times n}$

## 微分逆運動学

$m < n$で冗長な時，式(1)の一般解，微分逆運動学の式は

$$
\dot{q} = J^{\sharp} \dot{x} + N y \tag{3}
$$

ここで$J^{\sharp}$は$J$の擬似逆行列で$N$は任意のベクトルを$J(\theta)$のヌルスペースに写像する行列で$y$は任意のベクトル．

## 優先度付き微分逆運動学

制御を行なう上で実現させたい量(手先の位置や速度，角運動量など)をタスクと呼ぶ．この時，そのタスクは式(1)のように一般化座標で表すことができるためタスクを実現するために一般化座標について解きロボットを制御する．  

ここでそのタスクが優先度を持って与えられたとする．タスク$x_i (i = 1, ... n)$，ここでタスクのインデックスが小さいほど優先順位が高いとする．

高い優先度のタスクを式(3)の微分逆運動学で実現し，$J_i$のヌルスペースでより低い優先度のタスクを実現する．[1]

$$
\dot{x_i} = J_i \dot{q}
$$

$$
\dot{q} = {J_i}^{\sharp} \dot{x_i} + N_i y \tag{4}
$$

$$
\dot{x_{i+1}} = J_{i+1} \dot{q} \tag{5}
$$

式(4)，(5)を同時に満たす，$y$を求める．(5)式に(4)式を代入すると

$$
\dot{x_{i+1}} = J_{i+1} {J_i}^{\sharp} \dot{x_i} + J_{i+1} N_i y
$$

$$
y =  (J_{i+1} N_i )^{\sharp} (\dot{x_{i+1}} - J_{i+1} {J_i}^{\sharp} \dot{x_i}) + N_{i+1} z
$$

ここで優先度順で解いた時に，漸化式によって分解でき以下のような一般解となる．[2]

$$
\rm{for} \  i = i \  \rm{to} \  N
$$

$$
\dot{q_i} = \dot{q_{i-1}} + (J_i N_{i-1})^{\sharp} (\dot{x_i} - J_i \dot{q_{i-1}})
$$

$$
N_i = N_{i-1} - (J_i N_{i_1})^{\sharp}(J_i N_{i_1})
$$

## Reference

[1]: Y.Nakamura, et al. (1987) "Task-Priority Based Redundancy Control of Robot Manipulators"  
[2]: B.Siciliano, J-J E. Slotine (1991) "A General Framework for Managing Multiple Tasks in Highly Redundant Robotic Systems"
