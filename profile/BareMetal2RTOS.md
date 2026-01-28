[**Arm Examples**](https://github.com/Arm-Examples/) » **Bare-Metal or RTOS**

# Bare-Metal or RTOS

Keil Studio is designed for all types of embedded projects, ranging from bare-metal firmware to complex RTOS-based systems. It provides direct hardware access, kernel awareness for supported RTOSes, and software component viewers for middleware and system services.

## Bare-Metal Systems

One of the first architectural decisions in an embedded project is whether an RTOS is required. An RTOS becomes appropriate when an application must handle multiple concurrent activities, enforce task priorities or deadlines, or manage system complexity that no longer fits cleanly into a superloop architecture. Maintainability and scalability are key factors. As systems evolve, an RTOS provides structure that prevents ad-hoc scheduling logic from becoming fragile and difficult to maintain. If none of these factors exist, a bare-metal approach remains the simplest and most deterministic option.

Bare-metal designs rely on a [superloop](https://arm-software.github.io/CMSIS_6/latest/Core/using_pg.html#using_basic) combined with interrupts, offering unrestricted hardware access and maximum timing predictability with minimal overhead. This approach is well suited to simple applications, highly resource-constrained microcontrollers, or latency-critical control paths. However, bare-metal systems scale poorly. When features grow, developers must manually manage scheduling, synchronization, and state transitions, which quickly becomes error-prone and hard to maintain. For this reason, bare-metal is best reserved for narrowly focused systems such as sensors, simple control loops, or bootloaders.

> **TIP**
>
> - Start a bare-metal application in Keil Studio *Create a New Solution* using a *Template*; see [Keil Studio User's Guide - Work with CMSIS solutions](https://mdk-packs.github.io/vscode-cmsis-solution-docs/create_app.html).

## Keil RTX (CMSIS-RTOS2 Kernel)

[Keil RTX](https://www.keil.arm.com/packs/cmsis-rtx-arm) is Arm’s reference RTOS kernel implementation for CMSIS-RTOS2 and is designed with strict real-time and safety requirements in mind. A key architectural property of RTX is that it never globally blocks interrupts to implement scheduling or synchronization. Instead, it relies on bounded critical sections, priority-aware mechanisms, and Arm Cortex-M architectural features to maintain kernel consistency while preserving interrupt responsiveness.

As a result, high-priority interrupts always execute with predictable latency, independent of RTOS activity. Communication between ISRs and threads is explicitly defined through CMSIS-RTOS2 APIs that are safe to call from interrupt context, ensuring that time-critical interrupt handling remains separate from deferred thread-level processing. This behavior makes RTX particularly suitable for safety-critical and real-time control systems where interrupt masking must be minimized or avoided altogether. For [safety-critical applications](#functional-safety), the [MDK-Professional edition](https://www.keil.arm.com/keil-mdk/) includes FuSa RTS, a TÜV certified version of Keil RTX.

> **TIP**
>
> - The Blinky example is a configured Keil RTX application stub; see [Keil Studio User's Guide - Work with CMSIS solutions](https://mdk-packs.github.io/vscode-cmsis-solution-docs/create_app.html) or [this video](https://armkeil.blob.core.windows.net/developer/Files/videos/KeilStudio/20250729_Working_with_STM32_devices.mp4?#t=00:51).

## FreeRTOS

[FreeRTOS](https://www.keil.arm.com/packs/cmsis-freertos-arm) is a widely used lightweight RTOS kernel that provides a scheduler and basic inter-process communication primitives, enabling multitasking without imposing a rigid system architecture. This flexibility makes it popular in small-to-medium systems where developers want RTOS functionality with minimal abstraction overhead.

Internally, FreeRTOS may temporarily mask interrupts as part of its kernel operation. Interrupts at or below a configured priority level are deferred while kernel data structures are updated. While this behavior is well-documented, it introduces interrupt latency that depends on kernel activity and requires careful interrupt priority configuration. Application code written against the native FreeRTOS API is also not inherently portable across RTOS implementations.

Using the standardized CMSIS-RTOS2 API layer decouples application code from the underlying kernel by providing a common interface for threads, synchronization primitives, and timers. CMSIS-RTOS2 is used natively by Keil RTX and FuSa RTS and is also supported by FreeRTOS and Zephyr via wrapper layers. This abstraction is particularly valuable in projects that prioritize portability, long-term maintainability, or safety certification.

> **TIP**
>
> - Install the [CMSIS-FreeRTOS Pack](https://www.keil.arm.com/packs/cmsis-freertos-arm) to get access to [FreeRTOS example projects](https://arm-software.github.io/CMSIS-FreeRTOS/main/page_example_projects.html).

## Zephyr

Zephyr is a full embedded operating system intended for large, long-lived products and multi-developer teams. In addition to an RTOS kernel, it provides standardized drivers, networking stacks, storage support, and power management, all integrated through a strong build and configuration system. Zephyr enforces architectural structure through mechanisms such as Devicetree, improving scalability and portability across hardware platforms.

This level of integration comes at the cost of increased footprint and a steeper learning curve. Direct hardware and interrupt access is still possible but is generally discouraged in favor of Zephyr’s driver and subsystem models. As a result, Zephyr is best suited for complex products rather than small, tightly hardware-coupled firmware.

> **TIP**
>
> - For detailed instructions, see the [Keil Studio User's Guide - Work with Zephyr applications](https://mdk-packs.github.io/vscode-cmsis-solution-docs/zephyr.html) or clone [github.com/Arm-Examples/cmsis-zephyr](https://github.com/Arm-Examples/cmsis-zephyr).

## Choosing the Right Option

Selecting between bare-metal, Keil RTX, FreeRTOS, and Zephyr depends on system complexity, longevity, and non-functional requirements. Bare-metal designs favor simplicity, minimal overhead, and unrestricted hardware control. FreeRTOS and Keil RTX provide a middle ground, offering multitasking with relatively low overhead. Zephyr targets product-scale systems that benefit from a rich ecosystem and enforced structure.

When portability across RTOS kernels or safety standards is a primary concern, CMSIS-RTOS2 combined with an appropriate kernel provides a clean abstraction that reduces long-term risk.

## Further Reading

- [Shawn Hymel – When to Use an RTOS](https://shawnhymel.com/2928/when-to-use-an-rtos-an-important-decision-for-embedded-projects/)
- [Shawn Hymel – Zephyr vs FreeRTOS](https://shawnhymel.com/3106/zephyr-vs-freertos-how-to-choose-the-right-rtos-for-your-embedded-project/)
- [Nathan Jones - You Don't Need an RTOS](https://www.embeddedrelated.com/showarticle/1636.php)
- [Arm – CMSIS-RTOS2 Overview](https://arm-software.github.io/CMSIS_5/RTOS2/html/index.html)
