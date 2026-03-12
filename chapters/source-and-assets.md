# 获取源码与游戏资源

## 克隆源码

```bash
git clone https://github.com/pjasicek/OpenClaw.git
cd OpenClaw
```

如果需要特定版本，可以在 [Releases 页面](https://github.com/pjasicek/OpenClaw/releases) 查看已发布的版本，或通过命令行查看：

```bash
git tag -l
```

## 准备游戏资源

> **重要提示：** 你必须拥有原版 Captain Claw 游戏的合法副本才能获取所需的资源文件。

### 第一步：获取 CLAW.REZ

`CLAW.REZ` 是原版游戏的资源包文件，包含所有的图形、音频和关卡数据。

将 `CLAW.REZ` 文件复制到项目的 `Build_Release` 目录中：

```bash
cp /path/to/your/CLAW.REZ Build_Release/
```

### 第二步：创建 ASSETS.ZIP

1. 确保 `Build_Release/ASSETS` 目录中包含所有必要的游戏资源文件
2. 将 ASSETS 目录中的内容打包为 ZIP 文件：

```bash
cd Build_Release/ASSETS
zip -r ../ASSETS.ZIP ./*
cd ../..
```

### 验证资源文件

确认以下文件存在且完整：

```bash
ls -la Build_Release/CLAW.REZ
ls -la Build_Release/ASSETS.ZIP
```

### 目录结构确认

完成后，`Build_Release` 目录应如下所示：

```
Build_Release/
├── CLAW.REZ        # 原版游戏资源包
├── ASSETS.ZIP      # 打包后的资源文件
├── ASSETS/         # 解包后的资源目录
│   ├── ...
│   └── ...
└── ...
```

## 常见问题

**Q: 在哪里可以找到 CLAW.REZ？**

A: `CLAW.REZ` 位于原版 Captain Claw 游戏的安装目录中。如果你拥有光盘版，安装游戏后在安装目录中可以找到该文件。

**Q: ASSETS 目录中应该有什么？**

A: ASSETS 目录包含从游戏资源中提取出来的各类文件（图片、音频、关卡数据等）。这些文件通常在首次构建或运行时由引擎自动生成。

**Q: 可以使用不同版本的 CLAW.REZ 吗？**

A: 建议使用英文原版游戏的 CLAW.REZ 文件，以确保最佳兼容性。
