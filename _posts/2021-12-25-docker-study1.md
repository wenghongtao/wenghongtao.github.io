---
layout: post
title:  "docker 的学习（一）"
categories: docker
tags:  docker 
author: wenghongtao
---

* content
{:toc}

docker 的学习（一）





## docker 的学习（一）
1. 创建网桥
```
docker network create wenght
```
2. 保存镜像
```
docker save -o [image].tar
sudo docker save -o test.tar test/core:v1.2
```

3. 删除容器
```
docker rm -f 容器ID
```

4. 打包镜像
```
sudo docker commit -a "wenght" -m "test-core" 32f4c171bb56 test/core:v2.2
```

    格式：docker commit :从容器创建一个新的镜像
    ```
    docker commit [OPTIONS] CONTAINER [REPOSITORY[:TAG]]
    ```
    OPTIONS说明：

    -a :提交的镜像作者；

    -c :使用Dockerfile指令来创建镜像；

    -m :提交时的说明文字；

    -p :在commit时，将容器暂停。

    例1:

    ```
    docker commit -a "runoob.com" -m "my apache" a404c6c174a2  mymysql:v1 
    ```

    例2:

    ```
    docker commit -m  ""   -a  ""   [CONTAINER ID]  [给新的镜像命名]
    docker commit -m  ""   -a  "" aa myelasticsearch:1.0
    ```










 














