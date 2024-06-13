# OGC.Engineering
### ogc_hw_nucleo_l476rg
developer contact - dustin ( at ) ogc.engineering

---
## Description:
* Hardware description of the ST NUCLEO-L476RG base development board and the STM32L476RG microcontroller
* NUCLEO-L476RG - https://www.st.com/en/evaluation-tools/nucleo-l476rg.html
    * STM32 Nucleo-64 development board with STM32L476RG MCU, supports Arduino and ST morpho connectivity
* STM32L476RG - https://www.st.com/en/microcontrollers-microprocessors/stm32l476rg.html
    * Ultra-low-power with FPU Arm Cortex-M4 MCU 80 MHz with 1 Mbyte of Flash memory, LCD, USB OTG, DFSDM
    * STM32L476RGT6 in LQFP64 package
    * ARM®32-bit Cortex®-M4 CPU
    * Adaptive real-time accelerator (ART Accelerator™) allowing 0-wait state execution from Flash memory
    * 80 MHz max CPU frequency ( Crystal Freq. TBD )
    * 32.768 kHz crystal oscillator 
    * VDD from 1.71 V to 3.6 V
    * 1 MB Flash
    * 128 KB SRAM
    * random generator (TRNG for HW entropy)
    * Quad SPI (1)
    * Timers General Purpose (7)
    * Timers Advanced-Control (2)
    * Timers Basic (2)
    * Timers LowPower (2)
    * Systick
    * Watchdog (2)
    * SPI (3)
    * I2C (3)
    * USART (3)
    * UART (2)
    * LPUART (1)
    * USB OTG Full Speed
    * CAN (1)
    * SAI (2)
    * SDMMC
    * SWPMI
    * LCD 8x28 or 4x32
    * GPIO (51) with external interrupt capability
        * User Button
        * LED ( Color TBD )
    * Capacitive sensing with 12 channels
    * 12-bit ADC (3) with 16 channels
    * 12-bit DAC with 2 channels
    * Analog comparator (2)
    * Opamp (2) 
* Additional resources:
    * https://os.mbed.com/platforms/st-nucleo-l476rg/ - provides summary of pinout and diagrams

---
## Pin Resources:
```
Arduino-compatible headers:
    CN6 ( top of board, left side, front )
         [ NC    ] - 
         [ IOREF ] - 
         [ RESET ] - 
         [ 3V3   ] - 
         [ 5V    ] - 
         [ GND   ] - 
         [ GND   ] - 
         [ VIN   ] - 
    CN8 ( top of baord, left side, rear )
         [ PA_0  ] - Serial4_TX, Serial2_RTS, PWM2/1, AnalogIn
         [ PA_1  ] - Serial4_RX, Serial2_RTS, PWM2/2, AnalogIn
         [ PA_4  ] - AnalogOut, SPI1_SSEL, AnalogIn
         [ PB_0  ] - PWM3/3, AnalogIn
         [ PC_1  ] - Serial1_TX, I2C3_SDA, AnalogIn
         [ PC_0  ] - Serial1_RX, I2C3_SCL, AnalogIn

    CN5 ( top of board, right side, front )
         [ PB_8  ] - CAN1_RD, I2C1_SCL, PWM4/3
         [ PB_9  ] - SPI2_SSEL, CAN1_TD, I2C1_SDA, PWM4/4
         [ AVDD  ] - 
         [ GND   ] - 
         [ PA_5  ] - AnalogIn, SC1, Out, PWM2/1
         [ PA_6  ] - AnalogIn, SPI1_MISO, PWM3/1
         [ PA_7  ] - AnalogIn, SPI1_MOSI, PWM3/2
         [ PB_6  ] - I2C1_SCL, Serial1_TX, PWM4/1
         [ PC_7  ] - PWM8/2
         [ PA_9  ] - Serail1_TX, PWM1/2
    CN9 ( top of baord, right side, rear )
         [ PA_8  ] - PWM1/1
         [ PB_10 ] - I2C2_SCL, SPI2_SCLK, Serial1_RX, Serial3_TX, PWM2/3
         [ PB_4  ] - SPI1_MISO, PWM3/1
         [ PB_5  ] - SPI1_MOSI, PWM3/2
         [ PB_3  ] - SPI1_SCLK, PWM2/2
         [ PA_10 ] - Serail1_RX, PWM1/3
         [ PA_2  ] - Serial2_TX
         [ PA_3  ] - Serial2_RX

Morpho headers:
CN7 ( top of board, left side )
                              SPI3_SCLK, Serial3_TX - [ PC_10 ][ PC_11 ] - Serial3_RX, SPI3_MISO
                              SPI3_MOSI, Serial5_TX - [ PC_12 ][ PD_2  ] - Serial5_RX
                                                    - [   VDD ][ E5V   ] - 
                                                    - [ BOOT0 ][ GND   ] - 
                                                    - [    NC ][ NC    ] - 
                                                    - [    NC ][ IOREF ] - 
                                                    - [ PA_13 ][ RESET ] - 
                                                    - [ PA_14 ][ 3V3   ] - 
                                  SPI1_SSEL, PWM2/1 - [ PA_15 ][ 5V    ] - 
                                                    - [   GND ][ GND   ] - 
                       I2C1_SDA, PWM4/2, Serial1_RX - [  PB_7 ][ GND   ] - 
                                    ( User Button ) - [ PC_13 ][ VIN   ] - 
                                                    - [ PC_14 ][ NC    ] - 
                                                    - [ PC_15 ][ PA_0  ] - Serial4_TX, Serial2_RTS, PWM2/1, AnalogIn
                                                    - [  PH_0 ][ PA_1  ] - Serial4_RX, Serial2_RTS, PWM2/2, AnalogIn
                                                    - [  PH_1 ][ PA_4  ] - AnalogOut, SPI1_SSEL, AnalogIn
                                                    - [  VBAT ][ PB_0  ] - PWM3/3, AnalogIn
                                AnalogIn, SPI2_MISO - [  PC_2 ][ PC_1  ] - Serial1_TX, I2C3_SDA, AnalogIn
                                AnalogIn, SPI2_MOSI - [  PC_3 ][ PC_0  ] - Serial1_RX, I2C3_SCL, AnalogIn

CN10 ( top of board, right side )
                                             PWM8/4 - [  PC_9 ][ PC_8  ] - PWM8/3
                          CAN1_RD, I2C1_SCL, PWM4/3 - [  PB_8 ][ PC_6  ] - PWM8/1
               SPI2_SSEL, CAN1_TD, I2C1_SDA, PWM4/4 - [  PB_9 ][ PC_5  ] - AnalogIn, Serial3_RX
                                                    - [  AVDD ][ U5V   ] - 
                                                    - [   GND ][ NC    ] - 
                         AnalogIn, SC1, Out, PWM2/1 - [  PA_5 ][ PA_12 ] - Serial1_RTS, CAN1_TD
                        AnalogIn, SPI1_MISO, PWM3/1 - [  PA_6 ][ PA_11 ] - PWM1/4, Serial1_CTS, CAN1_RD
                        AnalogIn, SPI1_MOSI, PWM3/2 - [  PA_7 ][ PB_12 ] - SPI2_SSEL
                       I2C1_SCL, Serial1_TX, PWM4/1 - [  PB_6 ][ PB_11 ] - PWM2/4, Serial1_TX, Serial3_RX, I2C2_SDA
                                             PWM8/2 - [  PC_7 ][ GND   ] - 
                                 Serail1_TX, PWM1/2 - [  PA_9 ][ PB_2  ] - 
                                             PWM1/1 - [  PA_8 ][ PB_1  ] - PWM3/4, AnalogIn
I2C2_SCL, SPI2_SCLK, Serial1_RX, Serial3_TX, PWM2/3 - [ PB_10 ][ PB_15 ] - PWM1/3N, SPI2_MOSI
                                  SPI1_MISO, PWM3/1 - [  PB_4 ][ PB_14 ] - PWM1/2N, SPI2_MISO, I2C_SDA
                                  SPI1_MOSI, PWM3/2 - [  PB_5 ][ PB_13 ] - PWM1/1N, SPI2_SCLK, I2C2_SCL
                                  SPI1_SCLK, PWM2/2 - [  PB_3 ][ AGND  ] - 
                                 Serail1_RX, PWM1/3 - [ PA_10 ][ PC_4  ] - Serial3_TX, AnalogIn
                                         Serial2_TX - [  PA_2 ][ NC    ] - 
                                         Serial2_RX - [  PA_3 ][ NC    ] - 

```
