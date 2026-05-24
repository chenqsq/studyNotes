# Docker 教程

## 一、Docker 是什么？

Docker 可以理解为：

```text id="v9n2ki"
“轻量级虚拟机”
```

但它比虚拟机更轻：

* 启动快
* 占用低
* 部署方便
* 环境统一

---

## 二、为什么现在开发都用 Docker

以前：

```text id="tltgm9"
我电脑能跑
你电脑跑不了
服务器又炸了
```

现在：

```text id="r10b4d"
Docker 打包一次
哪里都能跑
```

---

## 三、Docker 能干嘛

你之后会经常拿它部署：

| 场景        | Docker作用         |
| --------- | ---------------- |
| 前端项目      | 部署 Next.js / Vue |
| Java后端    | SpringBoot       |
| Python AI | FastAPI / Flask  |
| 数据库       | MySQL / Redis    |
| 微服务       | 服务隔离             |
| CI/CD     | 自动部署             |
| 测试环境      | 快速启动             |

---

# 四、Windows 安装 Docker

## 推荐环境

| 软件             | 推荐 |
| -------------- | -- |
| Windows 11     | 推荐 |
| WSL2           | 必装 |
| Docker Desktop | 推荐 |

---

# 五、先安装 WSL2

如果没装：

管理员 PowerShell：

```powershell id="i6h2d5"
wsl --install
```

重启电脑。

查看：

```powershell id="kiz14t"
wsl -l -v
```

出现：

```text id="2jlwmj"
Ubuntu    Running    2
```

说明成功。

---

# 六、下载 Docker Desktop

官方下载：

https://www.docker.com/products/docker-desktop?utm_source=chatgpt.com

---

# 七、安装 Docker Desktop

安装时：

勾选：

```text id="zchd05"
Use WSL2 instead of Hyper-V
```

---

安装完成后：

重启电脑。

---

# 八、第一次启动 Docker

启动：

```text id="4q4v42"
Docker Desktop
```

看到：

```text id="y7zw9d"
Engine running
```

说明成功。

---

# 九、测试 Docker 是否安装成功

PowerShell 输入：

```powershell id="1n8u55"
docker -v
```

看到：

```text id="e91onm"
Docker version xx.x.x
```

---

再测试：

```powershell id="4ckq6r"
docker run hello-world
```

如果输出：

```text id="0lrr4e"
Hello from Docker!
```

说明 Docker 正常。

---

# 十、Docker 核心概念

| 名称           | 类比     |
| ------------ | ------ |
| 镜像 Image     | 安装包    |
| 容器 Container | 运行中的程序 |
| 仓库 Registry  | 应用商店   |
| Dockerfile   | 自动安装脚本 |
| Volume       | 数据存储   |
| Network      | 网络     |

---

# 十一、Docker 最常用命令

## 1. 查看镜像

```bash id="0pnr9k"
docker images
```

---

## 2. 查看运行中的容器

```bash id="ph6ux6"
docker ps
```

查看全部：

```bash id="p6d5zj"
docker ps -a
```

---

## 3. 拉取镜像

比如 MySQL：

```bash id="a6gg7v"
docker pull mysql
```

---

## 4. 启动容器

```bash id="1m0hih"
docker run -d nginx
```

参数：

| 参数     | 作用   |
| ------ | ---- |
| -d     | 后台运行 |
| -p     | 端口映射 |
| --name | 容器名字 |
| -v     | 挂载目录 |

---

## 5. 端口映射

```bash id="b07ymn"
docker run -d -p 8080:80 nginx
```

意思：

```text id="84m6ma"
本机8080 -> 容器80
```

浏览器访问：

```text id="z3i0xv"
http://localhost:8080
```

---

## 6. 停止容器

```bash id="0fvxqv"
docker stop 容器ID
```

---

## 7. 删除容器

```bash id="apuk77"
docker rm 容器ID
```

---

## 8. 删除镜像

```bash id="9m1hij"
docker rmi 镜像ID
```

---
