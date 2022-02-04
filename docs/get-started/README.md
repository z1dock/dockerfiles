## 安装

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

## 参考

https://docs.docker.com/get-started/
