
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

![](https://github.com/yyccQQu/mini-docker/docker-k8s-devops/img/about_docker_image.png)

- 图中 image#4和image#2共享底层centos image
- 执行 `docker image ls`可查看所用image（镜像）

## Docker Image 的获取
- dockerfile
- pull from Registry 'docker pull centos:7.2.1511'
- dockerhub 下载




