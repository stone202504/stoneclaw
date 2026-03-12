# macOS 平台构建

## 前提条件

确保已通过 Homebrew 安装所有[依赖](prerequisites.md)：

```bash
brew install cmake sdl2 sdl2_image sdl2_mixer sdl2_ttf sdl2_gfx
```

同时需要安装 Xcode Command Line Tools：

```bash
xcode-select --install
```

## 构建步骤

```bash
cd OpenClaw
mkdir build && cd build
cmake ..
make -j$(sysctl -n hw.ncpu)
```

## 运行游戏

```bash
cp openclaw ../Build_Release/
cd ../Build_Release
./openclaw
```

## 注意事项

- macOS 的构建流程与 Linux 基本相同，使用 CMake + Make
- 确保 Homebrew 安装的 SDL2 库路径被 CMake 正确识别
- 如果 CMake 找不到 SDL2，可以手动指定路径：

```bash
cmake -DSDL2_DIR=$(brew --prefix sdl2)/lib/cmake/SDL2 ..
```

- Apple Silicon (M1/M2/M3) 用户可能需要使用 Rosetta 2 或确保安装的是 ARM 原生版本的 SDL2 库
