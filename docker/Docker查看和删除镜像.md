# Docker查看和删除镜像

---

## 列出镜像

``` shell
docker images [OPTSIONS][REPOSITORY]

# -a:显示所有镜像（默认不显示）
# -f:过滤
# --no-trunc：不截断ID
# -q：只显示镜像的唯一ID

```

![1](./images/10.png)

* REPOSITORY:仓库名
* TAG:标签名
* IMAGE ID:镜像ID
* CREATED:创建时间
* SIZE:大小

## 查看镜像详细信息

``` shell
docker inspect [OPTSIONS] CONTAINER|IMAGE

# 例如
docker inspect ubuntu:latest

```

## 删除镜像

``` shell
docker rmi [OPTSIONS] IMAGE|[IMAGE...]

# -f：强制删除
# --no-prune:不删除打标签的父类镜像

# 例如
docker rmi ubuntu:latest

```