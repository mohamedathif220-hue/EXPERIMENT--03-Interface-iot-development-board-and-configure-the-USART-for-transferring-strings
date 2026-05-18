# EXPERIMENT--03-INTERFACING IOT DEVELOPMENT BOARD AND CONFIGURE USART FOR TRANSFERRING STRINGS 

**DATE:18/05/2026**

**NAME:S.L.NARASIMHA REDDY**

**ROLL NO:212223040214**

**DEPARTMENT:cse**

## Aim:

To Interface iot development board for configuring the usart and transfer strings through it 

## Components required: 

STM32 CUBE IDE, ARM IOT development board,  STM programmer tool, Serial port utility tool 


## Theory 

The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

![image](https://github.com/user-attachments/assets/82224b9f-ed9c-4eed-9b36-1f6ec98db68a)

UART (Universal Asynchronous Receiver-Transmitter) is a serial communication protocol used to transfer data between devices. It is widely used in embedded systems, microcontrollers, and computers for short-distance communication.
UART transmits and receives data asynchronously, meaning there is no shared clock signal between the sender and receiver. Instead, both devices must agree on a predefined baud rate (speed of communication).


## Procedure

1. Click on STM 32 CUBE IDE, the following screen will appear
   
 ![image](https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png)


2. Click on FILE, click on new stm 32 project
   
![image](https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png)

![image](https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png)

3. Select the target to be programmed as shown below and click on next
   
![Screenshot 2025-03-11 134231](https://github.com/user-attachments/assets/09e61f3d-224f-4ca8-96d4-7336869df5c7)

4. Select the program name
   
![image](https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png)

5. Corresponding ioc file will be generated automatically
   
![Screenshot 2025-03-11 134528](https://github.com/user-attachments/assets/df427edd-e24a-4612-a858-aeae859b379f)


6. Select the appropriate pins as GPIO, in or out, USART or required options and configure
   
![Screenshot 2025-03-11 134617](https://github.com/user-attachments/assets/125ee548-30b1-4c88-932f-adf07984522f)
![Screenshot 2025-03-11 134642](https://github.com/user-attachments/assets/0adfbb58-4cad-408a-9300-f4808b53cac4)


7. Click on Ctrl+S, automatically C program will be generated
   
![image](https://github.com/user-attachments/assets/1e9a3494-c750-44d2-9a64-145b2b7bf8f1)

8. Edit the program and as per required 

![image](https://user-images.githubusercontent.com/36288975/226189461-a573e62f-a109-4631-a250-a20925758fe0.png)


9. Use project and build all 

![image](https://user-images.githubusercontent.com/36288975/226189554-3f7101ac-3f41-48fc-abc7-480bd6218dec.png)

10. Once the project is bulild 

![image](https://user-images.githubusercontent.com/36288975/226189577-c61cc1eb-3990-4968-8aa6-aefffc766b70.png)

11. Open STM32Cube Programmer

![Screenshot 2025-03-11 135208](https://github.com/user-attachments/assets/bb67ab6b-81a5-450c-b170-4276a9b87ef2)

12. Connect the STM board through the COM port, then upload the corresponding project ELF file while ensuring the board is in flash mode, and click on 'Start Program.' After the file download is complete, switch your board to run mode and press the reset button to see the output
  
13.Open serial port utility 

![image](https://github.com/user-attachments/assets/c7fb1ee4-814b-4589-92c3-080442637265)

14. Check for execution of the output using run option.


## STM 32 CUBE PROGRAM :
```
#include "main.h"
#include "stdio.h"

UART_HandleTypeDef huart2;

void SystemClock_Config(void);
static void MX_GPIO_Init(void);
static void MX_USART2_UART_Init(void);

#if defined(_ICCARM) || defined(_ARMCC_VERSION)
#define PUTCHAR_PROTOTYPE int fputc(int ch,FILE *f)
#elif defined(_GNUC_)
#define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#endif
int main(void)
{
  HAL_Init();                 // Initialize HAL library
  SystemClock_Config();       // Configure system clock
  MX_GPIO_Init();             // Initialize GPIOs
  MX_USART2_UART_Init();      // Initialize UART2

  while (1)
  {
    printf(" saveetha engineerng college\n");
    printf("scoft\n");
    HAL_Delay(500);          // 500ms delay
  }
}
PUTCHAR_PROTOTYPE
{
  HAL_UART_Transmit(&huart2, (uint8_t *)&ch, 1, 0xFFFF);
  return ch;
}
```



## Output screen shots of Serial port utility   :
 
 ![WhatsApp Image 2025-04-09 at 11 48 03_fa603256](https://github.com/user-attachments/assets/9cb6513d-df6e-43f5-b626-649bf28459d4)

 
 
## Result :
The IoT development board was successfully interfaced, and the USART was configured to transmit strings. The transmitted data was verified using a serial monitor, confirming proper communication.
