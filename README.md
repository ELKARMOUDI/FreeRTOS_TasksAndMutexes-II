# FreeRTOS Threads & Mutexes on STM32F411-NUCLEO / Tera Term - II

![FreeRTOS](https://img.shields.io/badge/FreeRTOS-10.4.3-green)
![STM32](https://img.shields.io/badge/STM32F411-84MHz-03234B?logo=stmicroelectronics)
![UART](https://img.shields.io/badge/UART-115200_8N1-blueviolet)

<img src="https://github.com/user-attachments/assets/1fe6ecbb-4a6f-4426-a85d-bc3d0b704bda" width="650" alt="D36BCBE0-D2CC-4BE4-A836-C7B4ACF4E81D_1_105_c">

STM32F411 FreeRTOS demo featuring mutex-protected UART communication with Tera Term, including 3 threads and GPIO control.
## Features
- 🧵 **3 FreeRTOS Threads** with execution profiling
- 🔒 **Mutex-Protected UART** - Thread-safe serial communication
- 📡 **Tera Term Integration** - Ready for debug output
- 💡 **Hardware Feedback** - Onboard LED (PA5) and Button (PC13)
- ⚡ **84MHz Clock** - Optimized performance via HSI/PLL

## Hardware Setup
| Component | NUCLEO-F411RE Connection |
|-----------|--------------------------|
| USART2_TX | PA2 (ST-LINK VCP) |
| USART2_RX | PA3 (ST-LINK VCP) |
| LED (LD2) | PA5 (Onboard) |
| User Button | PC13 (Onboard) |

## Code Architecture
```c
// Thread Workflow:
Thread1 -> [Take Mutex] -> UART_Transmit() -> [Give Mutex]
Thread2 -> [Take Mutex] -> UART_Transmit() -> [Give Mutex]
DefaultThread -> System Monitoring
