# Docker-Command-ZH

### 安装Docker
```
curl -fsSL https://get.docker.com/ | sh

# 检验是否安装成功,成功的话会看到server 和 client的相关信息
docker version
```

| 命令 | 说明 |
|--- |--- |
| docker login -u 用户名 -p 密码 | 登陆到Docker Hub |
| docker logout | 登出Docker Hub |
| docker pull 镜像名 | 拉取镜像 |
| docker pull -a 镜像名 | 拉取镜像名所有镜像 |
| docker push name:v1 | 上传本地镜像name:v1到镜像仓库中 |
| docker search java | 从Docker Hub查找java镜像 |
| docker images | 查看镜像列表 |
| docker image rm 镜像名或镜像id | 删除镜像 |
| docker save -o 保存的文件路径以及文件名 镜像名 | 镜像备份 |
| docker load -i 镜像路径 | 镜像迁移/加载到本地 |
| docker container start container_name或container_id | 启动容器 |
| docker container stop container_name或container_id | 停止容器 |
| docker container kill container_name或container_id | kill容器 |
| docker ps | 查看正在运行的容器 |
| docker ps -a | 查看所有容器 |
| docker rm container_id | 删除容器|
| docker commit 容器名 镜像名 | 容器保存为镜像 |
| docker container exec container_id 命令 | 向容器传入和执行命令|


容器相关操作
创建容器
```
docker run -itd --restart always --name 容器名 镜像名  执行的命令
其他参数含义：

--network=host 表示将主机的网络环境映射到容器中，容器的网络与主机相同
-p 表示端口映射，前者是宿主机端口，后者是容器内的映射端口。可以使用多个-p 做多个端口映射
-v 表示目录映射关系(前者是宿主机目录，后者是映射到宿主机上的目录，即 宿主机目录:容器中目录)，可以使 用多个-v 做多个目录或文件映射。注意:最好做目录映射，在宿主机上做修改，然后 共享到容器上。
-i 表示以“交互模式”运行容器 -t 表示容器启动后会进入其命令行。加入这两个参数后，容器创建就能登录进去。即 分配一个伪终端。
--name 为创建的容器命名
-d 在run后面加上-d参数,则会创建一个守护式容器在后台运行(这样创建容器后不 会自动登录容器，如果只加-i -t 两个参数，创建后就会自动进去容器)。
-e 为容器设置环境变量 -e username="ritchie": 设置环境变量
--net="bridge": 指定容器的网络连接类型，支持 bridge/host/none/container: 四种类型
--link=[]: 添加链接到另一个容器 -
-expose=[]: 开放一个端口或一组端口 -h "RidingRoad": 指定容器的hostname
```

查看容器列表
进入容器终端
docker attach container_id
或
docker container exec container_id /bin/bash
