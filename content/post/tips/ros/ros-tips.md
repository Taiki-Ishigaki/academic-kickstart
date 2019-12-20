---
title: Use of ROS
share: false  # Show social sharing links?
view: ["3"]
date: "2019-12-16"
markup: mmark
abstruct: ""
draft: false
categories : ["ros"]
tags : []
---
## 初めてのROS
rosがインストール完了しているとして

### ワークスペースの作成と設定
1. 任意の名前のワークスペース(例~/catkin_ws)ディレクトリとその中にsrcディレクトリを作成する
```sh
mkdir ~/catkin_ws/src
```

2. catkinワークスペースとして初期化
```sh
cd ~/catkin_ws/src
catkin_init_workspace
```

3. ワークスペースのビルド  
ワークスペース直下にbuildディレクトリとdevelディレクトリが生成
```sh
cd ~/catkin_ws
catkin_make
```

4. 環境変数の設定  
環境変数「$ROS_PACKAGE_PATH」に自分のワークスペースを追加する  
ワークスペースを変更したときに毎回行う必要あり
```sh
source ~/catkin_ws/devel/setup.bash
```
5. ワークスペースの環境変数を自動で読み込むようにする
新たにターミナルを起動しても自動で環境変数を読み込むように
```sh
echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc
```

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

## rqt 

### Robot Steering
```sh
rqt
```

Plugins->Robot Tools->Robot Steering
トピック名を変更