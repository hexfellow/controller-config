[中文](README-CN.md) | [English](README.md)
---

# Overview

This repository provides configuration file examples for Hex Controller. By using the `hf-bot-cfg-cli` tool, you can quickly switch the working mode of Hex Controller.

- **Since the functionality is actually provided by two different daemon processes, it is essential to synchronously modify both JSON files when configuring.**

## Usage

Basic command format:
```bash
hf-bot-cfg-cli -c <json_path> --url ws://<controller_ip:port>
```

## Standard Mode Examples

### CanHub Mode
```bash
hf-bot-cfg-cli -c ./can_hub/backend_config.json --url ws://<ip>:8404

hf-bot-cfg-cli -c ./can_hub/backend_config2.json --url ws://<ip>:9404
```
If you prefer not to automatically enable power output, you can set the `"power_on"` parameter to `false` in "backend_config.json".

### Dual Arm Configuration

**Enable arm `can0` port driver and CAN forwarding:**
```bash
hf-bot-cfg-cli -c ./arm/<arm series>/backend_config.json --url ws://<ip>:8404
```

**Enable arm `can1` port driver:**
```bash
hf-bot-cfg-cli -c ./arm/<arm series>/backend_config2.json --url ws://<ip>:9404
```

### Single Arm Configuration

**Enable arm `can0` port driver and CAN forwarding:**
```bash
hf-bot-cfg-cli -c ./arm/<arm series>/backend_config.json --url ws://<ip>:8404
```

**Disable arm `can1` port driver:**
```bash
hf-bot-cfg-cli -c ./can_hub/backend_config2.json --url ws://<ip>:9404
```
