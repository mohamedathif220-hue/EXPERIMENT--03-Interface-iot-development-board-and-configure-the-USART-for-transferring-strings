# EXPERIMENT--03-INTERFACING IOT DEVELOPMENT BOARD AND CONFIGURE USART FOR TRANSFERRING STRINGS 

**DATE:18/05/2026

**NAME:Mohamed Athif

**ROLL NO:212225040239

**DEPARTMENT:cse

## Aim:

To Interface iot development board for configuring the usart and transfer strings through it 

## Components required: 

STM32 CUBE IDE, ARM IOT development board,  STM programmer tool, Serial port utility tool 


## Theory 

The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

<img width="940" height="659" alt="Screenshot 2026-05-25 141443" src="https://github.com/user-attachments/assets/95319b20-38cf-47ff-ad8f-f34b3df97883" />

UART (Universal Asynchronous Receiver-Transmitter) is a serial communication protocol used to transfer data between devices. It is widely used in embedded systems, microcontrollers, and computers for short-distance communication.
UART transmits and receives data asynchronously, meaning there is no shared clock signal between the sender and receiver. Instead, both devices must agree on a predefined baud rate (speed of communication).


## Procedure

1. Click on STM 32 CUBE IDE, the following screen will appear
   <img width="1044" height="588" alt="Screenshot 2026-05-25 141454" src="https://github.com/user-attachments/assets/2c0a5bc2-826a-4c66-bae0-c8fe2d4c1835" />

 


2. Click on FILE, click on new stm 32 project
   
<img width="1048" height="592" alt="Screenshot 2026-05-25 141504" src="https://github.com/user-attachments/assets/913d2ab3-bc31-4a45-a349-c62f4186b0af" />




3. Select the target to be programmed as shown below and click on next
   
<img width="1048" height="594" alt="Screenshot 2026-05-25 141512" src="https://github.com/user-attachments/assets/bbb8d17b-88a6-45c5-85c7-48dafd827b8f" />


4. Select the program name
   
<img width="1044" height="628" alt="Screenshot 2026-05-25 141523" src="https://github.com/user-attachments/assets/a16c3e69-0ed4-4b84-b9b5-34f4fa6f91c8" />


5. Corresponding ioc file will be generated automatically
   <img width="600" height="665" alt="Screenshot 2026-05-25 141531" src="https://github.com/user-attachments/assets/cc9031d8-977b-47c3-9b58-13581a7a5ab9" />




6. Select the appropriate pins as GPIO, in or out, USART or required options and configure
<img width="1042" height="607" alt="Screenshot 2026-05-25 141541" src="https://github.com/user-attachments/assets/492858d2-9580-4965-8cf6-e9dea433e22a" />

<img width="1043" height="604" alt="Screenshot 2026-05-25 141552" src="https://github.com/user-attachments/assets/0957e61b-2d59-48a0-9a39-6a26c9359d34" />


7. Click on Ctrl+S, automatically C program will be generated
   
<img width="1044" height="620" alt="Screenshot 2026-05-25 141602" src="https://github.com/user-attachments/assets/0a771e5e-ddc7-4907-bfaa-e8aed4d42331" />


8. Edit the program and as per required 

<img width="1044" height="471" alt="Screenshot 2026-05-25 141611" src="https://github.com/user-attachments/assets/bd33b219-cf57-4b67-8da7-837d6ae72780" />


9. Use project and build all 

<img width="1047" height="588" alt="Screenshot 2026-05-25 141627" src="https://github.com/user-attachments/assets/52d35ee4-d0bd-4b94-8777-7d54bda88a8a" />


10. Once the project is bulild 

<img width="1052" height="596" alt="Screenshot 2026-05-25 141636" src="https://github.com/user-attachments/assets/b8a81fab-1df2-44ef-aa2d-0022be9dbe4b" />

11. Open STM32Cube Programmer

<img width="1044" height="459" alt="Screenshot 2026-05-25 141647" src="https://github.com/user-attachments/assets/e21366b5-2c9d-4c72-84ac-4c5b89a14814" />


12. Connect the STM board through the COM port, then upload the corresponding project ELF file while ensuring the board is in flash mode, and click on 'Start Program.' After the file download is complete, switch your board to run mode and press the reset button to see the output
  
13.Open serial port utility 

<img width="1049" height="618" alt="Screenshot 2026-05-25 141832" src="https://github.com/user-attachments/assets/23fb3a11-60a6-4431-91b6-04299fed123f" />


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
 
<img width="1042" height="546" alt="Screenshot 2026-05-25 141849" src="https://github.com/user-attachments/assets/ef47c348-ecf0-413a-af42-c40b6a04fa60" />

## Result :
The IoT development board was successfully interfaced, and the USART was configured to transmit strings. The transmitted data was verified using a serial monitor, confirming proper communication.
