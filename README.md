- [Overview](#overview)
  - [Chassis](#chassis)
  - [Special Modes](#special-modes)
  - [Robotic Arm](#robotic-arm)
    - [Dual Arm Mode Configuration](#dual-arm-mode-configuration)
    - [Single Arm Mode Configuration](#single-arm-mode-configuration)

# Overview

This repository provides example configuration files for the Hex Controller. By using the `hf-bot-cfg-cli` tool, you can quickly switch the working mode of the Hex Controller.

Usage:

```bash
hf-bot-cfg-cli -c <json_path>/backend_config.json --url ws://<controller_ip>:8404

hf-bot-cfg-cli -c <json_path>/backend_config.json --url ws://<controller_ip>:9404
```

## Chassis
- [Ark](./base/ark_default/)
- [MaverX4](./base/maver_x4_default/)
- [TriggerA3](./base/trigger_a3_default/)

## Special Modes
- [CanHub Mode](./can_hub)
  - If you want to prevent automatic power output, set the `"power_on"` parameter in "backend_config.json" to `false`.

## Robotic Arm
### Dual Arm Mode Configuration

**Enable robotic arm `can0` port drive and CAN forwarding:**
```bash
hf-bot-cfg-cli -c ./arm/<arm series>/backend_config.json --url ws://<ip>:8404
```

**Enable robotic arm `can1` port drive:**
```bash
hf-bot-cfg-cli -c ./arm/<arm series>/backend_config2.json --url ws://<ip>:9404
```

### Single Arm Mode Configuration

**Enable robotic arm `can0` port drive and CAN forwarding:**
```bash
hf-bot-cfg-cli -c ./arm/<arm series>/backend_config.json --url ws://<ip>:8404
```

**Disable robotic arm `can1` port drive:**
```bash
hf-bot-cfg-cli -c ./can_hub/backend_config2.json --url ws://<ip>:9404
```