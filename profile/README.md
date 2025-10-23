# About Arm Examples

The organization contains meaningful examples that can be used with various tools and IDEs.

## Keil MDK version 6 examples

| Repository | Hardware used | Tool/IDE | Content |
|------------|---------------|----------|-------|
| [cmsis-mlek-examples](https://github.com/Arm-Examples/cmsis-mlek-examples) | Alif Ensemble E7 | CMSIS-Toolbox, Keil Studio |  Pre-configured machine learning (ML) projects using the ML Embedded Evaluation Kit. [Watch the related webinar](https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250812_Multicore_Alif.mp4). |
| [cmsis-mlek](https://github.com/Arm-Examples/cmsis-mlek) | Various | CMSIS-Toolbox, Keil Studio |  CMSIS-Pack repository with ML template projects for various models and devices. [Watch the related webinar](https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250812_Multicore_Alif.mp4). |
| [SDS-Examples](https://github.com/Arm-Examples/SDS-Examples) | Various | CMSIS-Toolbox, Keil Studio | Examples showing the usage of the Synchronous Data Streaming (SDS) Framework. [Watch the related webinar](https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250916_SDS_Webinar.mp4). |
| [SDS-Framework](https://github.com/Arm-Software/SDS-Framework) | Various | CMSIS-Toolbox, Keil Studio | Framework software with template applications that can be reused on different hardware. [Watch the related webinar](https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250916_SDS_Webinar.mp4). |
| [Safety-Example-Infineon-T2G](https://github.com/Arm-Examples/Safety-Example-Infineon-T2G) | Various | CMSIS-Toolbox, Keil Studio | Traffic light example and CMSIS-Driver verification project. [Watch the related webinar](https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250930_FuSa_TRAVEO.mp4). |
| [Safety-Example-STM32](https://github.com/Arm-Examples/Safety-Example-STM32) | Various | CMSIS-Toolbox, Keil Studio | Traffic light example using safety features of Keil RTX5. [Watch the related webinar](https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250930_FuSa_TRAVEO.mp4). |
| [AVH](https://github.com/Arm-Software/AVH) | N/A | N/A | Documentation and virtual streaming interface API. |
| [AVH-MLOps](https://github.com/Arm-Software/AVH-MLOps) | Various Arm FVPs | CMSIS-Toolbox, Keil Studio, AVH | Foundational components for MLOps systems, such as Docker container, GitHUb Actions, and basic examples. |
| [AVH-VSI](https://github.com/Arm-Examples/AVH-VSI) | Arm Corstone-310 | CMSIS-Toolbox, Keil Studio, AVH | Examples demonstrating the use of virtual peripherals on Arm FVPs. |
| [AVH-Hello](https://github.com/Arm-Examples/AVH-Hello) | Multiple AVH FVPs | CMSIS-Toolbox, AVH | CI project with a test matrix that uses GitHub Actions on a GitHub-hosted runner. |

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

### Blinky examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [Blinky_FRDM-K32L3A6](https://github.com/Arm-Examples/Blinky_FRDM-K32L3A6) | NXP Blinky_FRDM-K32L3A6 | CMSIS-Toolbox | Blinks an LED, changes frequency after button press |

### Machine learning (ML) examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [mlek-cmsis-pack-examples](https://github.com/Arm-Examples/mlek-cmsis-pack-examples) | Various | CMSIS-Toolbox, Keil Studio |  Machine Learning (ML) examples using the ML Embedded Evaluation Kit. |

## AVH-FVP examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [AVH_CI_Template](https://github.com/Arm-Examples/AVH_CI_Template) | AVH (FVP_MPS2_Cortex-M3) | CMSIS-Toolbox, AVH | CI Template for unit test automation |
| [AVH-Virtual-Peripherals](https://github.com/Arm-Examples/AVH-Virtual-Peripherals) | AVH (FVP_MPS2_Cortex-M0) | AVH (locally) | Example of AVH models and their python extension implementing virtual peripherals. |
| [AVH-VSI](https://github.com/Arm-Examples/AVH-VSI) | Arm Corstone-310 | CMSIS-Toolbox, AVH | Simple Hello World example using VSI interfaces. |
| [AVH-Hello](https://github.com/Arm-Examples/AVH-Hello) | Multiple AVH FVPs | CMSIS-Toolbox, AVH | CI project with a test matrix that uses GitHub Actions on a GitHub-hosted runner. |
| [AWS_MQTT_Demo](https://github.com/Arm-Examples/AWS_MQTT_Demo) | Arm Corstone-300 | CMSIS-Toolbox, AVH | CI project that connects to AWS MQTT broker; can be retarget to physical boards using layers. |

## Other examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [CMSIS-Stream-PoC](https://github.com/Arm-Examples/CMSIS-Stream-PoC) | NXP LPC1700 | µVision | Example project showing the usage of the CMSIS-Stream software component. |
| [keil-studio-get-started](https://github.com/Arm-Examples/keil-studio-get-started) | AVH (FVP_MPS2_Cortex-M3) | CMSIS-Toolbox, Keil Studio (VS Code Extensions) | Get started example for use in Keil Studio. |
| [MDK-MW-PoC](https://github.com/Arm-Examples/MDK-MW-PoC) |STMicroelectronics STM32F429I-Discovery | CMSIS-Toolbox, Keil Studio | MDK-Middleware application using the csloution project format. |
| [Using CMSIS-View and CMSIS-Compiler](https://github.com/Arm-Examples/CMSIS-View_and_CMSIS-Compiler) |Various | µVision | Example projects from the CMSIS v6 webinar about CMSIS-View and CMSIS-Compiler. |
| [AVH FVPs on MacOS](https://github.com/Arm-Examples/fvps-on-mac) | Mac | All | This repo contains a set of scripts that allow you to run AVH FVPs on MacOS using Docker. |
