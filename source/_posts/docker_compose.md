---
title: Docker Compose
date: 2023-08-08
tags: docker
---

# 使用 Docker Compose 部署应用

在现代软件开发中，容器化技术已经成为一种标准实践。Docker 是最流行的容器化平台之一，而 Docker Compose 则是一个用于定义和运行多容器 Docker 应用的工具。通过 Docker Compose，你可以使用一个 YAML 文件来配置应用的服务、网络和卷，然后通过一个简单的命令启动整个应用。

## 什么是 Docker Compose？

Docker Compose 是一个用于定义和运行多容器 Docker 应用的工具。它允许你使用一个 `docker-compose.yml` 文件来配置应用的服务、网络和卷。通过 Docker Compose，你可以轻松地启动、停止和重建应用的所有服务。

## 安装 Docker Compose

在开始使用 Docker Compose 之前，你需要确保已经安装了 Docker。Docker Compose 通常与 Docker 一起安装，但如果你需要单独安装，可以按照以下步骤进行：

### 在 Linux 上安装 Docker Compose

1. 下载 Docker Compose 二进制文件：

   ```bash
   sudo curl -L "https://github.com/docker/compose/releases/download/$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep -Po '"tag_name": "\K.*\d')" /usr/local/bin/docker-compose
   ```

2. 赋予二进制文件可执行权限：

   ```bash
   sudo chmod +x /usr/local/bin/docker-compose
   ```

3. 验证安装：

   ```bash
   docker-compose --version
   ```

### 在 Windows 和 macOS 上安装 Docker Compose

在 Windows 和 macOS 上，Docker Compose 通常与 Docker Desktop 一起安装。你可以通过 Docker Desktop 的安装程序来安装 Docker Compose。

## 编写 `docker-compose.yml` 文件

`docker-compose.yml` 文件是 Docker Compose 的核心配置文件。它定义了应用的服务、网络和卷。以下是一个简单的 `docker-compose.yml` 文件示例，用于部署一个包含 Web 服务和数据库的应用：

```yaml
version: '3.8'

services:
  web:
    image: nginx:latest
    ports:
      - "80:80"
    volumes:
      - ./html:/usr/share/nginx/html
    networks:
      - mynetwork

  db:
    image: mysql:5.7
    environment:
      MYSQL_ROOT_PASSWORD: example
      MYSQL_DATABASE: mydb
      MYSQL_USER: user
      MYSQL_PASSWORD: password
    volumes:
      - db_data:/var/lib/mysql
    networks:
      - mynetwork

volumes:
  db_data:

networks:
  mynetwork:
```

### 解释

- `version`: 指定 Docker Compose 文件的版本。
- `services`: 定义应用的服务。在这个例子中，我们定义了两个服务：`web` 和 `db`。
  - `web`: 使用 `nginx:latest` 镜像，将主机的 80 端口映射到容器的 80 端口，并将主机的 `./html` 目录挂载到容器的 `/usr/share/nginx/html` 目录。
  - `db`: 使用 `mysql:5.7` 镜像，设置了一些环境变量来配置 MySQL 数据库，并将数据库数据存储在名为 `db_data` 的卷中。
- `volumes`: 定义了一个名为 `db_data` 的卷，用于持久化数据库数据。
- `networks`: 定义了一个名为 `mynetwork` 的网络，用于连接 `web` 和 `db` 服务。

## 启动应用

在编写好 `docker-compose.yml` 文件后，你可以使用以下命令启动应用：

```bash
docker-compose up -d
```

`-d` 参数表示在后台运行容器。

## 停止应用

要停止应用，可以使用以下命令：

```bash
docker-compose down
```

这将停止并删除所有容器、网络和卷。

## 查看日志

你可以使用以下命令查看服务的日志：

```bash
docker-compose logs -f web
```

这将实时显示 `web` 服务的日志。

## 总结

Docker Compose 是一个强大的工具，可以帮助你轻松地定义和运行多容器 Docker 应用。通过一个简单的 `docker-compose.yml` 文件，你可以配置应用的所有服务、网络和卷，并使用简单的命令来管理整个应用的生命周期。希望这篇博客能帮助你更好地理解和使用 Docker Compose。


这篇博客介绍了 Docker Compose 的基本概念、安装方法、如何编写 `docker-compose.yml` 文件以及如何使用 Docker Compose 启动、停止和查看应用日志。希望对你有所帮助！