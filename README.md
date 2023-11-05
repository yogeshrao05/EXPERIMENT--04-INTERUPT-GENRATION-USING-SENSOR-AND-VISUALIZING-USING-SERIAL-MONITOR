# EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR

### Aim:
To Interface a IR Sensor to digital port of iot development board  and generate an interrupt and visualize on the serial monitor 

### Components required:
STM32 CUBE IDE,  serial port utility monitor .


## Theory :

An infrared (IR) sensor a proximity sensor, or a ‘nearness’ sensor senses whether there is an object near it or not. The IR stands for Infrared sensor. Infrared is the light out of our visible spectrum.

Working of an IR Sensor
The white LED here is an IR LED which works as the transmitter and the component next to the IR LED is a photodiode that works as the receiver in the IR sensor.

The IR transmitter continuously emits the IR light and the IR receiver keeps on checking for the reflected light. If the light gets reflected back by hitting any object in front it, the IR receiver receives this light. This way the object is detected in the case of the IR sensor.

The blue knob here is a potentiometer. You can control the range i.e. from how far you want to detect the object by changing the value of the potentiometer.

An IR sensor has two small LED indicators – one for power, which is ON the entire time the sensor is ON; the other is the Signal LED which detects the object. The signal LED has two states or situations:

ON (Active) when it detects an object
OFF (Inactive) when it doesn’t detect any object

![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/9bf61298-1deb-48d7-b88f-bd08e3cc6a83)
Now that we have a little idea about its works, let’s take a look at how to interface it with evive and see it in action.

Connect VCC pin to the +5V pin on evive.
Connect GND pin to evive’s GND pin.
Connect OUT to any gpio and configure that pin as EXTI mode 

### Interrupts


Interrupts are asynchronous (i.e. can happen anytime) events that disrupt the normal flow of your program. This allows the microcontroller to focus on a key task and attend to these events (e.g. pressing a button) as they come without needing to wait for them.

With interrupt, we do not need to continuously check the state of the digital input pin. When an interrupt occurs (a change is detected), the processor stops the execution of the main program and a function is called upon known as ISR or the Interrupt Service Routine. The processor then temporarily works on a different task (ISR) and then gets back to the main program after the handling routine has ended.

![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/cb4ac7aa-30ed-4b97-b3b4-1986db9f1558)
The STM32 ARM microcontroller interrupts are generated in the following manner:

The system runs the ISR and then goes back to the main program. The NVIC and EXTI are configured. The Interrupt Service Routine (ISR) also known as the interrupt service routine handler is defined to enable the external interrupts.

 
Interrupt Lines (EXTI0-EXTI15)
The STM32 ARM microcontroller features 23 event sources which are divided into two sections. The first section corresponds t external pins on each port which are P0-P15. The second section corresponds to RTC, ethernet, USB interrupts. Therefore, in the first section, we have 16 lines corresponding to line0 till line15. All of these map to a pin number.
![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/1110746f-6be2-4d12-9a34-66004e4b307b)


The diagram below shows how the GPIO pins are connected to the 16 interrupt lines:
## Procedure:
 1. click on STM 32 CUBE IDE, the following screen will appear 
 ![image](https://user-images.githubusercontent.com/36288975/226189166-ac10578c-c059-40e7-8b80-9f84f64bf088.png)

 2. click on FILE, click on new stm 32 project 
 ![image](https://user-images.githubusercontent.com/36288975/226189215-2d13ebfb-507f-44fc-b772-02232e97c0e3.png)
![image](https://user-images.githubusercontent.com/36288975/226189230-bf2d90dd-9695-4aaf-b2a6-6d66454e81fc.png)
3. select the target to be programmed  as shown below and click on next 

![image](https://user-images.githubusercontent.com/36288975/226189280-ed5dcf1d-dd8d-43ae-815d-491085f4863b.png)

4.select the program name 
![image](https://user-images.githubusercontent.com/36288975/226189316-09832a30-4d1a-4d4f-b8ad-2dc28f137711.png)


5. corresponding ioc file will be generated automatically 
![image](https://user-images.githubusercontent.com/36288975/226189378-3abbdee2-0df6-470f-a3cd-79c74e3d3ad8.png)

6.select the appropriate pins as gipo, in or out, USART or required options and configure 
![image](https://user-images.githubusercontent.com/36288975/226189403-f7179f1a-3eae-4637-826b-ab4ec35ba1e1.png)
![image](https://user-images.githubusercontent.com/36288975/226189425-2b2414ce-49b3-4b61-a260-c658cb2e4152.png)


7.click on cntrl+S , automaticall C program will be generated 
![image](https://user-images.githubusercontent.com/36288975/226189443-8b43451d-0b14-47e4-a20b-cc09c6ad8458.png)
![image](https://user-images.githubusercontent.com/36288975/226189450-85ffa969-2ffb-4788-81e5-72d60fdda0f1.png)
8. edit the program and as per required 
![image](https://user-images.githubusercontent.com/36288975/226189461-a573e62f-a109-4631-a250-a20925758fe0.png)

9. use project and build all 
![image](https://user-images.githubusercontent.com/36288975/226189554-3f7101ac-3f41-48fc-abc7-480bd6218dec.png)
10. once the project is bulild 
![image](https://user-images.githubusercontent.com/36288975/226189577-c61cc1eb-3990-4968-8aa6-aefffc766b70.png)

11. click on debug option 
![image](https://user-images.githubusercontent.com/36288975/226189625-37daa9a3-62e9-42b5-a5ce-2ac63345905b.png)

12. connect the  iot board to power supply and usb 

13. After connecting open the STM cube programmer 
![image](https://user-images.githubusercontent.com/36288975/227599356-9c465b7e-6bd0-436b-b4e8-742ed25e06ce.png)

14. click on UART and click on connect 
![image](https://user-images.githubusercontent.com/36288975/227599458-26976d4a-f2d4-49f0-a49f-31f46eb15761.png)

15. once it is connected , click on Erasing and programming option 
![image](https://user-images.githubusercontent.com/36288975/227599531-f03d277e-440f-4f8a-8875-97f8e8058c71.png)

16. flash the bin or hex file as shown below by switching the switch to flash mode 

![image](https://user-images.githubusercontent.com/36288975/227599656-dc4a635f-b5f1-44c8-84c5-ee0a592fa184.png)


17. check for execution of the output by switching the board to run mode 
18. click on the serial port utility 
![image](https://github.com/vasanthkumarch/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/36288975/cd2c17fc-afac-4d72-97f9-20db3e63f23f)
19. click on the run to observe the values 


  

## STM 32 CUBE PROGRAM :
```c
#include "main.h"
#include"stdbool.h"
#include "stdio.h"
UART_HandleTypeDef huart1;
void SystemClock_Config(void);
static void MX_GPIO_Init(void);
static void MX_USART1_UART_Init(void);
#if defined (__ICCARM__) || defined (__ARMCC_VERSION)
#define PUTCHAR_PROTOTYPE int fputc(int ch, FILE *f)
#elif defined(__GNUC__)
#define PUTCHAR_PROTOTYPE int __io_putchar(int ch)
#endif
int main(void)
{
  HAL_Init();
  SystemClock_Config();
  MX_GPIO_Init();
  MX_USART1_UART_Init();
  while (1)
  {
  }
}
void HAL_GPIO_EXTI_Callback(uint16_t GPIO_Pin)
{
	if (HAL_GPIO_ReadPin(GPIOA, GPIO_PIN_6)==0)
	{
		printf("IR ON  \n");
	}
	else
	{
		printf("IR OFF \n");
	}
}
void SystemClock_Config(void)
{
  RCC_OscInitTypeDef RCC_OscInitStruct = {0};
  RCC_ClkInitTypeDef RCC_ClkInitStruct = {0};
  __HAL_PWR_VOLTAGESCALING_CONFIG(PWR_REGULATOR_VOLTAGE_SCALE2);
  RCC_OscInitStruct.OscillatorType = RCC_OSCILLATORTYPE_MSI;
  RCC_OscInitStruct.MSIState = RCC_MSI_ON;
  RCC_OscInitStruct.MSICalibrationValue = RCC_MSICALIBRATION_DEFAULT;
  RCC_OscInitStruct.MSIClockRange = RCC_MSIRANGE_6;
  RCC_OscInitStruct.PLL.PLLState = RCC_PLL_NONE;
  if (HAL_RCC_OscConfig(&RCC_OscInitStruct) != HAL_OK)
  {
    Error_Handler();
  }
  RCC_ClkInitStruct.ClockType = RCC_CLOCKTYPE_HCLK3|RCC_CLOCKTYPE_HCLK
                              |RCC_CLOCKTYPE_SYSCLK|RCC_CLOCKTYPE_PCLK1
                              |RCC_CLOCKTYPE_PCLK2;
  RCC_ClkInitStruct.SYSCLKSource = RCC_SYSCLKSOURCE_MSI;
  RCC_ClkInitStruct.AHBCLKDivider = RCC_SYSCLK_DIV1;
  RCC_ClkInitStruct.APB1CLKDivider = RCC_HCLK_DIV1;
  RCC_ClkInitStruct.APB2CLKDivider = RCC_HCLK_DIV1;
  RCC_ClkInitStruct.AHBCLK3Divider = RCC_SYSCLK_DIV1;

  if (HAL_RCC_ClockConfig(&RCC_ClkInitStruct, FLASH_LATENCY_0) != HAL_OK)
  {
    Error_Handler();
  }
}
static void MX_USART1_UART_Init(void)
{
  huart1.Instance = USART1;
  huart1.Init.BaudRate = 9600;
  huart1.Init.WordLength = UART_WORDLENGTH_8B;
  huart1.Init.StopBits = UART_STOPBITS_1;
  huart1.Init.Parity = UART_PARITY_NONE;
  huart1.Init.Mode = UART_MODE_TX_RX;
  huart1.Init.HwFlowCtl = UART_HWCONTROL_NONE;
  huart1.Init.OverSampling = UART_OVERSAMPLING_16;
  huart1.Init.OneBitSampling = UART_ONE_BIT_SAMPLE_DISABLE;
  huart1.Init.ClockPrescaler = UART_PRESCALER_DIV1;
  huart1.AdvancedInit.AdvFeatureInit = UART_ADVFEATURE_NO_INIT;
  if (HAL_UART_Init(&huart1) != HAL_OK)
  {
    Error_Handler();
  }
  if (HAL_UARTEx_SetTxFifoThreshold(&huart1, UART_TXFIFO_THRESHOLD_1_8) != HAL_OK)
  {
    Error_Handler();
  }
  if (HAL_UARTEx_SetRxFifoThreshold(&huart1, UART_RXFIFO_THRESHOLD_1_8) != HAL_OK)
  {
    Error_Handler();
  }
  if (HAL_UARTEx_DisableFifoMode(&huart1) != HAL_OK)
  {
    Error_Handler();
  }
}
static void MX_GPIO_Init(void)
{
  GPIO_InitTypeDef GPIO_InitStruct = {0};
  __HAL_RCC_GPIOB_CLK_ENABLE();
  __HAL_RCC_GPIOA_CLK_ENABLE();
  GPIO_InitStruct.Pin = GPIO_PIN_6;
  GPIO_InitStruct.Mode = GPIO_MODE_IT_RISING;
  GPIO_InitStruct.Pull = GPIO_PULLUP;
  HAL_GPIO_Init(GPIOA, &GPIO_InitStruct);
  HAL_NVIC_SetPriority(EXTI9_5_IRQn, 0, 0);
  HAL_NVIC_EnableIRQ(EXTI9_5_IRQn);
}
void Error_Handler(void)
{
  __disable_irq();
  while (1)
  {
  }
}
#ifdef  USE_FULL_ASSERT
void assert_failed(uint8_t *file, uint32_t line)
{
}
#endif
```


## Output screen shots of serial port utility   :
 ![WhatsApp Image 2023-10-28 at 16 21 28_0395f335](https://github.com/NaveenM-IOT0804/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/117974950/13d46b0d-2b81-421e-a0bb-7d1d25285452)
![WhatsApp Image 2023-10-28 at 16 21 40_84e1deaa](https://github.com/NaveenM-IOT0804/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/117974950/dc9c56f5-31c2-4334-8d37-5a317e96eced)

 
 ## Circuit board :
 
![image](https://github.com/NaveenM-IOT0804/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/117974950/5b06cb7c-852e-41b9-8f1c-54f11f71c813)

![image](https://github.com/NaveenM-IOT0804/EXPERIMENT--04-INTERUPT-GENRATION-USING-SENSOR-AND-VISUALIZING-USING-SERIAL-MONITOR/assets/117974950/af1883e2-f93d-4011-98d6-41f3262e6b4f)

## Result :
Interfacing a  IR SENSOR and interrupt is generated using external interrupt mode , visualized on serial port 
