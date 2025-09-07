# Getting Started

## Flashing and Setup

For blank STM32s, these are the general steps to get the board up and running:

1. Configuring the option bytes.
2. Flashing the appropriate bootloader.
3. Flashing the firmware.

> [!WARNING]  
> Do **not** power the board with a battery before completing these steps. The gate drivers do not have shoot-through protection, and powering prematurely will damage the MOSFETs.

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

Build the following baseline target(s) and flash at address `0x08001000`.

**v1:**

```
add_target(CRLS1 STM32G431 DEAD_TIME=240 COMP_MAP=123 HALL_MAP=0xB450 SENS_MAP=0xB2A6A7 VOLT_MUL=3130 CURR_MUL=20 TEMP_ADC2 TEMP_CHAN=12 TEMP_FUNC=NTC10K3455UP2K USE_XOR USE_HSE=24 DUTY_SPUP=10 DUTY_RATE=5 FREQ_MIN=24 FREQ_MAX=24 TELEM_MODE=1 TELEM_POLES=2)
```

**v2:**

```
add_target(CRLS2 STM32G431 DEAD_TIME=160 COMP_MAP=312 HALL_MAP=0xB450 SENS_MAP=0xB2A6A7 VOLT_MUL=3130 TEMP_ADC2 TEMP_CHAN=12 TEMP_FUNC=NTC10K3455UP2K USE_XOR USE_HSE=24 DUTY_SPUP=10 DUTY_RATE=10 PROT_TEMP=90 FREQ_MIN=24 FREQ_MAX=24 TELEM_MODE=1 TELEM_POLES=2)
```

### Resources on Installation

[ESCape32's Installation Wiki Page](https://github.com/neoxic/ESCape32/wiki/Installation)

[Building ESCape32 on Windows](https://github.com/adrianblakey/slot-car-ecom/wiki/Building-ESCape32-on-Windows)

## Settings and Configuration

Under rapid deceleration on 50V input, the back electromotive force (BEMF) may exceed hardware voltage ratings. This was observed during no-load testing with a bench power supply. To mitigate this, limiting `duty_rate` to `0.5%/ms` is recommended.

> [!TIP]
> In real-world scenarios with a battery under load, this condition is less likely due to voltage sag and the battery acting as a load.

### Resources on Settings and Configuration

[ESCape32's Configuration Wiki Page](https://github.com/neoxic/ESCape32/wiki/Configuration)

[ESCape32's Settings Wiki Page](https://github.com/neoxic/ESCape32/wiki/Settings)
