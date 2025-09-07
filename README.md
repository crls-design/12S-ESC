# 12S ESC

This repository provides a low-cost, open-source design for a 12S Electronic Speed Controller (ESC) geared towards heavy-lift multirotor applications. It is designed to work with [ESCape32](https://github.com/neoxic/ESCape32), an open-source 32-bit ESC firmware.

## Design Philosophy

The goal of this ESC design is to maximize the performance-to-cost ratio by utilizing readily available components and open-source firmware while maintaining electrical and thermal characteristics that meet or exceed those of commercial ESCs in the same class.

This project aims to offer a competitive alternative to proprietary ESCs used in drones, robotics, and other high-power applications.

## Specifications

- STM32G431 processor
- 24MHz HSE crystal resonator
- 12S input (up to 50.4V)
- Full support for [ESCape32](https://github.com/neoxic/ESCape32)

> [!NOTE]  
> Although these are designed for 12S, the actual hardware is rated for 100V which is nearly double.

## Gallery

<p align="center">
    <img src="./images/v1 raw.jpg" height="280">
    <img src="./images/v1 bypassed.jpg" height="280">
    <img src="./images/v1 explosion.jpg" height="280">
    </br>
    <img src="./images/v2 raw.jpg" height="280">
</p>

## Getting Started

See [Getting Started](./docs/getting-started.md) for instructions on flashing and setup.
