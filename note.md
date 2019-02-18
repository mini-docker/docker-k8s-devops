
-  ps -ef | grep docker 查看后台dockerd进程

## vagrant创建虚拟机
- 用 vagrant 搭建 docker环境
- https://www.vagrantup.com/ 下载完成之后
- 与根目录 执行 `vagrant init centos/7`
- 接着 执行 `vagrant up` 下载环境配置文件
- 执行 `vagrant ssh` 进入vagrant virtualmachine里面
- 执行 `sudo yum update` 检验是否能运行更新package

- 如果不想要这台虚拟机了 运行 `exit` 退出

- vagrant status 检验是否有运行的虚拟机
- vagrant halt 停掉正在运行的虚拟机
- vagrant destroy 销毁虚拟机