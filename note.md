
-  ps -ef | grep docker 查看后台dockerd进程

## vagrant创建虚拟机
- 用 vagrant 搭建 docker环境
- https://www.vagrantup.com/ 下载完成之后
- 与根目录 执行 `vagrant init centos/7`
- 接着 执行 `vagrant up` 下载环境配置文件
- 执行 `vagrant ssh` 进入vagrant virtualmachine里面
- 执行 `sudo yum update` 检验是否能运行更新package
- 主要做 vagrant创建的centos7的环境

- 如果不想要这台虚拟机了 运行 `exit` 退出

- vagrant status 检验是否有运行的虚拟机
- vagrant halt 停掉正在运行的虚拟机
- vagrant destroy 销毁虚拟机

## 什么是Docker Image（镜像）
- 文件(root filesystem)和meta data的集合
- 对Linux系统，分为内核空间（boot filesystem）和用户空间（boot filesystem上面做的发行版）
- 分层的，并且每一层都可以添加改变删除文件，成为一个新的image
- 不同的image可以共享相同的layer
- Image 本身是read-only的

![](https://github.com/mini-docker/docker-k8s-devops/blob/master/img/about%20Docker%20Image.png)

- 图中 image#4和image#2共享底层centos image
- 执行 `docker image ls`可查看所用image（镜像）

## Docker Image 的获取
- dockerfile
- pull from Registry 'docker pull centos:7.2.1511'
- dockerhub 下载

- [Docker Image 的删除](https://blog.csdn.net/winy_lm/article/details/77980529) 


- docker pull hello-world
- docker image ls
- docker run hello-world


## 编译c语言
- history | grep yum
- sudo yum install git 
- sudo yum install vim
- sudo yum install docker 

- [sudo yum install gcc](https://www.jianshu.com/p/795ff28ac8d2)
- sudo yum install glibc
- sudo yum install locate
- sudo yum install glibc-static

### 执行命令均在对应虚拟机下的文件目录下执行
- gcc -static hello.c -o hello //编译c语言
- vim hello.c,,, vim dockerfile
- docker build -t xie19docker/hello-world .
- 发布遇到问题 执行 `sudo su - root`, `systemctl start docker`
-      (https://stackoverflow.com/questions/44678725/cannot-connect-to-the-docker-daemon-at-unix-var-run-docker-sock-is-the-docker) 执行 docker build 命令用于使用 Dockerfile 创建镜像。

- docker history e157dcaa45bf(IMAGE ID) 查看docker分层
- docker run xie19docker/hello-world 执行成功代表 hello-world 可以当成一个container去执行的
- 1)，制作base image hello-word
- 2)，通过dockerfile 构建一个baseimg
- 3)，并且baseimg 可以通过container去执行



## 关于 yum 
- yum repolist
- yum update
- sudo su - root // 完全切换到root用户
- yum update
- yum -y install  gcc
- https://www.jianshu.com/p/541c737bc947 //添加到网易yum源
- yum -y install wget
- wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.163.com/.help/CentOS7-Base-163.repo

- yum clean all
- yum makecache


## 什么是container
- 通过Image创建（copy）
- 在Image Layer之上建立一个container layer（可读写）
- 类比面向对象： 类和实例
- Image负责app的存储和分发，Container 负责运行app

![](https://github.com/mini-docker/docker-k8s-devops/blob/master/img/about%20Docker%20Container.png)

- `sudo docker container ls` 列举当前本地正在运行的容器
- `sudo docker container ls -a`
- `more hello-world/Dockerfile`

- `docker -h` Management Commands: Commands:

- `docker ps -a` == ` docker image ls`
- `docker container ls -aq` 直接列举imageId
- `docker rm $(docker container ls -aq)` 全部清除container

- `docker rm $(docker container ls -f "status=exited" -q)`全部清除已退出的container

### 基于某个image创建container 
- docker container commit

- docker image build --> docker build

- 把一个container重新commit成一个image
- docker run -it centos 交互运行centos（在centos上操作）
- yum install vim
- sudo docker container ls -a 找到 NAMES
- sudo docker commit gallant_easley xie19docker/centos-vim

#### 在对应虚拟机目录下
- mkdir docker-centos-vim
- cd docker-centos-vim/
- vim Dockerfile
- sudo docker build -t xie19docker/centos-vim-new .



