# 容器基本操作

---

## 启动容器

``` shell
docker run IMAGE [COMMAND] [ARG...]

# IMAGE:镜像名
# COMMAND：命令
# ARG：参数

# 例如：
docker run ubuntu echo 'Hello World'
```

![1](./images/2.png)

## 启动交互式容器

``` shell
docker run -i -t IMAGE /bin/bash

# -i:--interactive=true|false 默认十false
# -t：--tty =true|false 默认为false

# 例如：
docker run ubuntu echo 'Hello World'
```

![1](./images/1.png)

## 查看容器命令

``` shell
docker ps [-a][-l]

# 当不指定参数时，显示正在运行的容器
# -a：列出所有容器，包括已经停止的容器
# -l；列出最新一次运行的容器
```

``` shell
docker inspect [容器ID][容器名字]

# 该命令用来查看容器的具体信息，
  参数可以是容器ID或者是容器名字

```

## 自定义容器名

``` shell
docker run --name=容器名 IMAGE [COMMAND] [ARG...]

# 使用--name来自定义名字

# 例如：
docker run --name=dockertest ubuntu /bin/bash
```

![1](./images/3.png)

## 重新开启容器

``` shell
docker start  容器名|容器ID

# 例如：
docker start -i dockertest1
```

![1](./images/4.png)

## 删除停止容器（并不能用于运行中的容器）

``` shell
docker rm  容器名|容器ID

# 例如：
docker rm dockertest1
```

![1](./images/5.png)