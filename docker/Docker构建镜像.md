# Docker构建镜像

---

## 两种构建方法

* docker commit  通过容器构建
* docker build  通过Dockerfile文件构建

## 使用commit构建镜像

``` shell
docker commit [OPRIONS] CONTAINER [REPOSITORY[:TAG]]

# -a:作者信息
# -m：提交信息
# -p 暂停容器在提交的时候

# 例如：
docker commit -a "946065221@qq.com" -m "add nginx" nginx1 mynginx1:1.0
```

![1](./images/13.png)

## 使用Dockerfile构建镜像

1. 创建Dockerfile
2. 使用Docker build命令构建

### Dockerfile：

### 简单指令

``` shell

# nginx 服务器
FROM ubuntu:16.04
MAINTAINER ryan "946065221@qq.com"
RUN apt-get update && apt-get install -y nginx
EXPOSE 80

# MAINTAINER <name>: 指定镜像的作者信息，包含镜像的所有者和联系信息

# RUN <command> (shell模式) ： /bin/bash -c command

# RUN ["executable" , "param1","param2"] (exec模式)  ：

# EXPOSE <port>[<port>]：该容器的会使用该端口

```

### 更多指令

CMD命令：用于容器启动后执行的命令 ，会被docker run后面的参数覆盖

``` shell
CMD command param1 param2 (shell模式)
CMD ["executable" , "param1","param2"] (exec模式)
CMD ["param1","param2"] (作为ENTRYPOINT指令的默认参数)

#例如：
CMD /usr/sbin/nginx -g daemon off
```

ENTRYPOINT命令：用于容器启动后执行的命令 ，不会被docker run后面的参数覆盖

``` shell
ENTRYPOINT command param1 param2 (shell模式)
ENTRYPOINT ["executable" , "param1","param2"] (exec模式)

#例如：
ENTRYPOINT ["/usr/sbin/nginx", "-g","daemon off"]
```

CMD与ENTRYPOINT结合

``` shell
#例如：
ENTRYPOINT ["/usr/sbin/nginx"]
CMD -g daemon off
```

ADD命令：

``` shell
ADD <src>...<dest>
ADD["src"..."dest"](适合用于文件路径有空格的情况)
<src> :宿主机的文件路径
<dest>:docker的绝对路径
#例如：

ADD test.txt  /usr/local/
```

COPY命令：

``` shell
COPY <src>...<dest>
COPY["src"..."dest"](适合用于文件路径有空格的情况)
<src> :宿主机的文件路径
<dest>:docker的绝对路径
#例如：

COPY test.txt  /usr/local/
```

ADD vs COPY
ADD包含类似tar解压功能，如果单纯复制文件，DOcker推荐使用Copy

### Docker build：

``` shell
docker build [OPTION] PATH

# 例如：
docker build -t='nginxtest1' .
```

![1](./images/14.png)