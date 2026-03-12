# OpenClaw 安装教程

欢迎阅读 **OpenClaw** 完整安装与构建指南。

## 什么是 OpenClaw？

OpenClaw 是经典 2D 平台跳跃游戏 **Captain Claw (1997)** 的开源 C++ 重制版引擎。整个代码库从零开始编写，使用现代库和工具链，支持在当代操作系统上原生运行这款经典游戏。

> 原始项目地址：[github.com/pjasicek/OpenClaw](https://github.com/pjasicek/OpenClaw)

## 支持平台

| 平台 | 状态 |
|------|------|
| Linux (Ubuntu/Debian/Fedora) | 完整支持 |
| Windows (VS2017+) | 完整支持 |
| macOS | 支持 |
| WebAssembly (Emscripten) | 实验性支持 |
| Android | 实验性支持 |

## 核心依赖

- **SDL2** 系列库 — 图形、输入、音频、字体渲染
- **Box2D** — 物理引擎
- **TinyXML** — 数据驱动的配置管理
- **CMake** — 跨平台构建系统

## 法律声明

OpenClaw 引擎本身是合法的开源软件。但运行游戏需要原版 Captain Claw 的游戏资源文件 (`CLAW.REZ`)，该文件受版权保护。请确保你拥有正版游戏的合法副本。

---

点击左侧目录开始阅读各章节。
