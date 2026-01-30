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

### 1. 环境准备

确保你已经安装了以下软件：
- [Visual Studio Code](https://code.visualstudio.com/)
- [Pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance) 插件（通常随 Python 插件自动安装）

### 2. 配置 VS Code

为了让编辑器识别这些桩文件并提供代码提示，你需要配置项目的 `pyrightconfig.json` 或 `settings.json`。

#### 方法 A：使用 `pyrightconfig.json` (推荐)

本项目根目录下已经包含了一个配置好的 `pyrightconfig.json` 文件。如果你是在当前目录下直接开发，开箱即用。

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

#### 方法 B：修改 VS Code 设置

你也可以在 VS Code 的 `.vscode/settings.json` 中添加以下配置：

```json
{
    "python.analysis.extraPaths": [
        "./stubs"
    ],
    "python.analysis.stubPath": "./stubs"
}
```

### 3. 验证配置

1. 打开 `seekfree_demo` 文件夹下的任意 `.py` 文件（例如 `E01_gpio_demo.py`）。
2. 尝试输入 `import machine` 或 `from smartcar import`。
3. 如果配置正确，你应该能看到相关的智能提示和文档说明。
4. 将鼠标悬停在函数名上（如 `machine.Pin`），可以看到详细的参数说明。

## 目录结构说明

- **`stubs/`**: 核心桩文件目录，包含所有 `.pyi` 定义文件。
- **`seekfree_demo/`**: 官方提供的功能例程，涵盖 GPIO、ADC、PWM、电机控制、PID 等常用功能。
- **`boot/`**: 启动文件模板。
    - `0-本文件夹下的两个py文件直接保存到设备根目录.txt`: 说明文件。
    - `boot.py`: 固件启动脚本。
    - `user_main.py`: 用户主程序入口。
- **`pyrightconfig.json`**: Pyright/Pylance 配置文件。

## 开发建议

- 建议将你的业务代码写在 `user_main.py` 中，或者新建文件并在 `user_main.py` 中导入，保持 `boot.py` 简洁。
- 参考 `seekfree_demo` 中的例程来学习如何使用各个硬件接口。
