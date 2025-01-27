---
title: FRP 暴露你的本地服务
date: 2022-06-13
tags: network
---
# 安装和使用 FRP 的指南

FRP（Fast Reverse Proxy）是一款高性能的反向代理工具，主要用于内网穿透。它可以帮助你将内网服务暴露到公网，方便远程访问。FRP 支持 TCP、UDP、HTTP、HTTPS 等多种协议，适用于 Windows、Linux 和 macOS 系统。本文将介绍如何安装和使用 FRP。

## 目录
1. [安装 FRP](#安装-frp)
   - [下载 FRP](#下载-frp)
   - [解压 FRP](#解压-frp)
2. [配置 FRP](#配置-frp)
   - [服务端配置](#服务端配置)
   - [客户端配置](#客户端配置)
3. [启动 FRP](#启动-frp)
   - [启动服务端](#启动服务端)
   - [启动客户端](#启动客户端)
4. [常见问题](#常见问题)
5. [参考链接](#参考链接)

## 安装 FRP

### 下载 FRP

1. 访问 [FRP GitHub 发布页面](https://github.com/fatedier/frp/releases) 下载适合你操作系统的 FRP 版本。
2. 选择对应的系统架构（如 `amd64`、`arm64` 等）和压缩包格式（如 `.zip` 或 `.tar.gz`）。

### 解压 FRP

1. 将下载的压缩包解压到指定目录。例如：

   ```bash
   tar -zxvf frp_0.45.0_linux_amd64.tar.gz
   ```

2. 进入解压后的目录：

   ```bash
   cd frp_0.45.0_linux_amd64
   ```

## 配置 FRP

### 服务端配置

1. 编辑 `frps.ini` 文件，配置 FRP 服务端。以下是一个简单的配置示例：

   ```ini
   [common]
   bind_port = 7000
   ```

   - `bind_port`：FRP 服务端监听的端口。

2. 保存并关闭文件。

### 客户端配置

1. 编辑 `frpc.ini` 文件，配置 FRP 客户端。以下是一个简单的配置示例：

   ```ini
   [common]
   server_addr = x.x.x.x
   server_port = 7000

   [web]
   type = http
   local_port = 80
   custom_domains = yourdomain.com
   ```

   - `server_addr`：FRP 服务端的公网 IP 地址。
   - `server_port`：FRP 服务端的监听端口。
   - `type`：代理类型（如 `http`、`tcp` 等）。
   - `local_port`：本地服务的端口。
   - `custom_domains`：自定义域名（仅适用于 HTTP/HTTPS 类型）。

2. 保存并关闭文件。

## 启动 FRP

### 启动服务端

1. 在 FRP 服务端目录下运行以下命令启动服务端：

   ```bash
   ./frps -c frps.ini
   ```

2. 如果一切正常，服务端会开始监听指定端口。

### 启动客户端

1. 在 FRP 客户端目录下运行以下命令启动客户端：

   ```bash
   ./frpc -c frpc.ini
   ```

2. 如果配置正确，客户端会连接到服务端，并将本地服务暴露到公网。

## 常见问题

### 1. 连接失败

- 检查服务端和客户端的配置文件，确保 `server_addr` 和 `server_port` 配置正确。
- 确保服务端防火墙允许 `bind_port` 端口的流量。

### 2. 客户端无法访问本地服务

- 检查本地服务是否正常运行。
- 确保 `local_port` 配置正确。

### 3. 如何查看日志

- FRP 默认会输出日志到控制台。你可以通过重定向输出到文件来保存日志：

  ```bash
  ./frps -c frps.ini > frps.log 2>&1 &
  ./frpc -c frpc.ini > frpc.log 2>&1 &
  ```

## 参考链接

- [FRP GitHub 仓库](https://github.com/fatedier/frp)
- [FRP 官方文档](https://gofrp.org/docs/)

---

通过本文，你应该已经掌握了如何安装和配置 FRP，并成功将内网服务暴露到公网。如果你有任何问题或建议，欢迎在评论区留言。