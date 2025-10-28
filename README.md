# LED-BLINK
# 💡 Experiment 01 – Interfacing a Digital Output (LED) with ARM Development Board

### 🎯 **Aim**
To interface a digital output (LED) to an ARM development board and write a blink code.

---

### ⚙️ **Components Required**
- STM32CubeIDE  
- NUCLEO ARM Development Board  

---

### 🧠 **Theory**

**ARM (Advanced RISC Machine)** is a 32-bit processor architecture developed by ARM Holdings. It is widely used in embedded systems and SoC (System-on-Chip) products. Many semiconductor companies like Samsung, Atmel, and Texas Instruments license ARM architecture to design their own SoCs.
### 🧩 **What is an ARM7 Processor?**
The **ARM7 processor** is commonly used in embedded system applications. It provides a balance between the classic ARM architecture and the newer Cortex series, offering an excellent platform for both hardware and software development.
### 🔍 **LPC2148 Microcontroller**
The **LPC2148**, developed by NXP Semiconductors (Philips), is a 16/32-bit ARM7-based microcontroller featuring a wide range of peripherals.
#### **Key Features**
- 16/32-bit ARM7TDMI-S core in LQFP64 package  
- On-chip **Flash memory**: 32 KB – 512 KB  
- On-chip **SRAM**: 8 KB – 40 KB  
- **ISP/IAP** via on-chip bootloader  
- **Embedded ICE-RT** and **Real Monitor** for real-time debugging  
- **USB 2.0** full-speed device controller with 2 KB endpoint RAM  
- **10-bit ADC** (6 or 14 channels, 2.44 μs conversion time)  
- **10-bit DAC** for analog output  
- **Timers:** Two 32-bit timers, watchdog, and PWM unit  
- **RTC** with 32 kHz clock input  
- **UARTs (2x), I²C (2x)** up to 400 kbit/s  
- **5V-tolerant GPIOs**, 21 external interrupt pins  
- **Max CPU Clock:** 60 MHz using on-chip PLL (lock time 100 µs)  
- **Crystal Frequency:** 1 MHz – 25 MHz  
- **Power modes:** Idle and Power-down with peripheral clock scaling  

---

### 🧭 **Procedure**

1. Open **STM32CubeIDE**.
  <img width="1919" height="1199" alt="Screenshot 2025-10-28 202526" src="https://github.com/user-attachments/assets/51dd4e79-506b-4be6-a1ba-e58ce5fe5b04" />

2. Click **File → New STM32 Project**.
   <img width="1919" height="1199" alt="Screenshot 2025-10-28 203225" src="https://github.com/user-attachments/assets/723904bc-55fe-4ea9-818a-bb0fabffb94b" />

<img width="1919" height="1199" alt="Screenshot 2025-10-28 203837" src="https://github.com/user-attachments/assets/94cef2c8-91ba-488d-bb94-4924303b2836" />

3. Select the **target microcontroller** or board and click **Next**.
   <img width="1919" height="1199" alt="Screenshot 2025-10-28 203723" src="https://github.com/user-attachments/assets/109bd30f-4806-455b-b1c8-2631166f3efc" />



4. Name the project.
   <img width="1918" height="593" alt="image" src="https://github.com/user-attachments/assets/35b39b05-f754-475b-982a-6038fbb82d8e" />

5. The corresponding `.ioc` file will be generated automatically.
 <img width="1918" height="1199" alt="Screenshot 2025-10-28 203910" src="https://github.com/user-attachments/assets/c682290e-b856-4d8f-8d21-ff1ee7180abf" />
 <img width="1736" height="1199" alt="Screenshot 2025-10-28 204329" src="https://github.com/user-attachments/assets/2da585be-047f-4e80-859e-fbdd5586d0b8" />
 
6.Configure the pins as GPIO(INPUT/OUTPUT),USART,etc as needed.
<img width="1919" height="1199" alt="Screenshot 2025-10-28 204350" src="https://github.com/user-attachments/assets/0a62f6e1-f224-4ecb-8e2e-e726e3cb4f20" />



7. Save the configuration (`Ctrl + S`) – the base C program will be generated automatically.
   <img width="1919" height="1199" alt="Screenshot 2025-10-28 204610" src="https://github.com/user-attachments/assets/f5565dff-516c-4aef-ba81-1548a0f13d41" />
   <img width="1919" height="1199" alt="Screenshot 2025-10-28 205054" src="https://github.com/user-attachments/assets/993f6cc7-00dd-4aba-ac61-9bef163dc896" />


 
8. Edit the generated main program as required.
   
<img width="716" height="261" alt="Screenshot 2025-10-28 222542" src="https://github.com/user-attachments/assets/be2169b0-bdcc-4e18-b896-f3f731f29187" />

10. Click **Project → Build All**.
    
<img width="725" height="251" alt="Screenshot 2025-10-28 222628" src="https://github.com/user-attachments/assets/359040dc-7abc-48a3-879d-3b82959e990d" />

11. Link the **HEX file** using the post-build process.
<img width="725" height="251" alt="Screenshot 2025-10-28 222628" src="https://github.com/user-attachments/assets/3763744a-a04b-405a-8a51-733e54eaf5d7" />


12. Click **Debug** and connect the **STM Nucleo Board**.
    <img width="1919" height="1199" alt="Screenshot 2025-10-28 222724" src="https://github.com/user-attachments/assets/4a9f9002-c6b9-47f6-8d6c-994bb9afe012" />


13. Click **Run** to execute the program.
    
---

### 💻 **Program**


```c
#include "main.h"

void SystemClock_Config(void);
static void MX_GPIO_Init(void);

int main(void)
{
    HAL_Init();
    SystemClock_Config();
    MX_GPIO_Init();

    while (1)
    {
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
        HAL_Delay(1000);
        HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_SET);
        HAL_Delay(1000);
    }
}
```
---
### OUTPUT
CASE 1: LED ON 
![WhatsApp Image 2025-10-28 at 20 09 22](https://github.com/user-attachments/assets/5dd65df8-4a99-4833-926c-091d8b298b8d)


CASE 2: LED OFF
<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/c7042b88-c2d2-4a30-96df-d2219c6a8f08" />


---
### RESULT
Interfacing a digital output with ARM microcontroller is executed and the results are verified.
