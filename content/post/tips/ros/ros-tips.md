---
title: Use of ROS
share: false  # Show social sharing links?
view: ["3"]
date: "2019-12-16"
markup: mmark
abstruct: ""
draft: true
categories : ["ros"]
tags : []
---
## RViz

シミュレータではない，ROSでシミュレータを使いたいならGazebo
```sh
rosrun rviz rviz
```
で起動する，「/opt/ros/kinematic/bin」にパスが通っているなら以下のコマンドで省略可能
```sh
rviz
```

## tf

ブロードキャスタとリスナ
tfはリスナの問い合わせに対してブロードキャストによって得られる情報から2フレーム間の相対位置を求める
- ブロードキャスト
異なる2フレーム間の相対位置を配信
- リスナ
異なる2フレーム間の相対位置を取得
