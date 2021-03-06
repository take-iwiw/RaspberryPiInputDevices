# Input devices test application for Raspberry Pi

* This is an application to try the following input devices on Raspberry Pi using pthread
	* Key (GPIO)
	* Rotary Encoder (GPIO)
	* Accelerometer (I2C)

## Environment
* NetBeans C/C++ Bundle

## Devices
* Raspberry Pi 2 Model B
* ADXL345

## Libraries required
* wiringPi

## Manual build command on Host PC (Cross Compile)
```
ARCH=arm ../../../tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian-x64/bin/arm-linux-gnueabihf-g++ -I../../../libraries/wiringPi/wiringPi -L../../../libraries/wiringPi/wiringPi -lwiringPi -lpthread main.cpp InputDevices.cpp
```
* need to change directory dependingon your environment


## Portmap
```
## IO
GPIO00 = N/A
GPIO01 = N/A
GPIO02 = I2C_SDA
GPIO03 = I2C_SCL
GPIO04 = 
GPIO05 = 
GPIO06 = 
GPIO07 = SPI_CE1
GPIO08 = SPI_CE0
GPIO09 = SPI_MISO
GPIO10 = SPI_MOSI
GPIO11 = SPI_SCLK
GPIO12 = 
GPIO13 = 
GPIO14 = UART_TXD
GPIO15 = UART_RXD
GPIO16 = 
GPIO17 = INPUT_KEY0
GPIO18 = 
GPIO19 = 
GPIO20 = INPUT_RotaryEncoder_B
GPIO21 = INPUT_RotaryEncoder_A
GPIO22 = 
GPIO23 = 
GPIO24 = 
GPIO25 = N/A
GPIO26 = 
GPIO27 = INPUT_KEY1
GPIO28 = N/A
GPIO29 = N/A

## Function
USART = System Console
SPI = 
I2C = Accelerometer (ADXL345)
```


## Memo I2C setup
* Enable I2C (and SPI)
	* $PI$ > sudo raspi-config 
	* 9 Advanced Options
		* A7 I2C
		* A6 SPI

* Install necessary tools
	* $PI$ > sudo apt-get install i2c-tools

* Try I2C from console
	* $PI$ > i2cdetect -y 1
	* $PI$ > i2cget -y 1 0x53 0x00 b
