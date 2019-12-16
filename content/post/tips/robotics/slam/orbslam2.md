---
title: Use of ORBSlam2
share: false  # Show social sharing links?
view: ["3"]
date: "2019-12-16"
markup: mmark
abstruct: ""
draft: true
categories : ["robotics-tips", "ros"]
tags : []
---
# ubuntu18.04 ros:melodicでORBSLAM2
[ORB_SLAM2](https://github.com/raulmur/ORB_SLAM2)を利用する。
[自分のレポジトリ](https://github.com/Taiki-Ishigaki/ORB_SLAM2)にForkし，Ubutntu18.04用にプログラムを変更した。

基本的に[ORB_SLAM2をUbuntu18.04で動かしてみた](https://qiita.com/yamakentoc/items/1e340b238e215646cd84)に従う

ORB_SLAM2をcloneする際に
```sh
git clone https://github.com/raulmur/ORB_SLAM2.git ORB_SLAM2
```
ではなく
```sh
git clone https://github.com/taiki-ishigaki/ORB_SLAM2.git ORB_SLAM2
git checkout ubuntu18.04
```
としブランチをubuntu18.04に変更すること
これによってubuntu18.04ようにプログラムなどを変更する必要がなくなる