## docker-k8s-devops

### Docker Platform

- docker 提供了一个开发，打包，运行app的平台，把app和底层infrastructure隔离开来
- cs架构（client && server）

### Docker Engine

- 后台进程（dockerd)
- REST API Server
- CLI接口 (docker)


### 底层技术支持

- Namespaces: 做隔离pid，net，ipc，mnt，uts
- Control groups: 做资源限制
- Union file systems: Container和image的分层

