---
layout: default
title: BlueROV2 Software Setup
permalink: /brov2/software-setup/
order: 1
topnavbar: brov2
nav:
- 軟體說明: 軟體說明
- 安裝QGroundControl: 安裝-QGroundControl
- 網路環境設定: 網路環境設定
- 控制器設定: 控制器設定
- 控制器-搖桿校正: 控制器-搖桿校正
- 按鍵設定: 按鍵設定
- 感測器校正: 感測器校正
- 設定推進器方向: 設定推進器方向
- 電壓與電流量測設定: 電壓與電流量測設定
- 水密洩漏偵測警報設定: 水密洩漏偵測警報設定
- 首航測試!: 首航測試!
- 勘誤回報: 勘誤回報

store-links:
- BlueROV: https://www.bluerobotics.com/store/rov/bluerov2/

manual-links:
- BlueROV2 Specifications: /brov2/
- Assembly Manual: /brov2/assembly/
- Operations Manual: /brov2/operation/
---

<script>
	var blacklistElements = []
	var osSpecificElements = []
	var osSpecific = ['install-qgroundcontrol',
		'network-setup',
		'joystick-setup']
		
$(document).ready(function(){
	// initialize collapse state
	$('#windowsDiv').collapse({toggle: false});
	$('#macDiv').collapse({toggle: false});
	$('#linuxDiv').collapse({toggle: false});
	
	// We don't show these sidebar-nav items until the user selects an OS
	var blacklist = ['Install QGroundControl',
	'Network Setup',
	'Joystick Setup',
	'Joystick Calibration',
	'Button Setup',
	'Sensor Calibration',
	'Configure Motor Directions',
	'Voltage and Current Measurement Setup',
	'SOS Leak Sensor Setup',
	'To The First Dive!']
	
	var sidebar = document.getElementById('sidebar');
	var children = sidebar.getElementsByTagName("a");

	for (var i = 0; i < children.length; i++) {
		var child = children[i];
		blacklist.forEach(function(item) {
			if (child.innerHTML == item) {
				blacklistElements.push(child);
			}
		});
		
		osSpecific.forEach(function(item) {
			if (child.href.split('#')[1] == item) {
				console.log('match', child);
				// Careful!, indices not guaranteed for modification step later on
				osSpecificElements.push(child);
			}
		});
	}
	
	// Hide these guys
	for (var i = 0; i < blacklistElements.length; i++) {
		var element = blacklistElements[i];
		element.style.display = "none";
	}	
});

function showBlacklistElements(os) {
	
	// Edit sidebar-nav links for headings repeated in each OS section
	for (var i = 0; i < osSpecificElements.length; i++) {
		var element = osSpecificElements[i];
		
		// Careful!, indices might not actually line up correctly
		element.href = "#" + osSpecific[i] + os;
	}
	
	// Show navigation options after OS selection
	for (var i = 0; i < blacklistElements.length; i++) {
		var element = blacklistElements[i];
		
		element.style.display = "block";
	}
}
</script>

<img src="/brov2/cad/ROV-scuba-1.png" class="img-responsive img-center" style="max-width:800px" />

# 軟體說明

要開始使用 BlueROV2 前，需要一部用來連接 BlueROV2 的電腦，並安裝相關軟體。如果您還沒完成 BlueROV2 的組裝，請參考 [Assembly Manual](/brov2/assembly/) 先完成 BlueROV2 組裝.

請選擇您電腦使用的作業系統查看對應的步驟說明：

<a class="btn btn-default" href="#software-introduction" onclick="{ $('#windowsDiv').collapse('show'); $('#macDiv').collapse('hide'); $('#linuxDiv').collapse('hide'); $('#commonDiv').collapse('show'); showBlacklistElements(''); }">Windows</a>
<a class="btn btn-default" href="#software-introduction" onclick="{ $('#macDiv').collapse('show'); $('#linuxDiv').collapse('hide'); $('#windowsDiv').collapse('hide'); $('#commonDiv').collapse('show'); showBlacklistElements('-1'); }">Mac</a>
<a class="btn btn-default" href="#software-introduction" onclick="{ $('#linuxDiv').collapse('show'); $('#macDiv').collapse('hide'); $('#windowsDiv').collapse('hide'); $('#commonDiv').collapse('show'); showBlacklistElements('-2'); }">Linux</a>

<div id="windowsDiv" class="collapse" markdown="1">

# 安裝 QGroundControl

QGroundControl 是您的地面站控制軟體，可用來連接您的電腦到 BlueROV2，可在此下載後進行安裝:

- [Windows](https://s3.amazonaws.com/downloads.bluerobotics.com/QGC/QGroundControl-installer.exe)

# 網路環境設定

您的電腦需要有乙太網路連接埠，如果您的筆電沒有，您可能會需要這種 [USB to Ethernet 轉接器](https://www.amazon.com/Cable-Matters-Ethernet-Network-Adapter/dp/B00ET4KHJ2)

**網路組態**

1. 前往 _控制台_ > _網路和共用中心_ 然後選取"變更介面卡設定".

	<img src="/brov2/cad/network-and-sharing-center-annotated.png" class="img-responsive img-center" style="max-width:800px" />

2. 右鍵選取網路介面卡, 選擇 _內容_.

	<img src="/brov2/cad/network-connections-annotated.png" class="img-responsive img-center" style="max-width:800px" />

3. 在內容對話框中, 選取 _Internet Protocol Version 4 (TCP/IPv4)_, 然後選取 _內容_.

	<img src="/brov2/cad/internet-protocol-version-4-annotated.png" class="img-responsive img-center" style="max-width:800px" />

4. 選取 "使用下列 IP 位址"，在 IP 位址欄中輸入 192.168.2.1 , 子網路遮罩為 255.255.255.0 ，完成後按下確定.

	<img src="/brov2/cad/static-ip-annotated.png" class="img-responsive img-center" style="max-width:800px" />

**防火牆**

1. 前往 _控制台_ > _Windows 防火牆_ 然後選擇 "允許程式或功能通過 Windows 防火牆".

2. 選取 "變更設定" 然後勾選 "Open source ground control app provided by QGroundControl dev team" or "QGroundControl".

	<img src="/brov2/cad/windows-firewall-annotated.png" class="img-responsive img-center" style="max-width:800px" />

# 控制器設定

**XBox 360 控制器** 

- Plug and Play 隨插即用

**XBox One 控制器** 

- 有線款: 隨插即用 
- 無線款: 
	1. 須接上 [Microsoft XBox Wireless Adapter for Windows](https://www.amazon.com/Microsoft-Xbox-Wireless-Adapter-Windows-one/dp/B00ZB7W4QU).
	2. 打開控制器, 然後按下控制器頂端的無線配對按鍵.

**羅技控制器 (F710 and F310)**

請將羅技控制器後方的選擇開關切至 "X" 位置.
</div>

<div id="macDiv" class="collapse" markdown="1">

# 安裝 QGroundControl

QGroundControl 是您的地面站控制軟體，可用來連接您的電腦到 BlueROV2，Mac 版可在此下載後進行安裝:

- [Mac](https://s3.amazonaws.com/downloads.bluerobotics.com/QGC/QGroundControl.dmg)

# 網路環境設定

您的電腦需要有乙太網路連接埠，如果您的筆電沒有，您可能會需要這種 [USB to Ethernet 轉接器](https://www.amazon.com/Cable-Matters-Ethernet-Network-Adapter/dp/B00ET4KHJ2)

**網路組態**

1. 前往 _System Preferences_ > _Network_

2. 如果您的 Mac 電腦具有網路埠, 請選取左方選項中的 Ethernet. 如果你用的是 USB 網路連接器, 請接上並選取它.

3. 選擇 "Configure IPv4" 旁的下拉選單然後選擇 "Manually"

4. IP Address 請輸入 192.168.2.1 ，子網路遮罩為 255.255.255.0 ，完成後選取 apply.

	<img src="/brov2/cad/mac-network-settings-annotated.png" class="img-responsive img-center" style="max-width:800px" />

# 控制器設定

**XBox 360 控制器**

1. 下載 [驅動程式](https://github.com/360Controller/360Controller/releases/download/v0.16.5/360ControllerInstall_0.16.5.dmg). 有關驅動程式的詳細資料，請看 [Readme.](https://github.com/360Controller/360Controller#about)
2. 安裝 XBox 360 控制器驅動程式.
2. 接上 Windows XBox 360 無線接收器.
3. 打開 XBox 360 控制器.

**XBox One 控制器**
目前尚不支援無線款.

1. 下載 [驅動程式](https://github.com/360Controller/360Controller/releases/download/v0.16.5/360ControllerInstall_0.16.5.dmg). 有關驅動程式詳細資料，請看 [Readme.](https://github.com/360Controller/360Controller#about)
2. 安裝 XBox 360 控制器驅動程式.
2. 使用 micro USB 線連接 XBox One 控制器到電腦.
3. 打開 XBox One 控制器.

**羅技控制器 (F710 and F310)**

請將羅技控制器後方的選擇開關切至 "X" 位置.
</div>

<div id="linuxDiv" class="collapse" markdown="1">

# 安裝 QGroundControl

QGroundControl 是您的地面站控制軟體，可用來連接您的電腦到 BlueROV2，Linux 版可在此下載後進行安裝:

- [Linux](https://s3.amazonaws.com/downloads.bluerobotics.com/QGC/QGroundControl.AppImage)

# 網路環境設定

您的電腦需要有乙太網路連接埠，如果您的筆電沒有，您可能會需要這種 [USB to Ethernet 轉接器](https://www.amazon.com/Cable-Matters-Ethernet-Network-Adapter/dp/B00ET4KHJ2)

**網路組態**

以下說明以 Ubuntu 環境為例，其他 Linux 版本圖形介面略有不同，請自行類推.

1. 選取上方工具列的網路圖示, 選取 "Edit Connections..." 編輯連線

	<img src="/brov2/cad/linuxsetup/LinuxStep1.png" class="img-responsive img-center" style="max-width:800px" />

2. 點選 "Add" 新增

	<img src="/brov2/cad/linuxsetup/LinuxStep2.png" class="img-responsive img-center" style="max-width:800px" />

3. 選擇 "Ethernet" 連接形式，點選 "Create..." 建立

	<img src="/brov2/cad/linuxsetup/LinuxStep3.png" class="img-responsive img-center" style="max-width:800px" />

4. 從 "Device MAC Address" 下拉選單, 選擇您使用的 ethernet 介面. 如果使用的是電腦主機內建的網路卡，則只有一個選項。如果使用的是 USB 網路卡，則可以比對接上前與接上後出現的選項，找出對應的網卡.

	<img src="/brov2/cad/linuxsetup/LinuxStep4.png" class="img-responsive img-center" style="max-width:800px" />

5. 點擊 "IPv4 Settings" 頁面, 從 "Method" 下拉選單中, 選取 "Manual". 點擊 "Add", IP 位址輸入 192.168.2.1，網路遮罩 255.255.255.0 ，閘道 0.0.0.0 完成後按下 "Save..." 儲存設定.

	<img src="/brov2/cad/linuxsetup/LinuxStep5.png" class="img-responsive img-center" style="max-width:800px" />

# 控制器設定

有線款的 Xbox 360 控制器與羅技控制器，相關驅動程式都已內建在 Ubuntu 14.04 與 Ubuntu 16.04 版本中，隨插即用!

**羅技控制器 (F710 and F310)**

請將羅技控制器後方的選擇開關切至 "X" 位置.
</div>
<div id="commonDiv" class="collapse" markdown="1">

# 控制器-搖桿校正

某些控制器/搖桿可能需要校正後才能使用. 如果 QGroundControl 軟體的 *Vehicle Settings* 頁面上的 *Joystick* 頁面呈現紅色，表示控制器/搖桿需要校正，請依照下列步驟進行校正，如果不需校正，則可省略下列步驟!

1. 前往 QGroundControl 軟體的 *Vehicle Settings* 頁面, 點擊在左方邊欄呈現紅色的 *Joystick* 頁面.

2. 確定 'TX Mode' 選項設定在 3.

3. 點擊 "Calibrate", 然後按下 "Next".
 
4. 跟隨 step-by-step 的步驟, 依照畫面指示移動搖桿.

完成時，*Joystick* 頁面將不在呈現紅色, 控制器頁面的 *Enabled* checkbox 選項應為已選取狀態.

# 按鍵設定

BlueROV2 的控制器按鍵預設對應如下圖：

<img src="/brov2/cad/joystick-defaults.png" class="img-responsive img-center" style="max-width:800px" />

這些按鍵可以在 *Vehicle Settings* 頁面上的 *Joystick* 頁面中進行設定.

# 感測器校正

1. 前往 QGroundControl 的 *Vehicle Settings* 頁面，從左方滑動選項頁面中選擇紅色 _Sensors_ 頁面.
2. 在 *Autopilot Orientation* 選項中選擇 `Roll90`.
3. 點擊 _Accelerometers_ 依照指示進行動作.
4. 點擊 _Compass_ 並依照指示進行動作.

完成後，_Sensors_ 頁面將不再呈現紅色.

# 設定推進器方向

在使用 BlueROV2 前，必須確定所有的推進器方向都正確.

<i class="fa fa-exclamation-triangle fa-fw fa-2x text-warning"></i>在 BlueROV2 進入待機狀態後(armed) 請確保身體與衣物遠離推進器螺槳.

<i class="fa fa-exclamation-triangle fa-fw fa-2x text-warning"></i>**請勿** 讓推進器在空中空轉超過30秒.

1. 設定飛行模式(flight mode)為手動 "Manual".

2. 按下控制器 "Start" 鍵讓 BlueROV2 進入待機狀態.

3. 移動控制器左側搖桿向前，檢查所有推進器方向是否正確。此時吹出的氣流應該全部流向機體後方。如果當中有錯誤的，前往 QGroundControl 的 _Settings_ 頁面, 然後前往 _Parameters_ ，選擇 _MOT_. 選擇方向錯誤的推進器後從右側下拉選單中更改方向。

	<img src="/brov2/cad/configure-motor-directions-annotated.png" class="img-responsive img-center" style="max-width:800px" />

4. 移動控制器右側搖桿向前，檢查垂直推進器方向是否正確。此時吹出的氣流應流向機體下方。如果當中有錯誤的，前往 QGroundControl 的 _Settings_ 頁面, 然後前往 _Parameters_ ，選擇 _MOT_ ， 選擇方向錯誤的推進器後從右側下拉選單中更改方向。

# 電壓與電流量測設定 

預設的電池電壓電流量測設定是為 [Multistar High Capacity 4s 10,000mAh](http://www.hobbyking.com/hobbyking/store/uh_viewItem.asp?idProduct=56844) 電池所設. 如果您使用的是不同的電池, 您可以自行調整電壓與電流設定值，請前往 _Settings_ 選擇 _Power_. 需要改變的只有一項 "Battery capacity", 請直接輸入大小數值.

<img src="/brov2/cad/current-monitoring-setup.PNG" class="img-responsive img-center" style="max-width:800px" />

# 水密洩漏偵測警報設定

在 Safety 頁面，選擇 "Pixhawk Aux6" 作為洩漏偵測器連接腳位，並設定邏輯為在乾燥狀態時為 "Low"。

<img src="/sos/cad/sos-software.png" class="img-responsive" style="max-width:800px"  />

# 首航測試! 

電腦端設定到此完成! 接下來請參考 [操作手冊](/brov2/operation/) 來完成首航前的準備工作!

</div>

# 勘誤回報

我們盡可能讓我們的文件、說明書、軟體更好更完善，如果您發現任何錯誤或可改進之處，請不吝通知我們或相關社群，貢獻一己之力。

- **ArduSub Issues:** 有關 ArduSub 軟體，使用 Pixhawk 控制器來控制 ROV 的議題，請回報至 [ArduSub Github Issues Page](https://github.com/bluerobotics/ardusub/issues). 
- **QGroundControl Issues:** 有關 QGroundControl 岸端介面軟體, 搖桿設定, 視訊串流, 等等議題, 請回報至 [QGroundControl Github Issues Page](https://github.com/mavlink/qgroundcontrol/issues).
- **Documentation:** 本文件、操作說明, 英文版請回報至 [Blue Robotics Documentation Github Issues Page](https://github.com/bluerobotics/bluerobotics.github.io/issues). 中文版請回報至 [bluerov.robodock.net Github Issues Page](http://github.com/robodock/bluerov/issues)





