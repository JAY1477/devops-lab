# Docker Redis 部署

## 环境信息

- 系统：Ubuntu 24.04
- Docker：29.1.3
- 虚拟环境：VMware Workstation
- 网络模式：NAT

---

# 拉取 Redis 镜像

```bash
docker pull redis
```

作用：

- 从 Docker Hub 拉取 Redis 官方镜像
- 默认拉取 latest 最新版本

---

# 启动 Redis 容器

```bash
docker run -d \
--name redis \
-p 6379:6379 \
redis
```

参数说明：

| 参数 | 作用 |
|---|---|
| `-d` | 后台运行容器 |
| `--name redis` | 指定容器名称 |
| `-p 6379:6379` | 宿主机端口映射到容器端口 |
| `redis` | 使用 redis 镜像启动 |

---

# 查看运行中的容器

```bash
docker ps
```

正常会看到：

```text
CONTAINER ID   IMAGE   COMMAND                  STATUS
xxxxxx         redis   "docker-entrypoint.s…"  Up xx seconds
```

---

# 查看 Redis 日志

```bash
docker logs redis
```

正常会看到：

```text
Ready to accept connections
```

说明 Redis 服务启动成功。

---

# 进入 Redis 容器

```bash
docker exec -it redis bash
```

参数说明：

| 参数 | 作用 |
|---|---|
| `exec` | 在运行中的容器执行命令 |
| `-it` | 进入交互终端 |
| `redis` | 容器名称 |
| `bash` | 进入 bash shell |

进入后提示符类似：

```bash
root@xxxx:/data#
```

---

# Redis 测试

进入容器后执行：

```bash
redis-cli
```

进入 Redis 命令行。

执行：

```bash
ping
```

返回：

```text
PONG
```

说明 Redis 服务正常。

---

# 退出 Redis CLI

```bash
exit
```

---

# 退出容器

```bash
exit
```

---

# 停止 Redis 容器

```bash
docker stop redis
```

---

# 启动 Redis 容器

```bash
docker start redis
```

---

# 删除 Redis 容器

```bash
docker rm -f redis
```

---

# 学到的内容

本次学习内容：

- Docker 镜像拉取
- Docker 容器运行
- Docker 日志查看
- Docker 容器进入
- Redis 基础测试
- Docker 端口映射
- Docker 容器生命周期

---

# 遇到的问题

## Docker 拉取镜像速度慢

现象：

```text
Unable to find image locally
```

原因：

- Docker Hub 国内访问较慢

解决：

配置 Docker 镜像加速器。

---

# 常用 Docker 命令总结

## 查看容器

```bash
docker ps
```

---

## 查看所有容器

```bash
docker ps -a
```

---

## 查看日志

```bash
docker logs redis
```

---

## 进入容器

```bash
docker exec -it redis bash
```

---

## 停止容器

```bash
docker stop redis
```

---

## 启动容器

```bash
docker start redis
```

---

## 删除容器

```bash
docker rm -f redis
```
