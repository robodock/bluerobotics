---
layout: default
title: BlueROV2
permalink: /brov2/
order: 1
topnavbar: brov2
nav:
- 簡介: 簡介
- - 特性: 特性
- - 產品包裝內容: 產品包裝內容
- - 您還需要這些: 您還需要這些
- - 相關資源: 相關資源
- 產品規格: 產品規格
- - 尺寸材質: 尺寸材質
- - 性能: 性能
- - 電池: 電池
- - 照明: 照明
- - 連接線: 連接線
- - 傳感器: 傳感器
- - 鏡頭俯仰: 鏡頭俯仰
- - 鏡頭: 鏡頭
- 3D模型: 3D模型
- 使用手冊: 使用手冊
- 勘誤回報: 勘誤回報

store-links:
- BlueROV2: https://www.bluerobotics.com/store/rov/bluerov2/

manual-links:
- Assembly Manual: /brov2/assembly/
- Software Setup: /brov2/software-setup/
- Operation Manual: /brov2/operation/

---

<img src="/brov2/cad/BlueROV2-Honaunau-6.png" class="img-responsive img-center" style="max-width:800px" />

# 簡介

_BlueROV2_ 是世界上價格最親民的高性能 ROV。 六具推進器的設置組態，提供了強大的穩定能力，提供載具穩定、平順的運動性，同時又具備高度操控性。_BlueROV2_ 以基本消費級 ROV 的價格，提供如同高階商用觀測級 ROV 的能力。

<a href="http://bluerobotics.com/downloads/bluerov2.pdf" alt="BlueROV2 Datasheet"><i class="fa fa-download" aria-hidden="true"></i> 資料表下載 </a>

## 特性

- 即時 1080p HD 高畫質影像
- 高度操控性向量推進器組態
- 觀測、檢查與研究級 ROV 任務最佳化
- 易於使用，跨平台使用者介面軟體(支援 Windows, Mac, Linux)
- 3組保留配線穿孔，具高度擴充性
- 標準 100m 工作深度與 300m 連接纜線長度範圍
- 6組 T200 推進器馬達與電子調速器，提供同級產品中最佳之推力重量比
- 鋰電池供電，可快速拆裝交換

## 產品包裝內容

產品送達包裝中包含已預組套件，組裝時間約在 1.5~3 小時間，依操作經驗而定。

[零件清單](/brov2/assembly/#套件內容) 在此。

## 您還需要這些

另外有些操作必要組件，並未包含在套件中：

 - 控制器. 我們推薦使用 [XBox One 遊戲控制器](https://www.microsoft.com/en-us/store/d/xbox-wireless-controller/8vcw8gln9vrf/ljvk?cid=msft_web_collection&activetab=pivot%3atechspecstab) 或是 [Logitech Gamepad](http://gaming.logitech.com/en-us/product/f310-gamepad).
 - 一台筆電或是 Windows 10 平板電腦。控制軟體 QGroundControl 具有 Windows 10, Mac 與 Linux 版本。
 - 鋰電池。 我們推薦 [18Ah Lithium-ion Battery](http://www.bluerobotics.com/store/electronics/batteries/battery-li-4s-18ah-r1/) 或者 2 或 3 個 [這種](http://www.hobbyking.com/hobbyking/store/uh_viewItem.asp?idProduct=56844)
 - 鋰電池平衡充電器, 例如這款 [Lithium Battery Charger](http://www.bluerobotics.com/store/electronics/batteries/lithium-battery-charger/).  

## 相關資源

 - [組裝說明](/brov2/assembly/)
 - [材料清單](/brov2/assembly/#套件內容)
 - [初始軟體設定](/brov2/software-setup)
 - [操作手冊](/brov2/operation)

# 產品規格

## 尺寸材質 

| 長         | 457 mm           | 18 in          |
| 寬         | 338 mm           | 13.3 in        |
| 高         | 254 mm           | 10 in          |
| 陸上重量 (含配重鉛塊)         | 10-11 kg       | 22-24 lb        |
| 陸上重量 (不含配重鉛塊)       | 9-10 kg        | 20-22 lb        |
| 淨浮力 (含配重鉛塊)           | 0.2 kg         | 0.5 lb          |
| 淨浮力 (不含配重鉛塊)         | 1.4 kg         | 3 lb       	   |
| 水密管內徑    | 102 mm        | 4.0 in         |
| 水密管內長度  | 298 mm        | 11.75 in       |
| 纜線穿孔      | 14 x 10mm     | 14 x 0.4 in    |
| 材質      | HDPE 框架, 鋁製蓋板, 壓克力圓管 |
| 主容器管 (電子控制器)      | [Blue Robotics 4 吋管系列/鋁蓋板](http://docs.bluerobotics.com/watertight-enclosures/#specifications-4-series)        |
| 電池容器管                 | [Blue Robotics 3 吋管系列/鋁蓋板](http://docs.bluerobotics.com/watertight-enclosures/#specifications-3-series)        |
| 浮力發泡橡膠               | [R-3318 聚氨脂發泡橡膠](https://www.bluerobotics.com/store/parts/float-r1/) 深度可達 210 公尺              |
| 配重鉛塊            | 6 x [200公克上漆鉛塊](https://www.bluerobotics.com/store/parts/ballast-200g-r1/)                             |
| 電池連接頭		  | XT90                       |

## 性能 

| 最大額定深度                   | 100 m         | 330 ft        |
| 最大測試深度(目前為止)          | 130 m         | 425 ft        |
| 最大前進速度d                  | 1 m/s         | 2 knots       |
| 推進器                        | [Blue Robotics T200](http://docs.bluerobotics.com/thrusters/t200/)            |
| ESC(電子調速器)                                    | [Blue Robotics Basic 30A ESC](http://docs.bluerobotics.com/besc/)   |
| 推進器組態                 | [6 thrusters](http://ardusub.com/images/vectored-frame.png)                   |
|                                        | - 4 向量             | 
|                                        | - 2 垂直             | 
| 縱向推力                | 14 kg<sub>f</sub>      | 30 lb<sub>f</sub>     |
| 垂直向推力              | 9 kg<sub>f</sub>       | 20 lb<sub>f</sub>     |
| 橫向推力                | 14 kg<sub>f</sub>      | 30 lb<sub>f</sub>     |

## 電池

| 電池使用時間 (一般使用)              | ~3 hours w/ [18AH Lithium-ion Battery](http://www.bluerobotics.com/store/electronics/batteries/battery-li-4s-18ah-r1/) |
| 電池使用時間 (輕度使用)              | ~5 hours w/ [18AH Lithium-ion Battery](http://www.bluerobotics.com/store/electronics/batteries/battery-li-4s-18ah-r1/) |

電池可在30秒內完成交換.

## 照明

| 亮度       | 1500 流明，亮度可調整            |
| 光束角度   | 135 degrees, 傾斜度可手動調整    |

## 連結線

| 直徑 | 7.6 mm | 0.30 in |
| 長度 | 25-300 m | 80-980 ft |
| 工作強度 | 45 kg<sub>f</sub> | 100 lb<sub>f</sub> |
| 破斷強度 | 160 kg<sub>f</sub> | 350 lb<sub>f</sub> |
| 強度元件材質 | 防水克維拉(Kevlar)合成纖維 |
| 淡水中浮力 | 中性 |
| 海水中浮力 | 輕微上浮力 |
| 線材導體 | 4 對雙絞線, 26 AWG |

## 傳感器

- 3-DOF 羅盤 (PixHawk內置)
- 3-DOF 加速度計 (PixHawk內置)
- 3-DOF 磁力計 (PixHawk內置)
- 內部氣壓計 (PixHawk內置)
- [Blue Robotics Bar 30 氣壓/深度/溫度 感測器](http://docs.bluerobotics.com/bar30/) (外部) 
- 電流與電壓監測 (PixHawk內置)

## 鏡頭俯仰
					   
| 俯仰範圍            | +/- 90 度 (總範圍 180 度)   | 
| 俯仰控制伺服馬達     | Hitec HS-5055MG           |

## 鏡頭

| 視野 (水下) | 110 degrees (水平)  |                                                      
| 光線敏感度  | 0.01 [lux](https://en.wikipedia.org/wiki/Lux#Illuminance)  |
| 解析度     | 1080p       |

## 控制系統

| 連接線介面     	| [Fathom-X Tether Interface Board](http://docs.bluerobotics.com/fathom-x/)                |
| 控制系統		| [3D Robotics PixHawk](https://www.bluerobotics.com/store/electronics/pixhawk-r1/)         |


# 3D 模型

3D模型檔案龐大，如需觀看或下載，請前往 [checking out the CAD files on GrabCAD](https://grabcad.com/library/bluerov2-1).

# 使用手冊

1. 組裝：請前往查看我們的 [組裝手冊](/brov2/assembly) , 了解詳細的組裝步驟.

2. 軟體設定：如果您的BlueROV2是 **October 24, 2016 之後的版本**, 請使用 [Software Setup Manual](/brov2/software-setup/) 來設定操作電腦端程式. 如果是 **October 24, 2016 之前的版本** 請直接參考 [ArduSub Documentation](http://ardusub.com/introduction/#overview).

3. 操作：詳細內容請參考 [_BlueROV2_ 操作手冊](/brov2/operation).

# 勘誤回報

我們盡可能讓我們的文件、說明書、軟體更好更完善，如果您發現任何錯誤或可改進之處，請不吝通知我們或相關社群，貢獻一己之力。

- **ArduSub Issues:** 有關 ArduSub 軟體，使用 Pixhawk 控制器來控制 ROV 的議題，請回報至 [ArduSub Github Issues Page](https://github.com/bluerobotics/ardusub/issues). 
- **QGroundControl Issues:** 有關 QGroundControl 岸端介面軟體, 搖桿設定, 視訊串流, 等等議題, 請回報至 [QGroundControl Github Issues Page](https://github.com/mavlink/qgroundcontrol/issues).
- **Documentation:** 本文件、操作說明, 英文版請回報至 [Blue Robotics Documentation Github Issues Page](https://github.com/bluerobotics/bluerobotics.github.io/issues). 中文版請回報至 [bluerov.robodock.net Github Issues Page](http://github.com/robodock/bluerov/issues)
