---
title: satgalaxy-cli：跨平台SAT求解命令行工具
toc: true
date: 2025-07-09 20:56:06
tags: ["SAT求解器", "命令行工具", "Rust开发", ]
categories: ["SAT"]
description:  一个强大、跨平台的 SAT 求解命令行工具
keywords: ["SAT求解器", "命令行工具", "Rust开发", "Minisat","Glucose"]
---


**satgalaxy-cli** 是基于Rust开发的跨平台SAT求解命令行工具，集成了Minisat和Glucose求解引擎，为研究者和开发者提供开箱即用的求解体验。



## 概述


**satgalaxy-cli** 是一个基于Rust开发的命令行SAT求解工具，主要特性包括：
- 支持Minisat 2.2.0和Glucose 4.2.1求解引擎
- 跨平台兼容：Windows、macOS和Linux
- 支持本地文件和网络资源(DIMACS CNF格式)作为输入
- 提供求解器原生参数透传能力

无论是研究人员、学生，还是需要快速求解 SAT 实例的用户，`satgalaxy-cli` 都提供了一个方便且强大的解决方案。

---

## 安装方法

### 前提条件

 `satgalaxy-cli` 构建需要一下环境，请自行安装：


* **Rust 工具链**： ≥1.65.0。
* **CMake**：≥3.10。
* **C/C++ 编译器**： 
    - Windows: MSVC或MinGW
    - macOS: Xcode命令行工具
    - Linux: gcc/clang + make

### 安装

1. 从源码构建

```bash
    # 克隆仓库
git clone https://github.com/sat-galaxy/satgalaxy-cli.git
cd satgalaxy-cli

# 编译项目
cargo build --release

# 输出位置
# Windows: target/release/satgalaxy.exe
# Unix系: target/release/satgalaxy
```

2. 安装到系统路径

    ```bash
    cargo install --path .
    ```

    安装后可在终端直接使用`satgalaxy`命令， 可执行文件将放置在 Cargo bin 目录 (通常是 `~/.cargo/bin`) 中。

    **注意**：如果您使用的是 Windows，可能需要将 `~/.cargo/bin` 目录添加到您的 PATH 环境变量中。

---

## 使用说明
### 基本命令结构
```bash
satgalaxy [minisat|glucose]  [OPTIONS] [INPUT] [OUTPUT]
```
参数说明：
- `[OPTIONS]`: 求解器特定参数
- `[INPUT]`: 输入文件路径或URL（支持.zx/.tgz格式）
- `[OUTPUT]`: 可选输出文件路径（默认输出到stdout）
### 支持的文件格式
|类型|示例|说明|
| -------- | ------- |------- |
|纯文本CNF|	problem.cnf|	DIMACS CNF格式|
|.zx压缩|problem.zx|ZX压缩格式|
|.tgz压缩|problem.tgz|Gzip压缩的tar归档|
### 使用示例
```bash
# 求解本地.zx文件
satgalaxy minisat problem.zx

# 求解HTTP上的.tgz文件
satgalaxy glucose http://example.com/archive.tgz
```

输出结构如下所示
```text
c Parse time:           59.998µs
c Simplification time:  11.755µs
c Solve time:           7.856µs
c Total time:           90.961µs
c Run time:             104.244µs
c Memory:               14 MiB
c SATISFIABLE
SAT
1 -2 0
```
若指定输出文件则后两行会写入文件，其他输出会打印在屏幕上。
### 输出字段说明

|字段|示例值|说明|
| -------- | ------- |------- |
|Parse time|59.998µs|解析输入文件时间（CPU 时间）|
|Simplification time|11.755µs|问题简化时间（CPU 时间）||
|Solve time|7.856µs|核心求解时间（CPU 时间）||
|Total time|90.961µs|总处理时间（CPU 时间）||
|Run time|104.244µs|实际运行时间（实际运行时间）||
|Memory|14 MiB|内存使用量|
|求解结果|SATISFIABLE|SAT/UNSAT结果|
|解向量|1 -2 0|变量赋值序列|

## 项目信息
- 项目主页： [https://github.com/sat-galaxy/satgalaxy-cli](https://github.com/sat-galaxy/satgalaxy-cli)
- 问题反馈：可直接在GitHub提Issue

> 工具完全开源免费，如果觉得好用，给个Star⭐就是对我们最大的支持！也欢迎提交PR一起完善～