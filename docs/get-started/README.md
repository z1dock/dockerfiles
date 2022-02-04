# 1. 安装

### 参考

1. https://docs.docker.com/engine/install/ubuntu/
1. https://docs.docker.com/engine/install/linux-postinstall/

```bash
## 清理已经安装的旧版 (新机器不用)
$sudo apt-get remove docker docker-engine docker.io containerd runc
## 设置软件仓库(repository)
$sudo apt-get update
$sudo apt-get install  ca-certificates curl gnupg lsb-release
$curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
$echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

$sudo apt update
$sudo apt-get install docker-ce docker-ce-cli containerd.io
## 验证安装完成
$sudo docker run hello-world
## 配置本地当前用户
$sudo groupadd docker ## 增加 docker 用户组
$sudo usermod -aG docker $USER ## 把自己加进去
## 登出 或者重启 后 再登入
$docker run hello-world
## 配置服务
$sudo systemctl enable docker.service
$sudo systemctl enable containerd.service
```


## get-started

```bash
##  -d 后台运行 , -p 宿主机端口:docker内端口
$docker run -d -p 8080:80 docker/getting-started
## 会看到运行中的docker
$docker ps
```

## 延伸阅读

1. 什么是容器
2. 什么是镜像


# 2. Sample Application/ 应用例子

```bash

$git clone https://github.com/docker/getting-started.git
$cd app
$vim Dockerfile
# syntax=docker/dockerfile:1
FROM node:12-alpine
RUN apk add --no-cache python2 g++ make
WORKDIR /app
COPY . .
RUN yarn install --production
CMD ["node", "src/index.js"]

```

### Dockerfile 命令

|命令|含义|
|:--|:--|
|FROM|继承镜像|
|RUN|编译镜像时执行/build|
|WORKDIR|-|
|CMD|run时执行|


## 参考

https://docs.docker.com/get-started/
