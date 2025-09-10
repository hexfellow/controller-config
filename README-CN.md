[中文](README-CN.md) | [English](README.md)
---

# 概述

本仓库提供适用于 Hex Controller 的配置文件示例。通过配合使用 `hf-bot-cfg-cli` 工具，可以快速切换 Hex Controller 的工作模式。

- **由于实际上功能是由两个不同的守护进程提供的，因此进行配置时务必同步修改两个json文件。**

## 使用方法

基本命令格式：
```bash
hf-bot-cfg-cli -c <json_path> --url ws://<controller_ip:port>
```

## 标准模式示例
### CanHub模式
```bash
hf-bot-cfg-cli -c ./can_hub/backend_config.json --url ws://<ip>:8404

hf-bot-cfg-cli -c ./can_hub/backend_config2.json --url ws://<ip>:9404
```
如果您希望不自动打开电源输出，可以将"backend_config.json"中的`"power_on"`参数设置为`false`.


### 双臂模式配置

**启用机械臂 `can0` 端口驱动及 CAN 转发：**
```bash
hf-bot-cfg-cli -c ./arm/<arm series>/backend_config.json --url ws://<ip>:8404
```

**启用机械臂 `can1` 端口驱动：**
```bash
hf-bot-cfg-cli -c ./arm/<arm series>/backend_config2.json --url ws://<ip>:9404
```

### 单臂模式配置

**启用机械臂 `can0` 端口驱动及 CAN 转发：**
```bash
hf-bot-cfg-cli -c ./arm/<arm series>/backend_config.json --url ws://<ip>:8404
```

**禁用机械臂 `can1` 端口驱动：**
```bash
hf-bot-cfg-cli -c ./can_hub/backend_config2.json --url ws://<ip>:9404
```