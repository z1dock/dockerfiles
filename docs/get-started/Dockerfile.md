# build image 编译镜像

1. 什么是镜像: 程序模版
2.  build stage (编译过程)
3. run stage (执行过程)
4. Parser directives 解析器指令

## 编译命令

必须是目录，目录下有 Dockerfile 文件

```bash
$docker build -t image/name .
```

## Dockerfile

docker 镜像编译文件


### 举例

```dockerfile
# 注释 指令 directive
FROM base_image ## 第一句应该是继承某个镜像
命令 参数
命令 参数1 \
  参数2 参数3 \
  参数4
```

#### Parser directives 解析器指令

可选, 写在所有注释和编译指令之前

```dockerfile
# directive=value
```


#### 环境变量 environment replacement

## build instructions 编辑指令

|名称|含义|举例|
|:---|:---|:---|
|FROM|父镜像| FROM ubuntu:latest|
|RUN|执行|RUN `apt install g++`|
|||


## 参考

1. https://docs.docker.com/engine/reference/builder/
1. https://docs.docker.com/develop/develop-images/dockerfile_best-practices/
