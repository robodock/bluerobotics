---
layout: default
title: BlueESC Documentation
permalink: /bluesc/
order: 1
nav:
- Introduction: introduction 
- - Safety: safety
- - Quick Start: quick-start
- Specifications: specifications
- - Diagram: diagram
- - Specification Table: specification-table
- - 3D Model: 3d-model
- Operation: operation
- - LED Indicator Lights: led-indicator-lights
- I<sup>2</sup>C Protocol: i2c-protocol
- - Throttle Command: throttle-command
- - Data Request: data-request
- - Data Conversion: data-conversion
- - Assigning I<sup>2</sup>C Addresses: assigning-i2c-addresses
- Example Code: example-code
- - Arduino With Servo Library: arduino-with-servo-library
- - Arduino With I2C: arduino-with-i2c
- Advanced: advanced
- - Firmware Files: firmware-files
- - Firmware Update and Customization: firmware-update-and-customization
---

# 簡介

BlueESC 是 T100 與 T200 推進器使用的 ESC 電子調速器。它是量身打造，可直接安裝在推進器上，同時具有防水、水冷與抗壓的特性。

## 安全守則 

<i class="fa fa-exclamation-triangle fa-fw fa-2x text-warning"></i> 在電氣環境中工作時，請隨時注意安全， 確認連頭連結穩固並維持水密。並將身體遠離轉動的馬達、螺槳部位。

## 快速開始

BlueESC 以預裝在 T100 或 T200 推進器上，您要做的只有供電與連接訊號線至控制器。

1. 透過粗的紅、黑導線連接 BlueESC 到電力來源，紅線為電源(+)，黑線為接地(-)。
2. 透過較細的訊號線，連接黑線至接地線，紅線或黃線為 PWM 訊號線。BlueESC 沒有 BEC 電路因此無法額外提供5V電源給其他設備。
3. 提供一個 1500 &mu;s 的停止訊號數秒鐘，來啟始 ESC，ESC 會短暫發出聲音同時閃爍燈光。

4. 起始過後即可待機備便!

# 規格

## 接線圖

<img src="/assets/images/documentation/blue-esc-labels.png" class="img-responsive" style="max-width:800px" />

## 規格表

|                       **電力**                        |
| --------------------------- | ------------- | ------------- |
| 電壓                 | 6-22 volts                    |
| 最大電流 (水中)      | 35 amps                       |
| 最大電流 (空氣中)    | 25 amps                       |
| --------------------------- | ------------- | ------------- |
|                       **實體**                          |
| --------------------------- | ------------- | ------------- |
| 外殼長度         | 18 mm         | 0.71 in       |
| 外殼直徑       | 40.4 mm       | 1.59 in       |
| 纜線長度             | 1 m           | 39 in         |
| 電源線直徑           | 6.3 mm        | 0.25 in       |
| 訊號線直徑           | 3.8 mm        | 0.15 in       |
| 電源線顏色                  | 紅 - 正                |
|                             | 黑 - 負 (接地)         |
| 訊號線顏色                  | 黑 - 接地              |
|                             | 紅 或 黃 - PWM 訊號    |
|                             | 白 - I<sup>2</sup>C 資料 (SDA) |
|                             | 綠 - I<sup>2</sup>C 時脈 (SCL) |
| --------------------------- | ------------- | ------------- |
|                    **脈波寬度訊號**                   |
| --------------------------- | ------------- | ------------- |
| 訊號電壓              | 3.3-5 volts                   |
| 更新率                 | 50-400 Hz                     |
| 停止                     | 1500 microseconds             |
| 最大向前                 | 1900 microseconds             |
| 最大向後                 | 1100 microseconds             |
| 訊號靜區(不工作區)       | +/- 25 microseconds (以 1500 microseconds 為中心) |
| --------------------------- | ------------- | ------------- |
|                   **I<sup>2</sup>C Signal**                 |
| --------------------------- | ------------- | ------------- |
| 訊號電壓              | 5 volts                       |
| I<sup>2</sup>C 位址   | 0x29 (default) - 0x38         |
| --------------------------- | ------------- | ------------- |
|                    **性能**                   |
| --------------------------- | ------------- | ------------- |
| 最大深度               | 待測定; 設計為 500m+|

## 3D模型

Coming soon.

<!--
| 檔案格式                   | 連結                          |
| -------------------------- | ----------------------------- |
| SolidWorks Part (.sldprt)  | [BLUESC-R1.sldprt](#) |
| STEP (.step)               | [BLUESC-R1.step](#)   |
| IGES (.igs)                | [BLUESC-R1.igs](#) |
| STL (.stl)                 | [BLUESC-R1.stl](#) |
| All in a zip file (.zip)   | [BLUESC-R1.zip](#) |
-->

# 操作

## LED指示燈

BlueESC 有兩個指示燈顯示 ESC 的狀態。這些 LEDs 的燈號與 tgy 韌體的預設行為相同。詳細請查看
[README for *tgy*](https://github.com/sim-/tgy/blob/master/README.md#troubleshooting).

# I<sup>2</sup>C 協定

I<sup>2</sup>C 通訊協定允許與 ESC 雙向通訊。協定使用一種 "register map" 的方式來溝通。

## 油門指令

### 敘述

油門指令是一個 16 位元有號整數。正負號代表不同旋轉方向。記得初始化時需送出 "0"。

### Registers: (0x00-0x01)

* **油門:** (僅能寫入)
	* -32767 (最大反轉) to 32767 (最大向前)
	* 0 為停止
	* 無靜區(不工作區)

### Bytes

* **Byte 0:** throttle_h  
* **Byte 1:** throttle_l

## 資料請求

### 敘述

資料 registers 可以讀取提供電壓、電流、轉速與溫度。所有數值為 16位元 無號整數。

### Registers: (0x02-0x0A)

* **pulse_count:** (唯讀)
  * 計算自從上次請求後的脈波數。
  * 計算 rpm 轉數 with pulse_count/dt*60/motor_pole_count
* **voltage:** (唯讀)
	* 類比數位轉換器測量值16位元轉換
  * 計算電壓 with voltage/2016
* **temperature:** (唯讀)
	* 類比數位轉換器測量值16位元轉換
  * 計算溫度 with the Steinhart equation
* **current:** (唯讀)
	* 類比數位轉換器測量值16位元轉換
  * 計算電流 with (current-32767)/891
* **identifier:** (唯讀)
	* ESC作動中測試驗證位元

### Bytes

* **Byte 0:** pulse_count_h  
* **Byte 1:** pulse_count_l  
* **Byte 2:** voltage_h  
* **Byte 3:** voltage_l  
* **Byte 4:** temperature_h  
* **Byte 5:** temperature_l  
* **Byte 6:** current_h  
* **Byte 7:** current_l  
* **Byte 8:** 0xab (identifier to check if ESC is alive)

## 資料轉換

透過 I2C 傳送的傳感器資料必須轉換成正確的單位。底下的方程式敘述如何處理。

### 電壓

電壓分配器使用 18K 與 3.3K 電阻形成 6.45 的分配率。並轉換成 16 位元。公式如下：

$$
\begin{align*}
V_{ESC} = 0.0004921 V_{raw}
\end{align*}
$$

程式碼範例：

~~~ cpp
float voltage() {
  return voltage_raw*0.0004921;
}
~~~

### 電流

電流使用 ACS711 霍爾效應傳感器IC測量，輸出 14.706 A/V 可有 2.5V 的偏差值，並轉換成 16 位元。

$$
\begin{align*}
I_{ESC} = 0.001122 (I_{raw}-32767)
\end{align*}
$$

程式碼範例：

~~~ cpp
float current() {
  (return current_raw-32767)*0.001122;
}
~~~

### 溫度

溫度使用一個 10K 熱敏電阻(NCP18XH103J03RB) 與 3.3K 電阻。溫度使用 Steinhart-Hart 公式計算。

$$
\begin{align*}
\frac{1}{T}=\frac{1}{T_0}+\frac{1}{B}ln \left (\frac{1}{T}\right )
\end{align*}
$$


程式碼範例：

~~~ cpp
// THERMISTOR SPECIFICATIONS
// resistance at 25 degrees C
#define THERMISTORNOMINAL 10000      
// temp. for nominal resistance (almost always 25 C)
#define TEMPERATURENOMINAL 25   
// The beta coefficient of the thermistor (usually 3000-4000)
#define BCOEFFICIENT 3900
// the value of the 'other' resistor
#define SERIESRESISTOR 3300 

float temperature(_temp_raw) {
  // This code was taken from an Adafruit
  float resistance = SERIESRESISTOR/(65535/float(_temp_raw)-1);

  float steinhart;
  steinhart = resistance / THERMISTORNOMINAL;  // (R/Ro)
  steinhart = log(steinhart);                  // ln(R/Ro)
  steinhart /= BCOEFFICIENT;                   // 1/B * ln(R/Ro)
  steinhart += 1.0 / (TEMPERATURENOMINAL + 273.15); // + (1/To)
  steinhart = 1.0 / steinhart;                 // Invert
  steinhart -= 273.15;                         // convert to C

  return steinhart;
}
~~~

### RPM

RPM 轉數是以 *自從上次讀取後的脈波數* 來傳送。

$$
\begin{align*}
RPS_{ESC} = \frac{RPS_{raw}}{0.5 N_{poles} \Delta t} 
\end{align*}
$$

$$
\begin{align*}
RPM_{ESC} = 60 RPS_{ESC}
\end{align*}
$$

$$N_{poles}$$ 極數依馬達而定。T100 為 12 極 而 T200 為 14 極。RPM 測量值 *不包含方向*。您可以透過加入負號來表示反方向。

程式碼範例：

~~~cpp
float rpm() {  
  _rpm = float(_rpm)/((uint16_t(millis())-_rpmTimer)/1000.0f)*60/float(_poleCount);
  _rpmTimer = millis();
}
~~~

## 指定 I<sup>2</sup>C 位址

當使用超過一個 ESC，需要對每一顆 ESC 指定唯一的位址。對 ESC 指派新位址時，必須更新 ESC 的韌體。

**需要工具:**

* 已上傳[ArduinoUSBLinker](https://github.com/bluerobotics/ArduinoUSBLinker) 程式碼的 Arduino 控制板。

1. 首先，確認[ArduinoUSBLinker](https://github.com/bluerobotics/ArduinoUSBLinker) 程式碼已上傳至您的 Arduino 控制板上。可透過 Arduino IDE 來確認。

2. 連接 BlueESC 訊號線的黑色接地線到 Arduino 板上的 "GND" 腳位上。連接紅色或黃色的 PWM 訊號線到 Arduino pin 2。

3. 使用電池或電源供應器對 BlueESC 供電。

4. 下載[最新的 BlueESC firmware zip file](/blueesc/firmware/blueesc_firmware_2015-07-09_a34f109.zip). 解開到合適的位置。 

5. 有數種上傳韌體到 BlueESC 的方式。第一種使用[avrdude](http://www.ladyada.net/learn/avr/setup-win.html) 指令列模式:

~~~~~~~~~~ bash
# Navigate to the location containing the BlueESC firmware files
# Replace XX with the desired ID number 0-15 (0 ,1, 2, 3, etc.)
# Replace [programmer port] with serial programmer port, i.e. COM3
avrdude -c stk500v2 -b 19200 -P [programmer port] -p m8 -U flash:w:blueesc_idXX.hex:i
~~~~~~~~~~~~~~~

第二種方式使用圖形介面程式[KKMulticopterTool](http://lazyzero.de/en/modellbau/kkmulticopterflashtool). 32 與 64 位元版本都可運作。

* 設定程式器為 *ArduinoUSBLinker*
* 選擇 Arduino 連接埠。
* 設定控制器為 *atmega 8-based brushless ESC (8kB flash)* 
* 在 "Flashing" 選單，點擊 "File" 選取希望更新的韌體檔案。
* 點擊綠色鈕開始更新 BlueESC。

<img src="/assets/images/documentation/KKshot1a.png" class="img-responsive" style="max-width:600px" />

If everything went well, this is the message you should see indicating a successful firmware flash:

<img src="/assets/images/documentation/KKshot2a.png" class="img-responsive" style="max-width:600px" />

# Example Code

## Arduino with Servo Library

This example uses the Arduino Servo library to control the speed controller. This provides an update rate of 50 Hz and can use any pin on the Arduino board as the "servoPin".

**Note:** If you power the Arduino before powering the ESC, then the ESC will miss the initialization step and won't start. Power them up at the same time, power the ESC first, or press "reset" on the Arduino after applying power to the ESC.

~~~~~~~~~~ cpp
#include <Servo.h>

byte servoPin = 9;
Servo servo;

void setup() {
	servo.attach(servoPin);

	servo.writeMicroseconds(1500); // send "stop" signal to ESC.
	delay(1000); // delay to allow the ESC to recognize the stopped signal
}

void loop() {
	int signal = 1700; // Set signal value, which should be between 1100 and 1900

	servo.writeMicroseconds(signal); // Send signal to ESC.
}
~~~~~~~~~~~~~~~~

## Arduino with I2C

The following example uses the [Blue Robotics Arduino_I2C_ESC library](https://github.com/bluerobotics/Arduino_I2C_ESC) to control the BlueESC through I2C. 

~~~~ cpp

#include <Wire.h>
#include "Arduino_I2C_ESC.h"

#define ESC_ADDRESS 0x29

Arduino_I2C_ESC motor(ESC_ADDRESS);

int signal;

void setup() {
  Serial.begin(57600);
  Serial.println("Starting");
  
  Wire.begin();
}

void loop() {

  if ( Serial.available() > 0 ) {
    signal = Serial.parseInt();
  }
  
  motor.set(signal);

  motor.update();

  Serial.print("ESC: ");
  if(motor.isAlive()) Serial.print("OK\t\t"); 
  else Serial.print("NA\t\t");
  Serial.print(signal);Serial.print(" \t\t");  
  Serial.print(motor.rpm());Serial.print(" RPM\t\t");
  Serial.print(motor.voltage());Serial.print(" V\t\t");
  Serial.print(motor.current());Serial.print(" A\t\t");
  Serial.print(motor.temperature());Serial.print(" `C");
  Serial.println();

  delay(250); // Update at roughly 4 hz
}
~~~~~~~~~~~~~~~~~~~

# Advanced

## Firmware Files

The compiled firmware files can be downloaded below. This file includes firmware hex files precompiled with 16 different I<sup>2</sup>C addresses.

[<i class="fa fa-download fa-fw"></i> BlueESC Firmware (2015-07-09 a34f109)](/blueesc/firmware/blueesc_firmware_2015-07-09_a34f109.zip)

## Firmware Update and Customization

The Basic ESC uses the [tgy firmware](http://github.com/bluerobotics/tgy) which is open source and editable. There are many parameters that can be changed to change the performance of the speed controller. 

### Firmware Compilation

To compile the firmware, you'll need the avra AVR Assembler.

*Mac:* (Uses Homebrew)

~~~ bash
brew update
brew install avra
make blueesc.hex
~~~

To compile the files with multiple I2C addresses, you can use the following:

~~~ bash
make build_blueesc_addresses
~~~

*Linux (Ubuntu 14 LTS):*

~~~ bash
sudo apt-get install avra
git clone https://github.com/bluerobotics/tgy
cd tgy
make blueesc.hex
~~~

### Firmware Flashing

The ESC includes a bootloader that allows flashing through the PWM signal wire using a programming like the [Turnigy USB Linker](http://www.hobbyking.com/hobbyking/store/__10628__turnigy_usb_linker_for_aquastar_super_brain.html) or the [AfroESC Programmer](http://www.hobbyking.com/hobbyking/store/__39437__afro_esc_usb_programming_tool.html). 

~~~ bash
avrdude -c stk500v2 -b 9600 -P [programmer port] -p m8 -U flash:w:bluesc.hex:i
~~~

<script type="text/javascript" src="http://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>
