# 12S ESC

This repository provides an open-source design for a 12S Electronic Speed Controller (ESC). It is designed to work with [ESCape32](https://github.com/neoxic/ESCape32), an open-source 32-bit ESC firmware.

## Specifications

- STM32G431 processor
- 24MHz HSE crystal resonator
- 12S (50.4V max) input
- All the features supported by [ESCape32](https://github.com/neoxic/ESCape32)

## Getting Started

For blank STM32s, these are the general steps to get the board up and running:

1. Configuring the option bytes.
2. Flashing the appropriate bootloader.
3. Flashing the firmware.

> [!WARNING]  
> Do not power the board directly with a battery before finishing these steps. Otherwise, the MOSFETs will get damaged since the gate drivers in V1 hardware do not have shoot-through protection.

### Prerequisites

- ST-LINK
- [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html)

### Option Bytes

1. Always run from flash.

    - BOOT_LOCK = 1

2. Disable read/write protection (if not set by default).

    - RDP = AA (Level 0)
    - Flash protection = disabled

### Bootloader

 Get the latest `BOOT4_PA2` bootloader binary from [https://github.com/neoxic/ESCape32/releases](https://github.com/neoxic/ESCape32/releases) and flash at address `0x08000000`.

### Firmware

Build the following baseline target and flash at address `0x08001000`.

```
add_target(CRLS69 STM32G431 DEAD_TIME=130 COMP_MAP=123 HALL_MAP=0xB450 SENS_MAP=0xB2A6A7 VOLT_MUL=3130 CURR_MUL=20 TEMP_CHAN=12 TEMP_FUNC=NTC10K3455UP2K USE_XOR USE_HSE=24)
```

## Resources

[ESCape32's Installation Wiki Page](https://github.com/neoxic/ESCape32/wiki/Installation)

[Building ESCape32 on Windows](https://github.com/adrianblakey/slot-car-ecom/wiki/Building-ESCape32-on-Windows)
