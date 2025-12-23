- [Overview](#overview)
  - [Chassis](#chassis)
  - [Special Modes](#special-modes)
  - [Robotic Arm](#robotic-arm)
    - [Dual Arm Mode Configuration](#dual-arm-mode-configuration)
    - [Single Arm Mode Configuration](#single-arm-mode-configuration)

# Overview

This repository provides example configuration files for the Hex Controller. By using the `hf-bot-cfg-cli` tool, you can push config to the Hex Controller.

To start, you need a Linux host computer that is in the same network as the Hex Controller, and get `hf-bot-cfg-cli` using: 

`wget https://dl.hexfellow.com/hf-bot-cfg-cli/hbcc-x86_64 -O hbcc` or `wget https://dl.hexfellow.com/hf-bot-cfg-cli/hbcc-aarch64 -O hbcc`, depends on your host computer's architecture.

Remember to also run `chmod +x hbcc` to make the `hbcc` executable.

Then, you need to copy all the TWO configuration files to the host computer, and replace the `<controller_ip>` with the IP address of the Hex Controller.

Copy the first configuration file to the host computer by running:
```bash
./hbcc -c <json_path>/backend_config.json --url ws://<controller_ip>:8404
```

Copy the second configuration file to the host computer by running:
```bash
./hbcc -c <json_path>/backend_config2.json --url ws://<controller_ip>:9404
```

E.g., you need to update config file for the MaverL4 base, you can run:
```bash
./hbcc -c {path_to_this_repo}/base/maver_l4_default/backend_config.json --url ws://{IP of Hex Controller}:8404
```

Then
```bash
./hbcc -c {path_to_this_repo}/base/maver_l4_default/backend_config2.json --url ws://{IP of Hex Controller}:9404
```


## Chassis
- [Ark](./base/ark_default/)
- [MaverX4](./base/maver_x4_default/)
- [TriggerA3](./base/trigger_a3_default/)
- [MaverL4](./base/maver_l4_default/)

## Special Modes
- [CanHub Mode](./can_hub)
  - If you want to prevent automatic power output, set the `"power_on"` parameter in "backend_config.json" to `false`.

## Robotic Arm
### Dual Arm Mode Configuration

**Enable robotic arm `8439` port drive and CAN forwarding:**
```bash
./hbcc -c ./arm/<arm series>/backend_config.json --url ws://<ip>:8404
```

**Enable robotic arm `9439` port drive:**
```bash
./hbcc -c ./arm/<arm series>/backend_config2.json --url ws://<ip>:9404
```

### Single Arm Mode Configuration

**Enable robotic arm `8439` port drive and CAN forwarding:**
```bash
./hbcc -c ./arm/<arm series>/backend_config.json --url ws://<ip>:8404
```

**Disable robotic arm `9439` port drive:**
```bash
./hbcc -c ./can_hub/backend_config2.json --url ws://<ip>:9404
```