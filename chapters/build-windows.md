# Windows 平台构建

## 方法一：Visual Studio (推荐)

项目自带 Visual Studio 2017 解决方案文件，所有库和头文件目录已预配置。

### 步骤

1. 用 Visual Studio 2017 (或更新版本) 打开 `OpenClaw.sln`
2. 在菜单栏选择 **"生成" → "生成解决方案"** (或按 `Ctrl+Shift+B`)
3. 等待编译完成
4. 编译输出在 `Build_Release` 目录中

### 配置选项

- **Debug**: 包含调试信息，适合开发调试
- **Release**: 优化构建，适合正常游玩

## 方法二：CMake + Visual Studio

如果你想使用其他版本的 Visual Studio：

```cmd
mkdir build
cd build
cmake -G "Visual Studio 15 2017" ..
```

常用生成器：

| Visual Studio 版本 | CMake 生成器 |
|--------------------|-------------|
| VS 2017 | `"Visual Studio 15 2017"` |
| VS 2019 | `"Visual Studio 16 2019"` |
| VS 2022 | `"Visual Studio 17 2022"` |

然后用 MSBuild 编译：

```cmd
msbuild OpenClaw.sln /p:Configuration=Release
```

## 方法三：CMake + NMake

```cmd
mkdir build
cd build
cmake -G "NMake Makefiles" ..
nmake
```

## 运行游戏

1. 确保 `Build_Release` 目录中包含：
   - `CLAW.REZ` (原版游戏资源)
   - `ASSETS.ZIP` (打包的资源文件)
   - `SDL2.dll` 及相关 DLL 文件

2. 运行 `OpenClaw.exe`

## SDL2 DLL 问题

如果启动时提示找不到 SDL2 相关 DLL：

1. 从 [SDL2 官网下载页](https://github.com/libsdl-org/SDL/releases) 下载 Runtime 版本（选择 `SDL2-x.x.x-win32-x64.zip`）
2. 或者从 OpenClaw 的 [GitHub Releases 页面](https://github.com/pjasicek/OpenClaw/releases) 下载包含所有 DLL 的发布包
3. 将以下 DLL 放入 `Build_Release` 目录：
   - `SDL2.dll`
   - `SDL2_image.dll`
   - `SDL2_mixer.dll`
   - `SDL2_ttf.dll`
   - `SDL2_gfx.dll`

## Box2D 编译说明

如果需要单独编译 Box2D：

1. 在 Box2D 根目录运行 CMake
2. 不要使用 `Build_Release` 目录中预编译的不同版本 SDL 库
3. 保持 Box2D 版本与项目一致
