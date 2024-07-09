# About Arm Examples

The organization contains meaningful examples that can be used with various tools and IDEs. There are examples with different complexity levels available:
- [CMSIS-Toolbox examples](#cmsis-toolbox-2-examples) help you getting started with your hardware and help you to check the correct tools set up.
- Examples for [AVH-FVP](#avh-fvpexamples) demonstrate how to set up virtual simulation environments on your local machine and in the cloud.
- Various [other examples](#other-examples) demonstrating different aspects of embedded development.

## CMSIS-Toolbox examples

### Hello world examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [Hello_B-U585I-IOT02A](https://github.com/Arm-Examples/Hello_B-U585I-IOT02A) | STMicroelectronics B-U585I-IOT02A | CMSIS-Toolbox | Prints "Hello World, 0..9" on the serial console |
| [Hello_FRDM-K32L3A6](https://github.com/Arm-Examples/Hello_FRDM-K32L3A6) | NXP FRDM-K32L3A6 | CMSIS-Toolbox | Prints "Hello World, 0..9" on the serial console |
| [Hello_IMXRT1050-EVKB](https://github.com/Arm-Examples/Hello_IMXRT1050-EVKB)   | NXP IMXRT1050-EVKB | CMSIS-Toolbox | Prints "Hello World, 0..9" on the serial console |
| [Hello_LPCXpresso55S69](https://github.com/Arm-Examples/Hello_LPCXpresso55S69) | NXP LPCXpresso55S69 | CMSIS-Toolbox | Prints "Hello World, 0..9" on the serial console |
| [Hello_MIMXRT1060-EVKB](https://github.com/Arm-Examples/Hello_MIMXRT1060-EVKB) | NXP MIMXRT1060-EVKB | CMSIS-Toolbox | Prints "Hello World, 0..9" on the serial console |
| [Hello_MIMXRT1064-EVK](https://github.com/Arm-Examples/Hello_MIMXRT1064-EVK) | NXP MIMXRT1064-EVK | CMSIS-Toolbox | Prints "Hello World, 0..9" on the serial console |
| [Hello_NUCLEO-G474RE](https://github.com/Arm-Examples/Hello_NUCLEO-G474RE) | STMicroelectronics NUCLEO-G474RE | CMSIS-Toolbox | Prints "Hello World, 0..9" on the serial console |
| [Hello_V2M-MPS3-SSE-300-FVP](https://github.com/Arm-Examples/Hello_V2M-MPS3-SSE-300-FVP) | Arm Corstone-300 | CMSIS-Toolbox | Prints "Hello World, 0..9" on the serial console |

### Blinky examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [Blinky_FRDM-K32L3A6](https://github.com/Arm-Examples/Blinky_FRDM-K32L3A6) | NXP Blinky_FRDM-K32L3A6 | CMSIS-Toolbox | Blinks an LED, changes frequency after button press |
| [Blinky_NUCLEO-G0B1RE](https://github.com/Arm-Examples/Blinky_NUCLEO-G0B1RE) | STMicroelectronics NUCLEO-G0B1RE | CMSIS-Toolbox | Blinks an LED, changes frequency after button press |
| [Blinky_NUCLEO-F756ZG](https://github.com/Arm-Examples/Blinky_NUCLEO-F756ZG) | STMicroelectronics NUCLEO-F756ZG | CMSIS-Toolbox | Blinks an LED, changes frequency after button press |

### Machine learning (ML) examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [mlek-cmsis-pack-examples](https://github.com/Arm-Examples/mlek-cmsis-pack-examples) | Various | CMSIS-Toolbox, Keil Studio |  Machine Learning (ML) examples using the ML Embedded Evaluation Kit. |

## AVH-FVP examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [AVH_CI_Template](https://github.com/Arm-Examples/AVH_CI_Template) | AVH (FVP_MPS2_Cortex-M3) | CMSIS-Toolbox, AVH | CI Template for unit test automation |
| [AVH-Virtual-Peripherals](https://github.com/Arm-Examples/AVH-Virtual-Peripherals) | AVH (FVP_MPS2_Cortex-M0) | AVH (locally) | Example of AVH models and their python extension implementing virtual peripherals. |
| [Hello_AVH](https://github.com/Arm-Examples/Hello_AVH) | Arm Corstone-310 | CMSIS-Toolbox, AVH | Simple Hello World example. |

## Other examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [CMSIS-Stream-PoC](https://github.com/Arm-Examples/CMSIS-Stream-PoC) | NXP LPC1700 | µVision | Example project showing the usage of the CMSIS-Stream software component. |
| [keil-studio-get-started](https://github.com/Arm-Examples/keil-studio-get-started) | AVH (FVP_MPS2_Cortex-M3) | CMSIS-Toolbox, Keil Studio (VS Code Extensions) | Get started example for use in Keil Studio. |
| [MDK-MW-PoC](https://github.com/Arm-Examples/MDK-MW-PoC) |STMicroelectronics STM32F429I-Discovery | CMSIS-Toolbox, Keil Studio | MDK-Middleware application using the csloution project format. |
| [Using CMSIS-View and CMSIS-Compiler](https://github.com/Arm-Examples/CMSIS-View_and_CMSIS-Compiler) |Various | µVision | Example projects from the CMSIS v6 webinar about CMSIS-View and CMSIS-Compiler. |
| [AVH FVPs on MacOS](https://github.com/Arm-Examples/fvps-on-mac) | Mac | All | This repo contains a set of scripts that allow you to run AVH FVPs on MacOS using Docker. |
