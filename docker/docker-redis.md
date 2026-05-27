# Docker Redis 部署

## 拉取镜像

```bash
docker pull redis
## 启动容器
docker run -d \
--name redis \
-p 6379:6379 \
redis
## 查看容器
docker ps
## 查看日志
docker logs redis
## 进入容器
docker exec -it redis bash
## Redis测试
redis-cli
ping
返回 PONG
