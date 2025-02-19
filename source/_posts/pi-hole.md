---
title: Pi-hole
date: 2022-06-14
tags: network
---
# Pi-hole 用法指南

Pi-hole 是一款开源的网络广告拦截工具，通过在网络层面拦截广告域名，保护整个网络的设备免受广告侵扰。它不仅可以拦截广告，还能提高网络速度、增强隐私保护。本文将介绍 Pi-hole 的安装、配置以及基本使用方法。

## 目录
1. [什么是 Pi-hole？](#什么是-pi-hole)
2. [安装 Pi-hole](#安装-pi-hole)
   - [硬件要求](#硬件要求)
   - [安装步骤](#安装步骤)
3. [配置 Pi-hole](#配置-pi-hole)
   - [设置 DNS](#设置-dns)
   - [管理界面](#管理界面)
4. [使用 Pi-hole](#使用-pi-hole)
   - [广告拦截](#广告拦截)
   - [白名单与黑名单](#白名单与黑名单)
   - [查看统计数据](#查看统计数据)
5. [高级功能](#高级功能)
   - [自定义过滤器](#自定义过滤器)
   - [远程访问](#远程访问)
6. [常见问题](#常见问题)
7. [总结](#总结)

---

## 什么是 Pi-hole？

Pi-hole 是一个网络级的广告拦截工具，通过在 DNS 层面拦截广告域名，阻止广告加载到用户的设备上。它的特点包括：
- **全网拦截**：保护网络中的所有设备，包括手机、电脑、智能电视等。
- **隐私保护**：阻止广告跟踪器，减少隐私泄露风险。
- **性能提升**：减少广告流量，加快网页加载速度。

---

## 安装 Pi-hole

### 硬件要求
- 一台 Raspberry Pi 或其他 Linux 设备。
- 稳定的网络连接。

### 安装步骤

1. **安装依赖**  
   确保系统已安装 `curl` 和 `git`：
   ```bash
   sudo apt update
   sudo apt install curl git
   ```

2. **下载安装脚本**  
   使用以下命令下载并运行 Pi-hole 的安装脚本：
   ```bash
   curl -sSL https://install.pi-hole.net | bash
   ```

3. **按照提示完成安装**  
   安装过程中会提示选择 DNS 提供商、设置管理员密码等。按照提示操作即可。

4. **完成安装**  
   安装完成后，记下显示的 Pi-hole 管理界面地址（如 `http://192.168.1.100/admin`）。

---

## 配置 Pi-hole

### 设置 DNS

1. 登录路由器管理界面。
2. 将 DNS 服务器地址设置为 Pi-hole 的 IP 地址。
3. 保存设置并重启路由器。

### 管理界面

1. 在浏览器中访问 Pi-hole 管理界面（如 `http://192.168.1.100/admin`）。
2. 输入安装时设置的管理员密码登录。

---

## 使用 Pi-hole

### 广告拦截

Pi-hole 默认会拦截常见的广告域名。启用后，所有连接到网络的设备都会自动受到保护。

### 白名单与黑名单

1. **白名单**  
   如果某些网站或服务被误拦截，可以将其添加到白名单：
   - 在管理界面中，点击 **Whitelist**。
   - 输入域名并保存。

2. **黑名单**  
   如果需要手动拦截某些域名，可以将其添加到黑名单：
   - 在管理界面中，点击 **Blacklist**。
   - 输入域名并保存。

### 查看统计数据

Pi-hole 提供详细的统计数据，包括：
- 拦截的广告数量。
- 查询的域名数量。
- 设备的活动情况。

在管理界面的 **Dashboard** 中可以查看这些数据。

---

## 高级功能

### 自定义过滤器

Pi-hole 支持自定义过滤器规则，可以拦截特定的域名或内容。例如：
- 拦截社交媒体跟踪器。
- 阻止恶意软件域名。

在管理界面的 **Group Management** 中可以添加自定义过滤器。

### 远程访问

通过配置动态 DNS 或 VPN，可以远程访问 Pi-hole 管理界面，随时随地管理网络。

---

## 常见问题

### 1. Pi-hole 拦截了正常网站怎么办？
- 将误拦截的域名添加到白名单。

### 2. 如何更新 Pi-hole？
- 使用以下命令更新 Pi-hole：
  ```bash
  pihole -up
  ```

### 3. Pi-hole 会影响网络速度吗？
- Pi-hole 通常会提高网络速度，因为它减少了广告流量。

---

## 总结

Pi-hole 是一款功能强大的广告拦截工具，能够有效保护整个网络的设备免受广告侵扰。通过简单的安装和配置，你可以享受更干净、更快速的网络体验。如果你对隐私保护和网络性能有较高要求，Pi-hole 是一个不可错过的工具。

如果有任何问题或建议，欢迎在评论区留言。

---

**参考链接：**
- [Pi-hole 官方网站](https://pi-hole.net/)
- [Pi-hole GitHub 页面](https://github.com/pi-hole/pi-hole)