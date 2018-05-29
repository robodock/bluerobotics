---
layout: default
title: Payload Skid Documentation
order: 1
topnavbar: brov2
nav:
- 簡介: 簡介
- 規格: 規格
- - 規格表: 規格表
- - 平面圖: 平面圖
- - 3D模型: 3D模型
- 使用說明: 使用說明
- 組合安裝: 組合安裝

store-links:
- Payload Skid: https://www.bluerobotics.com/store/rov/brov-payload-skid/

manual-links:
- BlueROV2: /brov2/assembly/
---

<img src="/payload-skid/cad/banner-style-1.png" class="img-responsive img-center" style="max-width:800px"  />

# 簡介

 <em>Payload Skid(裝載平台)</em> 是一個供 BlueROV2 使用的模組化的框架，可加掛水密筒、照明燈或其他設備。

# 規格

## 規格表

|  **尺寸重量**  |
| ------------- | --------- |
| 長 | 475 mm | 18 in |
| 寬 | 338 mm | 13.3 in |
| 高 | 197mm | 7.7in |
| 重量 (陸地上) | 1200g | 2.65lbs |
|----------------------|


## 平面圖

<img src="/payload-skid/cad/payload-skid-2view.png" class="img-responsive img-center" style="max-width:800px" />

<img src="/payload-skid/cad/rov-payload-dimensions.png" class="img-responsive img-center" style="max-width:800px" />

## 3D模型

所有 3D 模型皆以壓縮檔方式提供，內有下列檔案格式：

- SolidWorks Part (.sldprt)
- IGES (.igs) 
- STEP (.step)
- STL (.stl)

|		**Payload Skid(擴充裝載平台)**																						|
| --------------------------------------------------------------------------------------------- |
| Payload Skid and Parts  | [BROV-PAYLOAD-SKID-R1.zip](cad/BROV-PAYLOAD-SKID-R1.zip) |

# 使用說明

下列的組態，可以讓 Payload Skid 裝載平台掛載兩個額外的照明燈，12個額外的壓載鉛塊，3 個額外的 3" 水密筒或 1 個 4" 水密筒。您可能會需要增加一些壓載鉛塊來讓 BlueROV2 保持中性浮力，特別是在水密筒內無設備時。下表列出大略需要的壓載鉛塊數量。

|  **建議增加的壓載鉛塊(200g)數量**  |
| ------------- | --------- |
| 1 x 3" 水密筒 (12") | 4-6 | 
| 3 x 3" 水密筒 (12") | 14-16 | 
| 1 x 4" 水密筒 (12") | 10-12 | 
|----------------------|

依據水密筒安裝的位置，也可能需要調整您的 BlueROV2 為略成正向浮力狀態，例如安裝了 3 支 3" 水密筒在裝載平台上時，會些許影響到垂直推進器的向下水流，調整為稍具正向浮力狀態將有助於保持平衡。只在中間安裝一支水密筒時則影響不大。

# 組合安裝

## 步驟 1: 安裝側板

<img src="/payload-skid/cad/payload-step-1.png" class="img-responsive img-center" style="max-width:800px"  />

使用四根 M5x16 螺絲，將側邊板固定到底板上。確定底板螺絲頭埋入擴孔面朝下，側板照明燈固定孔朝前。

## 步驟 2: 安裝拉力桿

<img src="/payload-skid/cad/payload-step-2.png" class="img-responsive img-center" style="max-width:800px"  />

在側板上方使用四根 M4x16 螺絲將拉力桿固定兩片側板。這些拉力桿在裝載架固定到 BlueROV2 本體後是可移除的，不過建議持續裝設以維持較佳的結構強度。

## 步驟 3: 連接片固定 

<img src="/payload-skid/cad/payload-step-3.png" class="img-responsive img-center" style="max-width:800px"  />

將 BlueROV2 放置到擴充裝載平台上，使用八支 M5x16 螺絲固定連接片，固定本體與擴充平台。

## 步驟 4: 安裝水密筒夾

<img src="/payload-skid/cad/payload-step-4.png" class="img-responsive img-center" style="max-width:800px"  />

使用四支 M4x14 螺絲，將水密筒夾安裝置底板上，建議使用螺絲固定膠。

## 步驟 5: 固定水密筒

<img src="/payload-skid/cad/payload-step-5.png" class="img-responsive img-center" style="max-width:800px"  />

使用四支 M3x12 螺絲與另一片筒夾，將水密筒安裝至平台上，記得保持水密筒在正中間位置，固定筒夾時，要兩邊平均施力鎖緊，同樣建議使用螺絲固定膠。若有其他的水密筒，重複步驟4與步驟5，固定水密筒到側板上，裝載平台內的空間可容納三支3"水密筒。

## 步驟 6: 安裝額外的照明燈

<img src="/payload-skid/cad/payload-step-6.png" class="img-responsive img-center" style="max-width:800px"  />

擴充裝載平台已預留一組照明燈安裝孔，使用兩支 M3x12 螺絲來安裝。

## 步驟 7: 卸載擴充平台

<img src="/payload-skid/cad/payload-skid-2.png" class="img-responsive img-center" style="max-width:600px"  />

卸下固定片上的 4 支 M5x16 螺絲即可分離本體與擴充平台，可將固定片保留在擴充平台上，方便下次組裝。
