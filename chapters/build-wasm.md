# WebAssembly 构建

通过 Emscripten 可以将 OpenClaw 编译为 WebAssembly，在浏览器中运行游戏。

> **注意：** WebAssembly 版本为实验性支持，存在一些已知限制。

## 前提条件

确保已安装并激活 [Emscripten SDK](prerequisites.md)：

```bash
source /path/to/emsdk/emsdk_env.sh
emcc --version
```

## 构建步骤

```bash
cd OpenClaw
mkdir build && cd build
emcmake cmake -DEmscripten=1 ..
make
```

### 可选参数

| 参数 | 说明 |
|------|------|
| `-DEmscripten=1` | 启用 Emscripten 构建模式 |
| `-DExtern_Config=0` | 将 config.xml 嵌入游戏资源中 |

## 运行

编译完成后，需要通过 Web 服务器来运行：

```bash
cd ../Build_Release
python3 -m http.server 8080
```

然后在浏览器中访问 `http://localhost:8080`。

> **重要：** 由于浏览器安全限制，不能直接用 `file://` 协议打开，必须通过 HTTP 服务器访问。

## 已知限制

- **MIDI 音乐不支持** — WebAssembly 版本无法播放 MIDI 格式的游戏音乐
- **画面淡入淡出效果异常** — 部分渲染特效在 Web 环境中无法正常工作
- **旧版浏览器兼容性差** — 建议使用最新版 Chrome、Firefox 或 Edge
- **文件加载** — 游戏资源需要预加载到虚拟文件系统中，首次加载可能较慢
