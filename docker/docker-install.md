# Docker 安装记录

## 环境信息

- 系统：Ubuntu Server 24.04 LTS
- 虚拟化平台：VMware Workstation
- 用户：root

---

# 更新软件源

```bash
apt update
```

作用：

- 更新软件包索引
- 获取最新软件列表

---

# 安装 Docker

```bash
apt install docker.io -y
```

作用：

- 安装 Docker Engine
- 安装 Docker CLI
- 安装 containerd

---

# 查看 Docker 版本

```bash
docker -v
```

示例输出：

```text
Docker version 29.x.x
```

说明：

Docker 已安装成功。

---

# 设置开机自启

```bash
systemctl enable docker
```

作用：

系统启动时自动启动 Docker 服务。

---

# 启动 Docker

```bash
systemctl start docker
```

---

# 查看 Docker 状态

```bash
systemctl status docker
```

正常状态：

```text
Active: active (running)
```

说明：

Docker 服务运行正常。

---

# 验证 Docker

执行：

```bash
docker run hello-world
```

首次运行会自动下载镜像。

成功会看到：

```text
Hello from Docker!
```

说明：

- Docker Client 正常
- Docker Daemon 正常
- 镜像拉取正常
- 容器运行正常

---

# 查看本地镜像

```bash
docker images
```

示例：

```text
REPOSITORY    TAG       IMAGE ID
hello-world   latest    xxxxxxxx
```

---

# 查看运行中的容器

```bash
docker ps
```

---

# 查看所有容器

```bash
docker ps -a
```

---

# Docker 基础概念

## 镜像（Image）

镜像相当于系统安装包。

例如：

```text
nginx
redis
mysql
ubuntu
```

---

## 容器（Container）

容器是镜像运行后的实例。

例如：

```bash
docker run nginx
```

会创建一个 nginx 容器。

---

## 仓库（Registry）

Docker 默认从 Docker Hub 下载镜像。

例如：

```bash
docker pull redis
```

---

# 学到的内容

本次学习内容：

- Docker 安装
- Docker 服务管理
- Docker 开机自启
- Docker 镜像
- Docker 容器
- Docker Hub
- Hello World 测试

---

# 常用命令

## 查看版本

```bash
docker -v
```

---

## 查看镜像

```bash
docker images
```

---

## 查看运行容器

```bash
docker ps
```

---

## 查看所有容器

```bash
docker ps -a
```

---

## 启动容器

```bash
docker start 容器名
```

---

## 停止容器

```bash
docker stop 容器名
```

---

## 删除容器

```bash
docker rm -f 容器名
```

---

## 查看日志

```bash
docker logs 容器名
```

---

## 进入容器

```bash
docker exec -it 容器名 bash
```
