# Linux 平台构建

## 快速构建

确保已安装所有[依赖](prerequisites.md)后，执行以下步骤：

```bash
cd OpenClaw
mkdir build && cd build
cmake ..
make -j$(nproc)
```

编译完成后，可执行文件将生成在 `build` 目录中。

## 详细步骤

### 1. 创建构建目录

```bash
mkdir build
cd build
```

### 2. 运行 CMake 配置

```bash
cmake ..
```

CMake 会自动检测系统中安装的依赖库并生成 Makefile。

常用 CMake 选项：

| 选项 | 说明 | 默认值 |
|------|------|--------|
| `-DCMAKE_BUILD_TYPE=Release` | 构建类型 | Debug |
| `-DCMAKE_INSTALL_PREFIX=/usr/local` | 安装路径 | /usr/local |

示例（Release 构建）：

```bash
cmake -DCMAKE_BUILD_TYPE=Release ..
```

### 3. 编译

```bash
make -j$(nproc)
```

`-j$(nproc)` 会使用所有可用的 CPU 核心进行并行编译，加快构建速度。

### 4. 运行游戏

将编译生成的可执行文件复制到 `Build_Release` 目录（该目录包含游戏资源）：

```bash
cp openclaw ../Build_Release/
cd ../Build_Release
./openclaw
```

## 安装预编译包

如果你不想从源码编译，可以使用预编译包：

### Debian / Ubuntu

```bash
# 从 GitHub Releases 页面下载 .deb 包
sudo apt install ./openclaw_1.0-0.deb
```

### Fedora

```bash
sudo dnf install ./openclaw-1.0-1.x86_64.rpm
```

### CentOS / RHEL

```bash
sudo yum localinstall ./openclaw-1.0-1.x86_64.rpm
```

## 构建问题排查

### CMake 找不到 SDL2

如果 CMake 报告找不到 SDL2，请确认已安装开发包：

```bash
# 检查 SDL2 是否已安装
dpkg -l | grep libsdl2    # Debian/Ubuntu
rpm -qa | grep SDL2        # Fedora/RHEL
```

### 编译错误

如果遇到编译错误，尝试以下步骤：

1. 清理构建目录重新开始：

```bash
rm -rf build
mkdir build && cd build
cmake ..
make -j$(nproc)
```

2. 检查编译器版本是否支持 C++11：

```bash
g++ --version
```

3. 确保使用最新的 SDL2 库版本（SDL 2.0.6 存在已知兼容性问题）。
