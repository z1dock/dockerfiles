# build image 编译镜像

1. 什么是镜像: 程序模版
2.  build stage (编译过程)
3. run stage (执行过程)
4. Parser directives 解析器指令
5. 文件结构，层(layers)

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

|名称|含义|举例|说明|
|:---|:---|:---|:---|
|FROM|父镜像|`FROM ubuntu:latest`|-|
|RUN|执行, 执行结果会添加层(layer)|`RUN apt install g++` 或者 RUN ["命令", "参数1", "参数2"]|-|
|CMD|命令,Dockerfile里只能有一个, 镜像的默认执行入口| CMD ["命令", "参数1"]|-|
|ENTRYPOINT|执行入口,会覆盖CMD或使用CMD作为参数|ENTRYPOINT ["executable", "param1", "param2"]|allows you to configure a container that will run as an executable. allows you to configure a container that will run as an executable.|
|LABEL|添加元数据(metadata)|LABEL "com.exmple.vendor"="ACME Incorporated"|-|
|MAINTAINER|维护者名字(弃用)|MAINTAINER eric|-|
|EXPOSE|暴露端口|EXPOSE 80/tcp , EXPOSE 3306|-|
|ENV|定义变量|ENV MY_NAME=jack|-|
|ADD|添加文件(夹)|ADD src dest|instruction copies new files, directories or remote file URLs from <src> and adds them to the filesystem of the image at the path <dest>|
|COPY|复制文件|

## 参考

1. https://docs.docker.com/engine/reference/builder/
1. https://docs.docker.com/develop/develop-images/dockerfile_best-practices/
