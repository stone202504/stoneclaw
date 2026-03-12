# 配置与运行

## 配置文件

OpenClaw 使用 `config.xml` 文件管理游戏设置。该文件位于游戏可执行文件所在目录。

### 基本配置示例

```xml
<?xml version="1.0"?>
<Configuration>
    <Display>
        <Size width="1920" height="1080" />
        <Scale>1.0</Scale>
        <Fullscreen>false</Fullscreen>
        <VSync>true</VSync>
    </Display>
    <Audio>
        <Frequency>44100</Frequency>
        <SoundVolume>50</SoundVolume>
        <MusicVolume>50</MusicVolume>
        <MusicOn>true</MusicOn>
        <SoundOn>true</SoundOn>
    </Audio>
    <Font>
        <Size>20</Size>
        <FontPath>ASSETS/console02.fon</FontPath>
    </Font>
    <Console>
        <BackgroundImagePath>ASSETS/STATES/MENU/SCREENS/MENU.PCX</BackgroundImagePath>
    </Console>
</Configuration>
```

## 常用配置项

### 显示设置

| 配置项 | 说明 | 推荐值 |
|--------|------|--------|
| `width` / `height` | 窗口分辨率 | 根据显示器调整 |
| `Fullscreen` | 全屏模式 | `false` (调试时) |
| `VSync` | 垂直同步 | `true` |
| `Scale` | 画面缩放比例 | `1.0` |

> **提示：** VSync 可以防止画面撕裂，但在某些系统上可能引入输入延迟。如果感觉操控不够灵敏，可以尝试关闭 VSync。

### 音频设置

| 配置项 | 说明 | 范围 |
|--------|------|------|
| `SoundVolume` | 音效音量 | 0-100 |
| `MusicVolume` | 音乐音量 | 0-100 |
| `Frequency` | 音频采样率 | 44100 |

## 运行游戏

### Linux / macOS

```bash
cd Build_Release
./openclaw
```

### Windows

双击 `Build_Release/OpenClaw.exe`，或在命令行中：

```cmd
cd Build_Release
OpenClaw.exe
```

## 游戏控制

| 按键 | 功能 |
|------|------|
| 方向键 | 移动 |
| Z | 攻击 (剑) |
| X | 跳跃 |
| C | 射击 (手枪) |
| Enter | 确认 / 暂停 |
| Esc | 返回菜单 |
| F1 | 帮助 |

## 命令行参数

OpenClaw 支持一些命令行参数：

```bash
./openclaw --help          # 显示帮助
./openclaw --level 5       # 直接加载第 5 关
./openclaw --windowed      # 窗口模式
```

> 具体支持的参数可能因版本不同而异，请以 `--help` 输出为准。
