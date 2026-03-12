# 项目概述

## 项目背景

**Captain Claw** 是 Monolith Productions 于 1997 年发行的经典 2D 平台跳跃游戏。玩家扮演猫船长 Nathaniel Joseph Claw，在各种关卡中冒险，收集宝石，击败敌人。

OpenClaw 项目由开发者 [pjasicek](https://github.com/pjasicek) 发起，目标是用现代 C++ 从零开始重新实现游戏引擎，使这款经典游戏能够在现代操作系统上流畅运行。

## 技术架构

```
OpenClaw
├── 游戏引擎核心
│   ├── 场景管理
│   ├── Actor 系统
│   ├── 事件系统
│   └── 资源管理
├── 渲染层 (SDL2 + SDL2_Image + SDL2_GFX)
├── 音频层 (SDL2_Mixer)
├── 字体渲染 (SDL2_TTF)
├── 物理引擎 (Box2D)
├── 配置管理 (TinyXML)
└── 资源解析器 (CLAW.REZ 解包)
```

## 与原版的区别

| 特性 | 原版 | OpenClaw |
|------|------|----------|
| 操作系统 | 仅 Windows 95/98 | Windows/Linux/macOS/Web |
| 分辨率 | 固定 640x480 | 可配置 |
| 引擎 | 闭源 | 完全开源 (C++) |
| 物理 | 自定义 | Box2D |
| 构建系统 | 无 (预编译) | CMake |

## 源码结构

```
OpenClaw/
├── OpenClaw/              # 游戏引擎主代码
│   ├── Engine/            # 引擎核心
│   │   ├── Actor/         # 游戏对象系统
│   │   ├── Graphics2D/    # 2D 渲染
│   │   ├── Physics/       # Box2D 物理封装
│   │   ├── Audio/         # 音频管理
│   │   ├── Resource/      # 资源加载
│   │   └── UserInterface/ # UI 系统
│   └── GameApp/           # 游戏应用层
├── Box2D/                 # Box2D 物理引擎源码
├── libwap/                # WAP/REZ 文件格式解析库
├── MidiProc/              # MIDI 音乐处理 (Windows)
├── Build_Release/         # 构建输出与游戏资源目录
│   └── ASSETS/            # 解包后的游戏资源
├── CMakeLists.txt         # CMake 构建配置
└── OpenClaw.sln           # Visual Studio 解决方案
```
