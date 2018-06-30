# Docker获取和推送镜像

---

## 查找镜像

* 访问 [Dockerhub官网](https://hub.docker.com/)

* 通过docker命令

    ``` shell
    docker search [OPTIONS] TEAM

    # --automated:
    # --no-trunc:
    # -s: 显示star大于多少的

    #例如
    docker search -s 5 ubuntu
    ```
    ![1](./images/11.png)

## 拉取镜像

修改registry-mirror

``` shell
docker pull [OPTIONS] NAME [:TAG]

# -a:下载所有标记的镜像下载到本地

# 例如
docker pull ubuntu：16.04
```

![1](./images/12.png)

## 推送镜像

``` shell
docker push NAME [:TAG]

# 例如
docker push ubuntu：16.04
```