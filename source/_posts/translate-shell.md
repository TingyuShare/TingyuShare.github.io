---
title: 使用 translate-shell 实现命令行翻译
date: 2023-09-26
tags: tools
---

# Translate Shell 用法指南

Translate Shell（原名 Google Translate CLI）是一款命令行翻译工具，支持多种语言之间的翻译。它基于 Google Translate、Bing Translator 等翻译服务，提供了简单易用的命令行接口。本文将介绍 Translate Shell 的安装、基本用法以及一些高级功能。

## 目录
1. [安装 Translate Shell](#安装-translate-shell)
   - [Linux](#linux)
   - [macOS](#macos)
   - [Windows](#windows)
2. [基本用法](#基本用法)
   - [简单翻译](#简单翻译)
   - [指定源语言和目标语言](#指定源语言和目标语言)
   - [翻译文件内容](#翻译文件内容)
3. [高级功能](#高级功能)
   - [语音播放](#语音播放)
   - [使用其他翻译服务](#使用其他翻译服务)
   - [交互模式](#交互模式)
4. [常见问题](#常见问题)
5. [总结](#总结)

---

## 安装 Translate Shell

### Linux

在大多数 Linux 发行版上，可以通过包管理器安装 Translate Shell。

#### Debian/Ubuntu
```bash
sudo apt update
sudo apt install translate-shell
```

#### Fedora
```bash
sudo dnf install translate-shell
```

#### Arch Linux
```bash
sudo pacman -S translate-shell
```

### macOS

在 macOS 上，可以使用 Homebrew 安装 Translate Shell。

```bash
brew install translate-shell
```

### Windows

在 Windows 上，可以通过 WSL（Windows Subsystem for Linux）安装 Translate Shell，或者直接下载预编译的二进制文件。

#### 使用 WSL
1. 安装 WSL 并选择一个 Linux 发行版（如 Ubuntu）。
2. 按照 Linux 的安装步骤安装 Translate Shell。

#### 下载二进制文件
1. 访问 [Translate Shell 的 GitHub 发布页面](https://github.com/soimort/translate-shell/releases)。
2. 下载适合 Windows 的二进制文件并解压。
3. 将解压后的文件路径添加到系统环境变量中。

---

## 基本用法

### 简单翻译

使用 `trans` 命令进行简单翻译。默认情况下，Translate Shell 会自动检测源语言并将其翻译为英语。

```bash
trans "你好"
```

**输出：**
```
你好

Hello
```

### 指定源语言和目标语言

可以通过 `:source` 和 `:target` 参数指定源语言和目标语言。

```bash
trans :zh "Hello"
```

**输出：**
```
Hello

你好
```

### 翻译文件内容

可以使用 `trans` 命令翻译文件内容。

```bash
trans :zh file.txt
```

---

## 高级功能

### 语音播放

Translate Shell 支持语音播放功能，可以通过 `-speak` 参数启用。

```bash
trans -speak "Hello"
```

### 使用其他翻译服务

默认情况下，Translate Shell 使用 Google Translate。可以通过 `-engine` 参数指定其他翻译服务，如 Bing。

```bash
trans -engine bing "你好"
```

### 交互模式

Translate Shell 提供了交互模式，可以通过 `-shell` 参数启用。

```bash
trans -shell
```

在交互模式下，可以连续输入文本进行翻译，输入 `quit` 退出。

---

## 常见问题

### 1. 翻译结果不准确怎么办？
- 确保指定了正确的源语言和目标语言。
- 尝试使用其他翻译引擎（如 Bing）。

### 2. 如何查看支持的语言列表？
- 使用以下命令查看支持的语言列表：
  ```bash
  trans -list-languages
  ```

### 3. 如何更新 Translate Shell？
- 在 Linux 上，可以通过包管理器更新。
- 在 macOS 上，使用 `brew upgrade translate-shell`。

---

## 总结

Translate Shell 是一款功能强大的命令行翻译工具，支持多种语言和翻译服务。通过简单的命令，你可以快速完成文本翻译、文件翻译等任务。如果你经常需要在命令行中进行翻译操作，Translate Shell 是一个不可错过的工具。

如果有任何问题或建议，欢迎在评论区留言。

---

**参考链接：**
- [Translate Shell GitHub 页面](https://github.com/soimort/translate-shell)
- [Translate Shell 官方文档](https://www.soimort.org/translate-shell/)