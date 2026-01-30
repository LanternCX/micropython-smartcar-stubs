# MicroPython SmartCar Stubs

提供了针对智能车（SmartCar）和逐飞（Seekfree）MicroPython 固件的代码提示桩文件（Stubs）。

通过使用这些 Stubs，你可以在 VS Code 等编辑器中获得完整的代码补全、类型检查和参数说明，极大地提升开发效率。

## 包含的模块

- `machine`: 标准 MicroPython 硬件控制接口
- `smartcar`: 智能车专用硬件驱动接口
- `seekfree`: 逐飞科技扩展库接口
- `display`: 屏幕显示相关接口
- `os`, `time`: 常用标准库

## 快速开始

1. **获取代码**
   
   使用 Git 克隆本仓库：

   ```bash
   git clone https://github.com/LanternCX/micropython-smartcar-stubs.git
   ```

2. **环境准备**
   
   - 安装 [Visual Studio Code](https://code.visualstudio.com/)。
   - 在 VS Code 中安装 [Python 插件](https://marketplace.visualstudio.com/items?itemName=ms-python.python)（插件会自动安装 Pylance 语言服务器）。

3. **开始开发**
   
   - 使用 VS Code 打开克隆下来的文件夹。
   - 本项目自带 `pyrightconfig.json` 配置文件，**开箱即用**。
   - 打开 `seekfree_demo` 下的任意文件（如 `E01_gpio_demo.py`），尝试悬停查看 `machine` 等模块提示，即刻享受代码补全。

## 配置详解

如果你想在**自己的新项目**中使用这套 Stubs，或者需要自定义配置，请参考以下说明。

为了让编辑器识别这些桩文件，你需要配置项目的 `pyrightconfig.json` 或 `settings.json`。

### 方法 A：使用 `pyrightconfig.json` (推荐)

如果你在新的项目中开发，请将本项目中的 `stubs` 文件夹复制到你的项目根目录，并创建一个 `pyrightconfig.json` 文件，内容如下：

```json
{
    "typeCheckingMode": "basic",
    "stubPath": "./stubs",
    "extraPaths": [
        "./stubs"
    ],
    "pythonVersion": "3.7"
}
```

### 方法 B：修改 VS Code 设置

你也可以在 VS Code 的 `.vscode/settings.json` 中添加以下配置：

```json
{
    "python.analysis.extraPaths": [
        "./stubs"
    ],
    "python.analysis.stubPath": "./stubs"
}
```

## 目录结构说明

```text
.
├── boot/                # 启动文件模板
│   ├── boot.py          # 固件启动脚本
│   └── user_main.py     # 用户主程序入口
├── seekfree_demo/       # 官方功能例程
├── stubs/               # 核心代码提示桩文件 (.pyi)
│   ├── display/         # 屏幕显示接口
│   ├── machine/         # MicroPython 标准硬件接口
│   ├── seekfree/        # 逐飞库
│   ├── smartcar/        # smartcar(nxp) 库
│   ├── os/              # 系统辅助库
│   └── time/            # 时间辅助库
├── pyrightconfig.json   # Pylance 配置文件
└── README.md            # 项目说明文档
```

## 注意事项

- **E28_wireless_uart_demo 和 E30_wifi_spi_demo**:
  
  为了确保数据类型正确，`data_wave` 列表的初始化已从整型修改为浮点型：
  ```python
  data_wave = [0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0]
  ```

## 开源协议

本项目采用 **GPL 3.0** 开源协议。

这意味着如果你在本项目的基础上进行开发，依据协议要求，你需要**开源你的代码**。

当然，你可以在比赛结束之后开源你的代码。

## 支持

如果本项目对你有帮助，欢迎在 GitHub 上给个 Star ⭐️ 。
