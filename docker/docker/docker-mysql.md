# Docker MySQL 部署

## 环境信息

- 系统：Ubuntu 24.04
- Docker：29.x
- 虚拟环境：VMware Workstation
- 网络模式：NAT

---

# 拉取 MySQL 镜像

```bash
docker pull mysql:8.0
```

说明：

- 拉取 MySQL 8.0 官方镜像
- `8.0` 为镜像 tag（版本号）

---

# 创建 MySQL 数据目录

```bash
mkdir -p /data/mysql
```

说明：

用于数据持久化。

如果不挂载数据目录：

- 删除容器后
- 数据会全部丢失

---

# 启动 MySQL 容器

```bash
docker run -d \
--name mysql \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=123456 \
-v /data/mysql:/var/lib/mysql \
mysql:8.0
```

---

# 参数说明

| 参数 | 作用 |
|---|---|
| `-d` | 后台运行 |
| `--name mysql` | 容器名称 |
| `-p 3306:3306` | 端口映射 |
| `-e MYSQL_ROOT_PASSWORD` | 设置 root 密码 |
| `-v /data/mysql:/var/lib/mysql` | 数据持久化 |
| `mysql:8.0` | MySQL 8.0 镜像 |

---

# 查看运行中的容器

```bash
docker ps
```

---

# 查看 MySQL 日志

```bash
docker logs mysql
```

正常会看到：

```text
ready for connections
```

说明：

MySQL 已正常启动。

---

# 进入 MySQL 容器

```bash
docker exec -it mysql bash
```

---

# 登录 MySQL

```bash
mysql -uroot -p
```

输入密码：

```text
123456
```

---

# 查看数据库

```sql
show databases;
```

---

# 创建测试数据库

```sql
create database testdb;
```

---

# 再次查看数据库

```sql
show databases;
```

会看到：

```text
testdb
```

---

# 退出 MySQL

```sql
exit
```

---

# 退出容器

```bash
exit
```

---

# 删除 MySQL 容器

```bash
docker rm -f mysql
```

说明：

这里只删除容器。

不会删除：

```text
/data/mysql
```

中的数据。

---

# 重新创建 MySQL 容器

```bash
docker run -d \
--name mysql \
-p 3306:3306 \
-e MYSQL_ROOT_PASSWORD=123456 \
-v /data/mysql:/var/lib/mysql \
mysql:8.0
```

---

# 验证数据是否存在

重新登录 MySQL：

```bash
docker exec -it mysql bash
mysql -uroot -p
```

查看数据库：

```sql
show databases;
```

发现：

```text
testdb
```

仍然存在。

---

# 数据持久化理解

MySQL 数据实际存储在：

```text
/data/mysql
```

而不是容器内部。

因此：

- 删除容器
- 重建容器

数据不会丢失。

---

# 学到的内容

本次学习内容：

- Docker MySQL 部署
- MySQL 容器运行
- MySQL 日志查看
- MySQL 登录
- 数据持久化
- Docker volume
- 容器生命周期

---

# 常用 Docker 命令

## 查看容器

```bash
docker ps
```

---

## 查看日志

```bash
docker logs mysql
```

---

## 进入容器

```bash
docker exec -it mysql bash
```

---

## 停止容器

```bash
docker stop mysql
```

---

## 启动容器

```bash
docker start mysql
```

---

## 删除容器

```bash
docker rm -f mysql
```
