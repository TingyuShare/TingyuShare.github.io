---
title: smartDNS 加速你的访问
date: 2022-06-14 16:00:16
tags: dns
---
SmartDNS 是一个运行在本地的 DNS 服务器，它接受来自本地客户端的 DNS 查询请求，然后从多个上游 DNS 服务器获取 DNS 查询结果，并将访问速度最快的结果返回给客户端


## SmartDNS 与 DNSmasq 的区别
SmartDNS 返回最快的解析结果
Dnsmasq 可用于智能加快 DNS的分析结果。DNSmasq 也可用于 DHCP 

## SmartDNS 的缺点
正常浏览访问上网没有问题， 如果使用域名解析 LB 只会返回一个结果，不会有树形搜索返回LB后面的多个IP地址

## SmartDNS的使用
[smartdns 教程](https://pymumu.github.io/smartdns/)

## DNSmasq 教程部分
[DNSmasq 教程](https://cloud.tencent.com/developer/article/1174717)