[**Arm Examples**](README.md) » **Serial I/O Messages**

# Serial I/O Messages

On microcontrollers, serial I/O messages (printf-style output) can be sent to a host PC in several ways. The most widely used are semihosting, UART, and RTT. Each method has different trade-offs in terms of speed, intrusiveness, hardware requirements, and suitability for production code.


The Arm CMSIS Debugger extension supports (with pyOCD and Segger J-Link server) semihosting and RTT. For UART communication, a terminal program is used and no special debugger support is required. With Keil Studio, the Serial Monitor can be used to connect to all types of serial I/O messages. For more information, see [CMSIS-View documentation](https://arm-software.github.io/CMSIS-View/latest/index.html).


## Technology Overview

### Semihosting

Semihosting is a debugger-assisted I/O mechanism defined by Arm. The Cortex-M processor executes a special instruction (usually BKPT), which the debugger intercepts. The debugger then performs I/O operations on behalf of the target, such as printing text to the IDE console. For details, see [Arm Semihosting documentation](https://github.com/ARM-software/abi-aa/blob/main/semihosting/semihosting.rst#introduction).


With semihosting, the application calls a C library I/O function (e.g. _write, printf). Inside this library function, the CPU executes a breakpoint (BKPT) instruction. The Debugger halts the CPU, reads the memory that contains the message, the CPU resumes execution, and outputs this message to a TCP port (for display) or file (for logging).


Semihosting requires no hardware configuration and is easy to use for quick debugging. No extra pins are required and it is typically used in early in startup (even before clocks are set) of a hardware platform.  Due to the communication via a breakpoint, the communication is slow and intrusive (program execution is stopped). It is not recommended for use in production systems.


### UART (Serial Port)

UART is the traditional hardware serial interface. Data is transmitted via dedicated TX/RX pins typically to a serial adapter (USB-to-UART). The application code implements I/O retargeting to an UART peripheral.

The communication requires an UART peripheral with TX (and optionally RX) pins. As the communication requires no debugger capabilities, but just a simple terminal program, UART communication can be widely used during application development up to message logging in production hardware. It requires pins, clock setup, and hardware and the bandwidth is limited by the baudrate (typical 115200bps).

The implementation of UART communication can be tricky with an RTOS system that runs multiple threads and a blocking printf routine can affect real-time behavior of the software.

### RTT (Real-Time Transfer)

RTT is a memory-based debug communication mechanism developed by SEGGER. The application code implements I/O retargeting to RAM ring buffers on the target, and the debugger reads those buffers, without halting the CPU. The debugger periodically reads the RAM ring buffers via the SWD/JTAG interface. See [SEGGER RTT documentation](https://www.segger.com/products/debug-probes/j-link/technology/about-real-time-transfer/) for more information.

RTT requires a simple module that is linked into the firmware and is easy to use. No extra pins are required and it is easy to implement in a hardware platform. The communication speed depends on the debugger and the debug clock setup, but is typically faster than UART communication.

For the communication a debugger with RTT support is required. As the debugger performs a hand-shake protocol, RTT is not suitable for production hardware that should be used without debugger.

### Summary

- Semihosting: Best for quick debugging in early bring-up. Simple but intrusive and slow.
- UART: The most versatile and production-ready method. Requires hardware but works everywhere.
- RTT: Ideal real-time debug logging during development when a debugger is connected.

| Feature            | Semihosting  | UART                      | RTT  |
|:-------------------|:-------------|:--------------------------|:-----|
| Debugger required  | Yes          | No                        | Yes  |
| CPU halted         | Yes          | No                        | No   |
| Speed              | Slow         | Medium                    | Fast |
| Hardware pins      | None         | Yes (TX/RX)               | None |
| Real-time safe     | No           | Depends on implementation | Yes  |
| Production use     | No           | Yes                       | No   |
| Setup complexity   | Very low     | Medium                    | Low  |

## Usage

ToDo