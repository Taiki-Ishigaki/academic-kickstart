---
title: Docker Tips
share: false  # Show social sharing links?
view: ["3"]
date: "2019-12-13"
markup: mmark
abstruct: ""
draft: false
categories : ["docker"]
tags : []
---

## docker command

### Dockerイメージをダウンロード

```sh
docker image pull repository:tag
```

### Dockerイメージを別名で保存

```sh
docker image tag repository:tag new_repository:new_tag
```

### DockerHubにpush

1. DockerHubアカウント作成

2. DockerHubにログイン  
  
    ```sh
    docker login
    ```
  
3. アカウントの確認

    ```sh
    docker info
    ```

4. プッシュ

    ```sh
    docker push repogitory
    ```

    repogitoryの名前はDockerHubのユーザ名から始まるもの
