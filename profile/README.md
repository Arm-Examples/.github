# About Arm Examples

The organization contains meaningful examples that can be used with various tools and IDEs. There are examples with different complexity levels available:
- Examples for [AVH](#avh-examples) demonstrate how to set up virtual simulation environments on your local machine and in the cloud.
- [Blinky](#blinky-examples) examples help you getting started with your hardware and help you to check the correct tools set up.
- [MQTT demos](#mqtt-examples) show how to connect to your favorite cloud service provider ([AWS](#aws), [Azure](#azure), [Google](#google), [Paho](#paho), and [Watson](#ibm-watson)).
- Various [other examples](#other-examples) demonstrating different aspects of embedded development.

## AVH examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [AVH-Jenkins](https://github.com/Arm-Examples/AVH-Jenkins) | AVH | Jenkins | Example of a Jenkins server running an ML application on Arm Virtual Hardware in the cloud. |
| [AVH-Virtual-Peripherals](https://github.com/Arm-Examples/AVH-Virtual-Peripherals) | AVH (VHT_MPS2_Cortex-M0) | AVH (locally) | Example of AVH models and their python extension implementing virtual peripherals. |
| [cloud_ci_demo_basic](https://github.com/Arm-Examples/cloud_ci_demo_basic) | AVH (V2M_MPS2_SSE_300) | AVH, µVision | Example of GitHub Actions together with a Docker image to run CI test automatically in the cloud. |
| [cloud_ci_demo_rv2](https://github.com/Arm-Examples/cloud_ci_demo_rv2) | AVH (V2M_MPS2_SSE_300) | AVH, µVision | Sophisticated example of GitHub Actions together with a Docker image to run CI test automatically in the cloud. |
| [Hello_AVH](https://github.com/Arm-Examples/Hello_AVH) | Arm Corstone-310 | CMSIS-Toolbox, AVH | Simple Hello World example. |

## Blinky examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [Blinky_AVH_uV](https://github.com/Arm-Examples/Blinky_AVH_uV) | Arm V2M-MPS3-SSE-300-FVP | CMSIS-Toolbox, µVision | This is a simple example to be used with the uVision debug learning path. |
| [Blinky_FRDM-K32L3A6_RTX](https://github.com/Arm-Examples/Blinky_FRDM-K32L3A6_RTX) | NXP FRDM-K32L3A6 | CMSIS-Toolbox, µVision | Example project using Keil RTX5 |
| [Blinky_IMXRT1050-EVKB_FreeRTOS](https://github.com/Arm-Examples/Blinky_IMXRT1050-EVKB_FreeRTOS) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using CMSIS-FreeRTOS |
| [Blinky_IMXRT1050-EVKB_RTX](https://github.com/Arm-Examples/Blinky_IMXRT1050-EVKB_RTX) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using Keil RTX5 |
| [Blinky_LPCXpresso55S69_RTX](https://github.com/Arm-Examples/Blinky_LPCXpresso55S69_RTX) | NXP LPCXpresso55S69 | CMSIS-Toolbox, µVision | Example project using Keil RTX5 |
| [Blinky_MIMXRT1064-EVK_RTX](https://github.com/Arm-Examples/Blinky_MIMXRT1064-EVK_RTX) | NXP MIMXRT1064-EVKB | CMSIS-Toolbox, µVision | Example project using CMSIS-FreeRTOS |
| [Blinky_STM32H745I-DISCO_FreeRTOS](https://github.com/Arm-Examples/Blinky_STM32H745I-DISCO_FreeRTOS) | STMicroelectronics STM32H745I-DISCO | CMSIS-Toolbox, µVision | Example project using CMSIS-FreeRTOS |
| [Blinky_STM32H745I-DISCO_RTX](https://github.com/Arm-Examples/Blinky_STM32H745I-DISCO_RTX) | STMicroelectronics STM32H745I-DISCO | CMSIS-Toolbox, µVision | Example project using Keil RTX5 |
| [RTX_Blinky](https://github.com/Arm-Examples/RTX_Blinky) | Arm V2M-MPS3-SSE-300-FVP, NXP FRDM-K32L3A6 | CMSIS-Toolbox | Example project using Keil RTX5 |

## MQTT examples

### AWS

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [AWS_MQTT_Demo_FRDM-K32L3A6_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/AWS_MQTT_Demo_FRDM-K32L3A6_ESP8266_WiFi_FreeRTOS) | NXP FRDM-K32L3A6 | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [AWS_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/AWS_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [AWS_MQTT_Demo_IMXRT1050-EVKB_MW-Network_ETH_RTX](https://github.com/Arm-Examples/AWS_MQTT_Demo_IMXRT1050-EVKB_MW-Network_ETH_RTX) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using wired Ethernet and Keil RTX5 |
| [AWS_MQTT_Demo_IMXRT1050-EVKB_WizFi360_WiFi_FreeRTOS](https://github.com/Arm-Examples/AWS_MQTT_Demo_IMXRT1050-EVKB_WizFi360_WiFi_FreeRTOS) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the WizFi360 shield and CMSIS-FreeRTOS |
| [AWS_MQTT_Demo_LPCXpresso55S69_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/AWS_MQTT_Demo_LPCXpresso55S69_ESP8266_WiFi_FreeRTOS) | NXP LPCXpresso55S69 | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [AWS_MQTT_Demo_MIMXRT1064-EVK_ESP8266_WiFi_RTX](https://github.com/Arm-Examples/AWS_MQTT_Demo_MIMXRT1064-EVK_ESP8266_WiFi_RTX) | NXP MIMXRT1064-EVK | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [AWS_MQTT_MutualAuth_Demo](https://github.com/Arm-Examples/AWS_MQTT_MutualAuth_Demo) | NXP i.MXRT1050-EVKB, STMicroelectronics B-U585I-IOT02A, Arm Corstone-300  | CMSIS-Toolbox | Example project using CMSIS-FreeRTOS |

### Azure

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [Azure_MQTT_Demo_FRDM-K32L3A6_ESP8266_WiFi_RTX](https://github.com/Arm-Examples/Azure_MQTT_Demo_FRDM-K32L3A6_ESP8266_WiFi_RTX) | NXP FRDM-K32L3A6 | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and Keil RTX5 |
| [Azure_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/Azure_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [Azure_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_RTX](https://github.com/Arm-Examples/Azure_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_RTX) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and Keil RTX5 |
| [Azure_MQTT_Demo_IMXRT1050-EVKB_WizFi360_WiFi_RTX](https://github.com/Arm-Examples/Azure_MQTT_Demo_IMXRT1050-EVKB_WizFi360_WiFi_RTX) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the WizFi360 WiFi shield and Keil RTX5 |
| [Azure_MQTT_Demo_LPCXpresso55S69_ESP8266_WiFi_RTX](https://github.com/Arm-Examples/Azure_MQTT_Demo_LPCXpresso55S69_ESP8266_WiFi_RTX) | NXP LPCXpresso55S69 | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and Keil RTX5 |
| [Azure_MQTT_Demo_MIMXRT1064-EVK_ESP8266_WiFi_RTX](https://github.com/Arm-Examples/Azure_MQTT_Demo_MIMXRT1064-EVK_ESP8266_WiFi_RTX) | NXP MIMXRT1064-EVK | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and Keil RTX5 |

### Google

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [Google_MQTT_Demo_FRDM-K32L3A6_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/Google_MQTT_Demo_FRDM-K32L3A6_ESP8266_WiFi_FreeRTOS) | NXP FRDM-K32L3A6 | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [Google_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/Google_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [Google_MQTT_Demo_IMXRT1050-EVKB_lwIP_ETH_RTX](https://github.com/Arm-Examples/Google_MQTT_Demo_IMXRT1050-EVKB_lwIP_ETH_RTX) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using wired Ethernet, lwIP stack, and Keil RTX5 |
| [Google_MQTT_Demo_LPCXpresso55S69_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/Google_MQTT_Demo_LPCXpresso55S69_ESP8266_WiFi_FreeRTOS) | NXP LPCXpresso55S69 | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [Google_MQTT_Demo_MIMXRT1064-EVK_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/Google_MQTT_Demo_MIMXRT1064-EVK_ESP8266_WiFi_FreeRTOS) | NXP MIMXRT1064-EVK | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |

### Paho

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [Paho_MQTT_Demo_FRDM-K32L3A6_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/Paho_MQTT_Demo_FRDM-K32L3A6_ESP8266_WiFi_FreeRTOS) | NXP FRDM-K32L3A6 | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [Paho_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/Paho_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [Paho_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_RTX](https://github.com/Arm-Examples/Paho_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_RTX) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and Keil RTX5 |
| [Paho_MQTT_Demo_LPCXpresso55S69_ESP8266_WiFi_RTX](https://github.com/Arm-Examples/Paho_MQTT_Demo_LPCXpresso55S69_ESP8266_WiFi_RTX) | NXP LPCXpresso55S69 | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and Kiel RTX5 |
| [Paho_MQTT_Demo_MIMXRT1064-EVK_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/Paho_MQTT_Demo_MIMXRT1064-EVK_ESP8266_WiFi_FreeRTOS) | NXP MIMXRT1064-EVK | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |

### IBM Watson

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [Watson_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS](https://github.com/Arm-Examples/Watson_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_FreeRTOS) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and CMSIS-FreeRTOS |
| [Watson_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_RTX](https://github.com/Arm-Examples/Watson_MQTT_Demo_IMXRT1050-EVKB_ESP8266_WiFi_RTX) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the SparkFun ESP8266 WiFi shield and Keil RTX5 |
| [Watson_MQTT_Demo_IMXRT1050-EVKB_WizFi360_WiFi_FreeRTOS](https://github.com/Arm-Examples/Watson_MQTT_Demo_IMXRT1050-EVKB_WizFi360_WiFi_FreeRTOS) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the WizFi360 WiFi shield and CMSIS-FreeRTOS |
| [Watson_MQTT_Demo_IMXRT1050-EVKB_WizFi360_WiFi_RTX](https://github.com/Arm-Examples/Watson_MQTT_Demo_IMXRT1050-EVKB_WizFi360_WiFi_RTX) | NXP i.MXRT1050-EVKB | CMSIS-Toolbox, µVision | Example project using the WizFi360 WiFi shield and Keil RTX5 |
| [Watson_MQTT_Demo_MIMXRT1064-EVK_MW-Network_ETH_RTX](https://github.com/Arm-Examples/Watson_MQTT_Demo_MIMXRT1064-EVK_MW-Network_ETH_RTX) | NXP MIMXRT1064-EVKB | CMSIS-Toolbox, µVision | Example project using wired Ethernet, MDK-Middleware stack, and Keil RTX5 |

## Other examples

| Repository | Hardware used | Tool/IDE | Notes |
|------------|---------------|----------|-------|
| [CMSIS-Stream-PoC](https://github.com/Arm-Examples/CMSIS-Stream-PoC) | NXP LPC1700 | µVision | Example project showing the usage of the CMSIS-Stream software component. |
| [keil-studio-get-started](https://github.com/Arm-Examples/keil-studio-get-started) | Arm VHT_MPS2_Cortex-M3 | CMSIS-Toolbox, Keil Studio (VS Code Extensions) | Get started example for use in Keil Studio. |
| [KSC_Debug_FRDM-K32L3A6](https://github.com/Arm-Examples/KSC_Debug_FRDM-K32L3A6) | NXP FRDM-K32L3A6 | CMSIS-Toolbox, Keil Studio Cloud | Simple application to test KSC debug functionality. |
| [KSC_Debug_LPCXpresso55S69](https://github.com/Arm-Examples/KSC_Debug_LPCXpresso55S69) | NXP LPCXpresso55S69 | CMSIS-Toolbox, Keil Studio Cloud | Simple application to test KSC debug functionality. |
| [KSC_Debug_MIMXRT1064-EVK](https://github.com/Arm-Examples/KSC_Debug_MIMXRT1064-EVK) | NXP MIMXRT1064-EVK | CMSIS-Toolbox, Keil Studio Cloud | Simple application to test KSC debug functionality. |
| [MDK-MW-PoC](https://github.com/Arm-Examples/MDK-MW-PoC) |STMicroelectronics STM32F429I-Discovery | CMSIS-Toolbox, Keil Studio | MDK-Middleware application using the csloution project format. |
| [mlek-cmsis-pack-examples](https://github.com/Arm-Examples/mlek-cmsis-pack-examples) | Various | CMSIS-Toolbox, Keil Studio |  Machine Learning (ML) examples using the ML Embedded Evaluation Kit. |
