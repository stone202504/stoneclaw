# 常见问题与故障排除

## 构建相关问题

### CMake 找不到 SDL2

**症状：** `Could NOT find SDL2`

**解决方法：**

```bash
# Ubuntu/Debian - 确认安装了开发包
sudo apt install libsdl2-dev libsdl2-image-dev libsdl2-mixer-dev libsdl2-ttf-dev libsdl2-gfx-dev

# macOS - 手动指定 SDL2 路径
cmake -DSDL2_DIR=$(brew --prefix sdl2)/lib/cmake/SDL2 ..
```

### SDL 2.0.6 兼容性问题

**症状：** 使用 SDL 2.0.6 时编译或运行出错

**解决方法：** 升级到最新版本的 SDL2。SDL 2.0.6 存在已知的兼容性问题。

```bash
# Ubuntu - 如果软件源中的版本太旧，从源码编译
# 下载地址: https://github.com/libsdl-org/SDL/releases
wget https://github.com/libsdl-org/SDL/releases/download/release-2.30.9/SDL2-2.30.9.tar.gz
tar xzf SDL2-2.30.9.tar.gz
cd SDL2-2.30.9
./configure
make -j$(nproc)
sudo make install
```

### Box2D 编译错误

**症状：** Box2D 相关的链接错误

**解决方法：** 不要尝试使用系统安装的 Box2D，使用项目自带的 Box2D 源码。在 Box2D 根目录运行 CMake 重新生成。

### C++ 标准不兼容

**症状：** 大量语法错误

**解决方法：** 确保编译器支持 C++11：

```bash
g++ --version   # 需要 GCC 4.8+
```

## 运行相关问题

### 找不到 CLAW.REZ

**症状：** 启动时提示缺少资源文件

**解决方法：**
1. 确保 `CLAW.REZ` 在 `Build_Release` 目录中
2. 确保 `ASSETS.ZIP` 已正确创建
3. 检查文件名大小写（Linux 区分大小写）

### SDL2.dll 缺失 (Windows)

**症状：** `The code execution cannot proceed because SDL2.dll was not found`

**解决方法：**
1. 从 [SDL2 GitHub Releases](https://github.com/libsdl-org/SDL/releases) 下载对应的 Runtime Binaries（选择 `SDL2-x.x.x-win32-x64.zip`）
2. 将 DLL 文件放入可执行文件所在目录
3. 或者从 OpenClaw 的 [GitHub Releases](https://github.com/pjasicek/OpenClaw/releases) 下载完整发布包（已包含所有 DLL）

### 没有声音

**症状：** 游戏运行正常但没有音效或音乐

**解决方法 (Linux)：**

```bash
# 安装 MIDI 支持
sudo apt install timidity freepats

# 检查音频设备
aplay -l
```

### 画面闪烁或撕裂

**症状：** 画面不稳定

**解决方法：** 在 `config.xml` 中启用 VSync：

```xml
<VSync>true</VSync>
```

### 性能问题

**症状：** 帧率低或卡顿

**解决方法：**
1. 使用 Release 构建而非 Debug 构建
2. 降低分辨率
3. 关闭不必要的后台程序
4. 确保显卡驱动是最新版本

## 获取帮助

如果以上方法都无法解决你的问题：

1. 查看 OpenClaw 的 [GitHub Issues 页面](https://github.com/pjasicek/OpenClaw/issues) 中是否有类似问题
2. 提交新的 Issue，附上：
   - 操作系统版本
   - 编译器版本
   - CMake 输出日志
   - 错误截图或日志
