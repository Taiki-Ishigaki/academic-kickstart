---
title: 非線形制御
share: false  # Show social sharing links?
view: ["3"]
date: "2019-10-11"
markup: mmark
abstruct: ""
draft: true
categories : ["control theory"]
tags : []
---

## 非線形制御理論

- リアプノフの安定論に基づく制御系設計論
- 制御対象を線形系や類似のシステムに変換後に制御系設計をする構造論

構造論：非干渉制御，出力零化，逆システム

構造論の延長線上に"完全な線形化"と"Chained System"への変換がある．

完全な線形化  
非線形系を非線形の変数変換とフィードバックによって線形系に変換し，線形制御理論で得られた成果を利用する

Chained Systemへの変換
非線形系を干渉のある2入力1($u_1, u_2$)，2サブシステム($\Sigma_1, \Sigma_2$)からなる正準系に変換する  
変換された正準系は入力$u_1$を非零の一定値に固定すると，$\Sigma$が完全な線形系となるもの

制御対象として，非線形制御系の中で入力が状態変数から分離できる以下の系を対象とする

アファイン系

$$
\dot{x}(t) = f(x(t)) + G(x(t))u(t) \tag{1}
$$

対象アファイン系

$$
\dot{x}(t) =  G(x(t))u(t) \tag{2}
$$

### 変数変換と積分可能性

対象アファイン系での変数変換の例

状態変数を変数$y \in \mathbb{R}^1$に以下のように変換する．

$$
y(t) = h(x(t))
$$

$u$から影響を受けないかどうかを考える．  
線形系では

$$
\dot{x} = Bu \\
y = cx
$$

