# Experiment-01-INTERFACING DIGITAL OUTPUT FOR ARM DEVELOPMENT BOARD 
 

## Aim: To Interface a Digital output (LED) to ARM development board and write a blink code 
## Components required: STM32 CUBE IDE, NUCLEO ARM DEVELOPMENT BOARD  
## Theory 
The full form of an ARM is an advanced reduced instruction set computer (RISC) machine, and it is a 32-bit processor architecture expanded by ARM holdings. The applications of an ARM processor include several microcontrollers as well as processors. The architecture of an ARM processor was licensed by many corporations for designing ARM processor-based SoC products and CPUs. This allows the corporations to manufacture their products using ARM architecture. Likewise, all main semiconductor companies will make ARM-based SOCs such as Samsung, Atmel, TI etc.

What is an ARM7 Processor?
ARM7 processor is commonly used in embedded system applications. Also, it is a balance among classic as well as new-Cortex sequence. This processor is tremendous in finding the resources existing on the internet with excellence documentation offered by NXP Semiconductors. It suits completely for an apprentice to obtain in detail hardware & software design implementation.
LPC2148 Microcontroller
 The LPC2148 microcontroller is designed by Philips (NXP Semiconductor) with several in-built features & peripherals. Due to these reasons, it will make more reliable as well as the efficient option for an application developer. LPC2148 is a 16-bit or 32-bit microcontroller based on ARM7 family.
Features of LPC2148
The main features of LPC2148 include the following.
•	The LPC2148 is a 16 bit or 32 bit ARM7 family based microcontroller and available in a small LQFP64 package.
•	ISP (in system programming) or IAP (in application programming) using on-chip boot loader software.
•	On-chip static RAM is 8 kB-40 kB, on-chip flash memory is 32 kB-512 kB, the wide interface is 128 bit, or accelerator allows 60 MHz high-speed operation.
•	It takes 400 milliseconds time for erasing the data in full chip and 1 millisecond time for 256 bytes of programming.
•	Embedded Trace interfaces and Embedded ICE RT offers real-time debugging with high-speed tracing of instruction execution and on-chip Real Monitor software.
•	It has 2 kB of endpoint RAM and USB 2.0 full speed device controller. Furthermore, this microcontroller offers 8kB on-chip RAM nearby to USB with DMA.
•	One or two 10-bit ADCs offer 6 or 14 analogs i/ps with low conversion time as 2.44 μs/ channel.
•	Only 10 bit DAC offers changeable analog o/p.
•	External event counter/32 bit timers-2, PWM unit, & watchdog.
•	Low power RTC (real time clock) & 32 kHz clock input.
•	Several serial interfaces like two 16C550 UARTs, two I2C-buses with 400 kbit/s speed.
•	5 volts tolerant quick general purpose Input/output pins in a small LQFP64 package.
•	Outside interrupt pins-21.
•	60 MHz of utmost CPU CLK-clock obtainable from the programmable-on-chip phase locked loop by resolving time is 100 μs.
•	The incorporated oscillator on the chip will work by an exterior crystal that ranges from 1 MHz-25 MHz
•	The modes for power-conserving mainly comprise idle & power down.
•	For extra power optimization, there are individual enable or disable of peripheral functions and peripheral CLK scaling.
 
 

## Procedure:
 1. click on STM 32 CUBE IDE, the following screen will appear 

![S1](https://user-images.githubusercontent.com/119476322/226983988-2e871bee-c630-4964-9d7f-9671939cb0f0.png)

 2. click on FILE, click on new stm 32 project 
 
 ![S2](https://user-images.githubusercontent.com/119476322/226984118-8db7a764-f968-4650-a36b-24f4706337bd.png)

3. select the target to be programmed  as shown below and click on next 

![S3](https://user-images.githubusercontent.com/119476322/226984209-6212b4e7-8a23-4b68-8c88-7c6736e44c3a.png)

4.select the program name 

![S4](https://user-images.githubusercontent.com/119476322/226984330-3b28f6bf-624e-495b-a0c4-b32130fd9f96.png)

5. corresponding ioc file will be generated automatically 

![S5](https://user-images.githubusercontent.com/119476322/226984388-c9617d21-953d-4143-b9f9-d100ca79a7df.png)

6.select the appropriate pins as gipo, in or out, USART or required options and configure 

![S6](https://user-images.githubusercontent.com/119476322/226984687-028378c4-a971-4798-b2ba-853026bcb731.png)

7.click on cntr+S
l+S , automaticall C program will be generated 

![S7](https://user-images.githubusercontent.com/119476322/226984770-1ed29200-6435-4436-bde7-88405c8f8f82.png)

8. edit the program and as per required 

![S8](https://user-images.githubusercontent.com/119476322/226984880-2f114897-7562-4122-bae8-b4a5a41f990e.png)

9. once the project is bulild 

![S9](https://user-images.githubusercontent.com/119476322/226985235-5fdc82ba-9458-4dde-afb6-b1ba077c2c4f.png)

10. click on debug option 

![S10](https://user-images.githubusercontent.com/119476322/226985348-8caf62a9-7fe4-41af-ab29-6976a0ff8d4c.png)


11. connect the stm nucleo board and click on run 
![image](https://user-images.githubusercontent.com/36288975/226189649-b5dff389-91df-4eca-b84a-1127c6562637.png)






## STM 32 CUBE PROGRAM :

```
Developed By: Sivaramakrishnan B
Register No: 212222110044
#include "main.h"
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
void led();

  */
int main(void)
{
  HAL_Init();
  SystemClock_Config();

  MX_GPIO_Init();
  
  while (1)
  {
   led();
   
  }
}
void led()
{
 HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5,GPIO_PIN_SET);
 HAL_Delay(100);
 HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET);
 HAL_Delay(100);
}
void SystemClock_Config(void)
{
  RCC_OscInitTypeDef RCC_OscInitStruct = {0};
  RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};

  
  HAL_PWREx_ControlVoltageScaling(PWR_REGULATOR_VOLTAGE_SCALE1);
  
  */
  RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_HSI;
  RCC_OscInitStruct.HSIState = RCC_HSI_ON;
  RCC_OscInitStruct.HSIDiv = RCC_HSI_DIV1;
  RCC_OscInitStruct.HSICalibrationValue = RCC_HSICALIBRATION_DEFAULT;
  RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;
  if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK)
  {
    Error_Handler();
  }
  */
  RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK|RCC_CLOCKTYPE_SYSCLK
                              |RCC_CLOCKTYPE_PCLK1;
  RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_HSI;
  RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
  RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;

  if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
  {
    Error_Handler();
  }
}

/
static void MX_GPIO_Init(void)
{
  GPIO_InitTypeDef GPIO_InitStruct = {0};

  __HAL_RCC_GPIOA_CLK_ENABLE();

  HAL_GPIO_WritePin(GPIOA, GPIO_PIN_5, GPIO_PIN_RESET); 
  GPIO_InitStruct.Pin = GPIO_PIN_5;
  GPIO_InitStruct.Mode = GPIO_MODE_OUTPUT_PP;
  GPIO_InitStruct.Pull = GPIO_NOPULL;
  GPIO_InitStruct.Speed = GPIO_SPEED_FREQ_LOW;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);

}
void Error_Handler(void)
{
  __disable_irq();
  while (1)
  {
  }
  
}

#ifdef USE_FULL_ASSERT

void assert_failed(uint8_t *file, uint32_t line)
{
  
}
#endif

```


## Output  :

#### LED ON & OFF CONDITION: 
 ![image](https://github.com/SivaramakrishnanBaskar/Experiment-01-INTERFACING-DIGITAL-OUTPUT-FOR-ARM-DEVELOPMENT-BOARD-/assets/119476322/2ad12b49-0584-4113-9a2d-a68ec4893b8a)

 
 
## Result :
Interfacing a digital output with ARM microcontroller is executed and the results are verified.


