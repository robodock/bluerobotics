---
layout: default
title: Basic ESC Documentation (New)
order: 1
nav:
- 簡介: 簡介
- - 安全守則: 安全守則
- - 快速開始: 快速開始
- 規格: 規格
- - 接線圖: 接線圖
- - 規格表: 規格表
- - 3D模型: 3D模型
- 安裝: 安裝
- - 散熱考量: 散熱考量
- 範例程式碼: 範例程式碼
- - Arduino: arduino
- 進階: 進階
- - 韌體檔案: 韌體檔案

store-links:
- Basic ESC: https://www.bluerobotics.com/store/electronics/besc30-r3/

manual-links:
- T100/T200 Thrusters: /thrusters/
- M100 Motor: /thrusters/motors/
---
<img src="/bescr3/cad/BESC30-R3-3-rotated-crop.PNG" class="img-responsive" style="max-width:600px" />

# 簡介

註: 這裡是最新版的 Basic ESC, 舊版本的文件資料[在此](http://docs.bluerobotics.com/besc/).

最新版的 Basic ESC 是基於 BLHeli_S ESC 的設計，提供新科技的升級，額外的功能與改善效能。Basic ESC 為簡單的無刷馬達控制器(電子調速器)，內有已程式化之韌體，控制馬達正反轉輸出。 BLHeli_S 程式韌體為一開源計畫[Github連結](https://github.com/bitdump/BLHeli/tree/master/BLHeli_S%20SiLabs).

## 安全守則 

<i class="fa fa-exclamation-triangle fa-fw fa-2x text-warning"></i> 在電氣環境中工作時，請隨時注意安全， 確認連頭連結穩固並維持水密。並將身體遠離轉動的馬達、螺槳部位。

## 快速開始

1. 連接三條馬達連接線至馬達上。線與連接點的順序無關，但只要交換其中任兩條就會改變馬達轉動方向。圖中 A、B、C 輸出相位順序是可完全互換的。

2. 連接紅色電源線與黑色接地線至電源(電池)。電源一接通時可聽到 ESC 會發出三響音調漸高的嗶聲，表示三個相位線已連接。

3. 連接訊號線到訊號來源，例如 RC 無線電接收器或為微控制器電路板。白線為訊號(PWM)線。

4. 傳送一個幾秒鐘的停止訊號(脈波佔時 1500毫秒)來啟動 ESC。可聽到兩個聲音表示成功啟動。接下來便可傳送 1100毫秒 ~ 1900毫秒的 PWM 訊號來操作推進器馬達。 

# 規格

## 接線圖

<img src="/bescr3/cad/BESC30-R3-diagram.PNG" class="img-responsive" style="max-width:600px" />

## 規格表

|                 **電力**                |
| ------------- | ------------- | ------------- |
| 電壓       | 7-26 volts (2-6S)             |
| 最大電流 (持續)  | 30 amps (相依於冷卻能力)|
| ------------- | ------------- | ------------- |
|                  **實體**                 |
| ------------- | ------------- | ------------- |
| 長        | 35 mm         | 1.38 in       |
| 寬         | 17.1 mm       | 0.67 in     |
| 高        | 5.5 mm        | 0.22 in      |
| 重量        | 16.3g         | 0.036lb
| 電力線端子 | Spade terminals for No. 6 screw (6號螺絲用U型端子)   |
| 馬達線端子 | 裸線包覆錫       |
| 訊號線端子 | 3-pin 伺服機端子 (0.1" 間距) (接地, 空, 訊號) |
| ------------- | ------------- | ------------- |
|            **脈波寬度訊號**             |
| ------------- | ------------- | ------------- |
| 訊號電壓| 3.3-5 volts                   |
| 最大更新率| 400 Hz                       |
| 停止       | 1500 microseconds             |
| 最大向前   | 1900 microseconds             |
| 最大向後   | 1100 microseconds             |
| 訊號靜區(不工作區)   | +/- 25 microseconds (以 1500 microseconds 為中心) |

## 3D模型

| 檔案格式                  | 連結                          |
| -------------------------- | ----------------------------- |
| SolidWorks Part (.sldprt)  | [BESC30-R3.SLDPRT](/bescr3/cad/BESC30-R3.SLDPRT) |
| STEP (.step)               | [BESC30-R3.STEP](/bescr3/cad/BESC30-R3.STEP)   |
| IGES (.igs)                | [BESC30-R3.IGS](/bescr3/cad/BESC30-R3.IGS) |
| STL (.stl)                 | [BESC30-R3.STL](/bescr3/cad/BESC30-R3.STL) |

# 安裝

## 散熱考量

與所有的 ESCs 一樣，Basic ESC 操作時可能產生可觀的熱能。安裝與操作時皆須納入考慮是否過熱的問題。主要的產熱元件為 MOSFET(金氧半場效電晶體)，位於 ESC 鋁散熱片下方。底下是幾點要訣：

1. 盡可能讓散熱片接觸空氣或者連貼至更大片的散熱片。

2. *請勿* 使用任何會阻礙熱傳導的接著劑，例如家居修繕的矽利康膠。

# 範例程式碼

## Arduino

底下範例使用 Arduino 伺服機程式庫來控制調速器。可提供達 50 Hz 的更新率，並使用任何 Arduino 板上的針腳。

如果您從未使用過 Arduino，建議您可看看[這裡](https://www.arduino.cc/en/Tutorial/HomePage)


**註:** 如果您在供電給 ESC 前先供電啟動 Arduino，ESC 會錯過起始步驟而無法動作。可按下 Arduino 上的 "reset" 鍵，重新啟動 Arduino。另外依據安裝設置的不同，可能會需要調整中間訊號延遲時間。

~~~~~~~~~~ cpp
#include <Servo.h>

byte servoPin = 9;
Servo servo;

void setup() {
	servo.attach(servoPin);

	servo.writeMicroseconds(1500); // send "stop" signal to ESC.
	delay(7000); // delay to allow the ESC to recognize the stopped signal
}

void loop() {
	int signal = 1700; // Set signal value, which should be between 1100 and 1900

	servo.writeMicroseconds(signal); // Send signal to ESC.
}
~~~~~~~~~~~~~~~~

# 進階

## 韌體檔案

BLHeliSuite 的韌體組態設定檔可在這裡下載：

[BR Basic ESC BLHEli_S](cad/BLHeli_BR Basic ESC - R_H_15 - Rev. 16.6 - Multi_170921.ini)

詳細的操作與設定文件：

[BLHeli_S Version 16.x manual](cad/BLHeli_S manual SiLabs Rev16.x.pdf)


## 韌體更新與客製

Basic ESC 使用 16.6 版的 [BLHeli_S firmware](https://github.com/bitdump/BLHeli/tree/master/BLHeli_S%20SiLabs)，韌體為開源專案同時可編輯改寫。透過 PWM 訊號線與下列工具程式，可更改韌體中的許多參數，進而改變調速器的性能。[Turnigy USB Linker](http://www.hobbyking.com/hobbyking/store/__10628__turnigy_usb_linker_for_aquastar_super_brain.html), [AfroESC Programmer](http://www.hobbyking.com/hobbyking/store/__39437__afro_esc_usb_programming_tool.html), or 一塊 Arduino 控制卡。
[BLHeliSuite](https://blhelisuite.wordpress.com/)則可用來存取 ESC 韌體與設定組態。

Basic ESC 使用一顆 SiLabs 微控制器同時具備 Oneshot 125 相容性。(註: Oneshot 125 新一代的 ESC 快速協定) 

