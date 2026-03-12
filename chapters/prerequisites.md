# 环境准备

在开始构建 OpenClaw 之前，你需要准备好开发环境和必要的依赖库。

## 通用要求

所有平台都需要以下工具：

- **Git** — 用于克隆源代码
- **CMake** (3.5+) — 跨平台构建系统
- **C++ 编译器** — 支持 C++11 标准

## Linux (Ubuntu / Debian)

```bash
sudo apt update
sudo apt install -y \
    git \
    cmake \
    build-essential \
    libsdl2-dev \
    libsdl2-image-dev \
    libsdl2-mixer-dev \
    libsdl2-ttf-dev \
    libsdl2-gfx-dev \
    libtinyxml-dev \
    zlib1g-dev
```

### 音频支持 (MIDI)

如果你想要 MIDI 音乐播放支持：

```bash
sudo apt install -y timidity freepats
```

## Linux (Fedora / RHEL)

```bash
sudo dnf install -y \
    git \
    cmake \
    gcc-c++ \
    SDL2-devel \
    SDL2_image-devel \
    SDL2_mixer-devel \
    SDL2_ttf-devel \
    SDL2_gfx-devel \
    tinyxml-devel \
    zlib-devel
```

## Linux (Arch Linux)

```bash
sudo pacman -S \
    git \
    cmake \
    base-devel \
    sdl2 \
    sdl2_image \
    sdl2_mixer \
    sdl2_ttf \
    sdl2_gfx
```

## Windows

### 方法一：Visual Studio (推荐)

1. 安装 [Visual Studio 2017](https://visualstudio.microsoft.com/) 或更新版本
2. 安装时选择 **"使用 C++ 的桌面开发"** 工作负载
3. 项目自带 VS2017 解决方案，所有库和头文件目录已预配置

### 方法二：CMake + MinGW

1. 安装 [CMake](https://cmake.org/download/)
2. 安装 [MinGW-w64](https://www.mingw-w64.org/)
3. 确保 `cmake` 和 `gcc` 在系统 PATH 中

## macOS

使用 [Homebrew](https://brew.sh/) 安装依赖：

```bash
brew install \
    git \
    cmake \
    sdl2 \
    sdl2_image \
    sdl2_mixer \
    sdl2_ttf \
    sdl2_gfx
```

## WebAssembly (Emscripten)

1. 安装 [Emscripten SDK](https://emscripten.org/docs/getting_started/downloads.html)：

```bash
git clone https://github.com/emscripten-core/emsdk.git
cd emsdk
./emsdk install latest
./emsdk activate latest
source ./emsdk_env.sh
```

2. 验证安装：

```bash
emcc --version
```

## 验证环境

安装完成后，运行以下命令验证关键工具：

```bash
git --version
cmake --version
gcc --version    # Linux/macOS
g++ --version    # Linux/macOS
```

确认所有工具都能正常输出版本信息后，即可进入下一步。
