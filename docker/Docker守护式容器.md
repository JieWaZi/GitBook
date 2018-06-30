# Docker 守护式容器

---

## 什么是守护式容器

除了交互式运行的容器（interactive container），也可以创建长期运行的容器。守护式容器（daemonized container）没有交互式会话，适合运行应用程序和服务。大多数时候是需要以守护式来运行容器。

## 以守护形式运行容器

``` shell
docker run -i -t IMAGE /bin/bash

# 再使用Ctrl+P或Ctrl+Q
```

## 附加到运行中的容器

``` shell
docker attach 容器名|容器ID
```

## 启动守护式容器

``` shell
docker run -d IMAGE /bin/bash -c "while true; do echo docker running; sleep5;done"

# -d:使容器以后台的方式运行,命令结束后容器依旧会停止，所以需要使用一个While循环保持处于运行状态
```

![1](./images/6.png)

## 查看容器日志

``` shell
docker logs [-f][-t][--tail] 容器名

# -f：跟踪日志
# -t：在返回的结果上加上时间戳
# --tail：显示最新的多少条

# 例如 ：
 docker logs -tf --tail 20 docker2
```

![1](./images/7.png)

## 查看容器中的进程

``` shell
docker top 容器名

# 例如 ：
docker top docker2
```

![1](./images/8.png)

## 在运行中的容器内启动新进程

``` shell
docker exec [-d][-i][-t] 容器名 [COMMAND][ARG...]


# 例如 ：
docker exec -i -t  docker2 /bin/sh -c "while true;do echo other process;sleep 2;done"
```

![1](./images/9.png)

## 停止守护式容器

``` shell
docker stop 容器名|容器ID
docker kill 容器名|容器ID

# stop：等待docker停止
# kill：立即停止

```