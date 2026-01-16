# Examples for Embedded Developers

Arm-Examples contains ready-to-run embedded projects showcasing RTOS, machine learning, functional safety, and CI/CD automation across diverse Arm-based hardware platforms. These examples leverage Keil Studio, CMSIS-Toolbox, and Arm FVP models with various compilers (Arm Compiler 6, GCC, LLVM) enabling both desktop and cloud-based CI/CD workflows with physical hardware and simulation models.

<table style="border: none; margin-left: 0; padding-left: 0;">
<tr>
<td style="border: none; padding-left: 0;"><a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250715_Introduction_to_Keil_Studio.mp4" target="_blank"><img src="IntroVideo.png" alt="Introduction Video" style="width: 318px; height: 185px;"></a></td>
<td style="border: none; ">Keil Studio is Arm's new IDE for embedded development directly in Visual Studio Code and the successor to the µVision IDE. <b><a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250715_Introduction_to_Keil_Studio.mp4" target="_blank">Watch this video to learn more...</a></b></td>
</tr>
</table>

## RTOS Applications

Keil Studio is designed for all types of embedded projects, ranging from bare-metal firmware to complex RTOS-based systems. How to choose the right option: bare-metal, Keil RTX, FreeRTOS, and Zephyr? [**Learn more ...**](BareMetal2RTOS.md)

| Repository | Hardware | Content |
|------------|----------|---------|
| [Hello_NUCLEO-G474RE](https://github.com/Arm-Examples/Hello_NUCLEO-G474RE) | ST NUCLEO-G474RE | Keil RTX configuration; prints "Hello World, 0..9" on the serial console. |
| [Middleware_USB_FS](https://github.com/Arm-Examples/cmsis-mlek-examples) | Alif Ensemble E7 | Pre-configured machine learning (ML) projects using the ML Embedded Evaluation Kit. <a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250812_Multicore_Alif.mp4" target="_blank">Watch the related webinar</a>. |
| [CMSIS-Zephyr](https://github.com/Arm-Examples/SDS-Examples) | Various | Examples showing the usage of the Synchronous Data Streaming (SDS) Framework. <a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250916_SDS_Webinar.mp4" target="_blank">Watch the related webinar</a>. |

## Edge AI and Machine Learning

<table style="border: none; margin-left: 0; padding-left: 0;">
<tr>
<td style="border: none; padding-left: 0;"><a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250812_Multicore_Alif.mp4?#t=07:22" target="_blank"><img src="ML_Video.png" alt="ML Video" style="width: 318px; height: 170px;"></a></td>
<td style="border: none; ">Comprehensive machine learning capabilities are available with ML Evaluation Kit (MLEK), Synchronous Data Streaming (SDS) Framework, LiteRT (TensorFlow), and Executourch that utilizes CMSIS-NN (for Cortex-M) or Vela (for Ethos-U). <b><a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250812_Multicore_Alif.mp4?#t=07:22" target="_blank">Watch this video to learn more...</a></b></td>
</tr>
</table>
Comprehensive machine learning capabilities are available with ML Evaluation Kit (MLEK), Synchronous Data Streaming (SDS) Framework, LiteRT (TensorFlow), and Executourch that utilizes CMSIS-NN (for Cortex-M) or Vela (for Ethos-U).  <!-- ToDo [**Learn more ...**](x.md) -->

| Repository | Hardware | Content |
|------------|----------|---------|
| [CMSIS-MLEK-Examples](https://github.com/Arm-Examples/cmsis-mlek-examples) | Alif Ensemble E7 |  Pre-configured machine learning (ML) projects using the ML Embedded Evaluation Kit. <a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250812_Multicore_Alif.mp4" target="_blank">Watch the related webinar</a>. |
| [SDS-Examples](https://github.com/Arm-Examples/SDS-Examples) | Various | Examples showing the usage of the Synchronous Data Streaming (SDS) Framework. <a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250916_SDS_Webinar.mp4" target="_blank">Watch the related webinar</a>. |

## Functional Safety (FuSa RTS)

| Repository | Hardware |  Content |
|------------|----------|----------|
| [Safety-Example-Infineon-T2G](https://github.com/Arm-Examples/Safety-Example-Infineon-T2G) | Infineon Traveo T2G | [Fusa RTS](https://developer.arm.com/Tools%20and%20Software/Keil%20MDK/FuSa%20Run-Time%20System) traffic light example, CMSIS-Driver development and verification. <a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250930_FuSa_TRAVEO.mp4" target="_blank">Watch the related webinar</a>. |
| [Safety-Example-STM32](https://github.com/Arm-Examples/Safety-Example-STM32) | STM32H5 | [Fusa RTS](https://developer.arm.com/Tools%20and%20Software/Keil%20MDK/FuSa%20Run-Time%20System) traffic light example. <a href="https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250930_FuSa_TRAVEO.mp4" target="_blank">Watch the related webinar</a>. |

## CI/CD Automation (GitHub Actions)




## Related

- Software Packs maintained by Arm
- [Other Examples](ListExamples.md)
