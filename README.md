# WHMCS Docker
## Prerequisite
Docker 已经安装
## 配置方法
### 1. 下载 Repo
```
git clone git@github.com:whao/whmcs-docker.git
cd whmcs-docker
```

### 2. 下载 `whmcs_v871_full.zip`
链接在Notion的 WHMCS Docker 环境配置文档中
### 3. 重命名 `docker-compose.example.yml` 为 `docker-compose.yml`
```
mv docker-compose.example.yml docker-compose.yml
```
### 4. 修改 `docker-compose.yml.example`
- 根据情况修改所有 `service` 中的端口映射
- 根据自己的host用户的UID和GID修改 `whmcs` 中 `user` 的值

### 5. 解压 `whmcs_v871_full.zip` 至 `whmcs-docker` 目录中

### 6. 创建 `db` 目录
```
mkdir db
```
### 7. 配置 Docker 网络
使用 `docker network inspect` 确认host上现有的docker虚拟网卡中没有使用 `172.20.0.0/16` 网段。如果有请修改其至其他网段。因为 WHMCS 的 license 是和 IP 绑定的。

## 最后的目录结构如下
```
.
├── db
├── docker-compose.yml
├── Dockerfile
├── EULA.txt
├── README.md
├── README-WHMCS.txt
└── whmcs
```
最后运行 `docker compose up`，在浏览器中配置WHMCS