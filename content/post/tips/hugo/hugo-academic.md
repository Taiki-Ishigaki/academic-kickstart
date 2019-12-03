---
title: Using Hugo-Academic
share: false  # Show social sharing links?
view: ["3"]
date: "2019-12-03"
markup: mmark
abstruct: ""
draft: false
featured: true
categories : ["tips"]
tags : ["hugo-academic"]
---
## hugo install

最新のhugoをインストールする（バージョンが古いとacademic-kickstarが使えない  
以下のURLより 
　 https://github.com/gohugoio/hugo/releases  

以下のようにダウンロード(20191203)
```sh
wget https://github.com/gohugoio/hugo/releases/download/v0.60.1/hugo_0.60.1_Linux-64bit.deb
```

以下のコマンドでインストール
```
sudo apt install ./hugo_0.60.1_Linux-64bit.deb
```
  
```sh
hugo version
```  
でバージョンを確認することができる

## academic-kickstar

### Setting

1. Academic KickstarレポジトリをForkする
2. 自身のForkしたリポジトリから以下のようにclone (`sorcethemes`を自身のGithubユーザー名に変更) 
```sh 
  git clone https://github.com/sourcethemes/academic-kickstart.git My_Website
```

3. テーマの初期化  
```sh
cd My_Website 
```  
```sh
git submodule update --init --recursive
```

4. ビルド
今回の場合なら`My_Website`ディレクトリで以下を実行しビルド
```sh
hugo
```

## reference
- https://sourcethemes.com/academic/docs/
