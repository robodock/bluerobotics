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
- - Performance: performance
- - Battery: battery
- - Lights: lights
- - Tether: tether
- - Sensors: Sensors
- - Camera Tilt: camera-tilt
- - Camera: camera
- 3D Model: 3d-model
- User Manuals: user-manuals
- Issue Reporting: issue-reporting

store-links:
- BlueROV2: https://www.bluerobotics.com/store/rov/bluerov2/

manual-links:
- Assembly Manual: /brov2/assembly/
- Software Setup: /brov2/software-setup/
- Operation Manual: /brov2/operation/

---

<img src="/brov2/cad/BlueROV2-Honaunau-6.png" class="img-responsive img-center" style="max-width:800px" />

# 簡介

_BlueROV2_ 是世界上價格最低的高性能 ROV. 六個推進器的組態設置，提供了強力的穩定能力，提供載具平順穩定性，同時又具有高度操控性。_BlueROV2_ 以基本消費級 ROV 的價格，提供如同高階商用觀測級 ROV 的能力。

<a href="http://bluerobotics.com/downloads/bluerov2.pdf" alt="BlueROV2 Datasheet"><i class="fa fa-download" aria-hidden="true"></i> Download Datasheet</a>

## 特性

- 即時 1080p HD 高畫質影像
- 高度操控性向量推進器組態
- 穩定且為檢查級與研究級 ROV 任務最佳化
- 易於使用，跨平台使用者介面軟體(支援 Windows, Mac, Linux)
- 3組冗餘配線穿孔，具高度擴充性
- 標準 100m 工作深度與 300m 連接纜線長度範圍
- 6組 T200 推進馬達與電子調速器，提供同級產品中最佳之推力重量比
- 鋰聚合物電池供電，可快速拆裝交換

## 產品包裝內容

產品送達包裝中包含已預組套件，組裝時間約在 1.5~3 小時間，依操作經驗而定。

[零件清單](/brov2/assembly/#whats-included) 在此。

## 您還需要這些

另外有些操作必要組件，並未包含在套件中：

 - 遊戲控制器. 我們推薦使用 [XBox One 遊戲控制器](https://www.microsoft.com/en-us/store/d/xbox-wireless-controller/8vcw8gln9vrf/ljvk?cid=msft_web_collection&activetab=pivot%3atechspecstab) 或是 [Logitech Gamepad](http://gaming.logitech.com/en-us/product/f310-gamepad).
 - 一台筆電或是 Windows 10 平板電腦。控制軟體 QGroundControl 具有 Mac, Windows 10, 與 Linux 版本。
 - 鋰聚合物電池。 我們推薦 [18Ah Lithium-ion Battery](http://www.bluerobotics.com/store/electronics/batteries/battery-li-4s-18ah-r1/) 或者 2 或 3 個 [these](http://www.hobbyking.com/hobbyking/store/uh_viewItem.asp?idProduct=56844)
 - 鋰電池平衡充電器, 例如這款 [Lithium Battery Charger](http://www.bluerobotics.com/store/electronics/batteries/lithium-battery-charger/).  

## 相關資源

 - [組裝說明](/brov2/assembly/)
 - [材料清單](/brov2/assembly/#whats-included)
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
| 浮力發泡橡膠               | [R-3318 聚氨脂發泡橡膠](https://www.bluerobotics.com/store/parts/float-r1/) rated to 210 meters                |
| 配重鉛塊            | 6 x [200 g coated lead weights](https://www.bluerobotics.com/store/parts/ballast-200g-r1/)                             |
| 電池連接頭		  | XT90                       |

## Performance 

| Maximum Rated Depth                    | 100 m         | 330 ft        |
| Maximum Tested Depth (so far)          | 130 m         | 425 ft        |
| Maximum Forward Speed                  | 1 m/s         | 2 knots       |
| Thrusters                              | [Blue Robotics T200](http://docs.bluerobotics.com/thrusters/t200/)            |
| ESC                                    | [Blue Robotics Basic 30A ESC](http://docs.bluerobotics.com/besc/)   |
| Thruster Configuration                 | [6 thrusters](http://ardusub.com/images/vectored-frame.png)                   |
|                                        | - 4 Vectored                  | 
|                                        | - 2 Vertical                  | 
| Forward Bollard Thrust                 | 14 kg<sub>f</sub>      | 30 lb<sub>f</sub>     |
| Vertical Bollard Thrust                | 9 kg<sub>f</sub>       | 20 lb<sub>f</sub>      |
| Lateral Bollard Thrust                 | 14 kg<sub>f</sub>      | 30 lb<sub>f</sub>      |

## Battery

| Battery Life (Normal Use)              | ~3 hours w/ [18AH Lithium-ion Battery](http://www.bluerobotics.com/store/electronics/batteries/battery-li-4s-18ah-r1/) |
| Battery Life (Light Use)               | ~5 hours w/ [18AH Lithium-ion Battery](http://www.bluerobotics.com/store/electronics/batteries/battery-li-4s-18ah-r1/) |

The batteries can be changed in about 30 seconds.

## Lights

| Brightness       | 1500 lumens each with dimming control                  |
| Light Beam Angle | 135 degrees, with adjustable tilt                    |

## Tether

| Diameter | 7.6 mm | 0.30 in |
| Length   | 25-300 m | 80-980 ft |
| Working Strength | 45 kg<sub>f</sub> | 100 lb<sub>f</sub> |
| Breaking Strength | 160 kg<sub>f</sub> | 350 lb<sub>f</sub> |
| Strength Member | Kevlar with waterblock |
| Buoyancy in Freshwater | Neutral |
| Buoyancy in Saltwater | Slightly Positive |
| Conductors | 4 twisted pairs, 26 AWG |

## Sensors

- 3-DOF Gyroscope (on the PixHawk)
- 3-DOF Accelerometer (on the PixHawk)
- 3-DOF Magnetometer (on the PixHawk)
- Internal barometer (on the PixHawk)
- [Blue Robotics Bar 30 Pressure/Depth and Temperature Sensor](http://docs.bluerobotics.com/bar30/) (external) 
- Current and Voltage Sensing (included with the PixHawk)

## Camera Tilt
					   
| Tilt Range                 | +/- 90 degree camera tilt (180 total range)                                             | 
| Tilt Servo                 | Hitec HS-5055MG         |

## Camera

| Field of View (Underwater) | 110 degrees (horizontal)                                                              |                                                      
| Light Sensitivity          | 0.01[lux](https://en.wikipedia.org/wiki/Lux#Illuminance)                              |
| Resolution                 | 1080p                                                                                 |

## Control System

| Tether Interface Board              	| [Fathom-X Tether Interface Board](http://docs.bluerobotics.com/fathom-x/)                |
| Control System 						| [M Robotics PixHawk](https://www.bluerobotics.com/store/electronics/pixhawk-r1/)         |


# 3D Model

These are BIG files since the model is fairly complex. If you just want to check out a 3D view or 3D models of the BlueROV, we recommend [checking out the CAD files on GrabCAD](https://grabcad.com/library/bluerov2-1).

# User Manuals

1. Please look at our [Assembly Manual](/brov2/assembly) for more detailed assembly instructions.

2. If you **received your BlueROV2 after October 24, 2016**, please look at our [Software Setup Manual](/brov2/software-setup/) for more details on setting up your topside computer. If you **received your BlueROV2 prior to October 24, 2016** please look at our [ArduSub Documentation](http://ardusub.com/introduction/#overview) for more details on the control software.

3. Please look at our [_BlueROV2_ Operating Manual](/brov2/operation) for a detailed operating manual.

# Issue Reporting

We're always trying to make our documentation, instructions, software, and user experience better. If you're having an issue with anything, please report it so that we can address it as soon as possible! Here's where to do that depending on what's wrong:

- **ArduSub Issues:** For anything related to the ArduSub software that runs on the Pixhawk and controls the ROV, reports issues on the [ArduSub Github Issues Page](https://github.com/bluerobotics/ardusub/issues). If you're unsure where your issue should be posted, you can report it here.
- **QGroundControl Issues:** For anything related to the QGroundControl software, joystick setup, video streaming, etc., please report an issue on the [QGroundControl Github Issues Page](https://github.com/mavlink/qgroundcontrol/issues).
- **Documentation:** For anything related to the documentation and instructions here, please report an issue on the [Blue Robotics Documentation Github Issues Page](https://github.com/bluerobotics/bluerobotics.github.io/issues).


