# APP for any devices
###### tags: `Javascript` `HTML` `Python` 

- [ ] 樹苺派系統安裝,Shell程式撰寫(啟動執行),網路設定
- [ ] 網頁伺服器程式撰寫
- [ ] 畫面呈現: HTML+CSS 程式撰寫, 圖形繪製.
- [ ] 動畫製作: Javascript 程式撰寫
- [ ] 參數設定: Javascript 程式撰寫
- [ ] 訊號傳輸: Phthon 程式撰寫

## 命令
**查看IP:** 
- ping raspberrypi.local
- hostname -I

**遠端SSH連線:** ssh pi@192.168.200.219
**raspberry pi 開啟vncserver:** vncserver
**連線Pi AP:**
- WiFi 名稱ssid: GSK_raspi 原為(raspap-webgui)
- WiFi 密碼: ChangeMe
- 樹莓派無線網卡 IP (管理介面網址)：10.3.141.1
- 使用者名稱：admin
- 使用者密碼：GSK 原為(secret)
- DHCP 範圍：10.3.141.50 到 10.3.141.255
- 
**重新啟動Lighttpd服務:** sudo service lighttpd force-reload

**CGI 設定:** /usr/share/doc/lighttpd/cgi.txt

**重看設備端口:** ls -l /dev/tty*

## Reference
### [Raspberry pi4 install](https://www.raspberrypi.org/software/)
### [開機時自動啟動VNCserver](https://sites.google.com/site/rasberrypintust/shu-mei-pai-xiao-ji-qiao/vnc/kai-ji-zi-dong-qi-dong)
### [遠端控制樹莓派](https://ithelp.ithome.com.tw/articles/10235452)
### [固定網路IP](https://www.youtube.com/watch?v=5Ws7kDu00aM&t=667s)
### [使用 Raspberry Pi 架設自己的 AP](https://dotblogs.com.tw/SideProgrammer/2019/02/17/raspberry-pi-set-ap) 
### [raspap-webgui](https://github.com/RaspAP/raspap-webgui) 
- 修改/etc/lighttpd/conf-available/50-raspap-router.conf 中將index.php 改為 index.html, localhost網址即可顯自己的html, 否則為原本ap管理頁面(index.php)
### [Setting up an Apache Web Server on a Raspberry Pi](https://www.raspberrypi.org/documentation/remote-access/web-server/apache.md) 
- 目前因為AP設定使用Lighttpd 所以不使用apache
### [如何使Python与Lighttpd配合使用](https://qastack.cn/raspberrypi/1346/how-to-get-python-to-work-with-lighttpd)
### [樹苺派與arduino通過USB進行通訊](https://blog.csdn.net/qq_18402617/article/details/81414541?utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7Edefault-7.control&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EBlogCommendFromBaidu%7Edefault-7.control)
- 了解樹苺派USB與Serial接口
### [Chart.js - 輕鬆完成資料視覺化](https://ithelp.ithome.com.tw/articles/10188031)

## 功能描述
### 握持偵測
- 同位置正反Sensor同時有感應時為握持狀態
- 於握持狀態時，任一區域雙擊時為功能選擇(音響提示)，再次雙擊為此功能的副功能(開、選擇、關...)
- 同時間只有一個功能處於選擇狀態，但可為多個功能開啟/關閉狀態
- 選擇狀態維持5秒，再次雙擊時再次作用為選擇狀態
- 於握持 & 功能選擇狀態時，滑動向上(逆時針)為[音量調高]
- 於握持 & 功能選擇狀態時，滑動向下(順時針)為[音量調低]
- 上方兩區域滑動時為靜音(作用/取消)
### 離手警示
- 於握持狀態時，顯示地圖及目前開啟功能
- 未握持狀態持續10秒時，閃爍方向盤圖示
- 未握持狀態持續15秒時，閃爍離手(橙色)圖示
- 未握持狀態持續20秒時，閃爍離手(紅色)圖示 + 音響警示
### 方向盤功能
- 正面右上: 音樂功能
- 正面右下: 電話功能
- 背面右上: 語音功能
- 背面右下: 車窗功能
### 軟體界面
- 參數調整
    - 傳輸參數: N,8,1 9600
    - 雙擊/滑動時間設定: 0.5s~1s
    - 離手秒數設定: 5s,10s,15s,20s
    - 方向盤選擇: 不同方向盤的圖片資料夾，未來有新的方向盤加入即可。
- 畫面顯示
    - 大平板顯示
---
## System Engineering
### HIL
:::success
硬體在環 (Hardware-in-the-loop simulation)
:::

> 硬體在環仿真，是一種用於即時嵌入式系統的開發和測試技術。硬體在環仿真提供動態系統模型，可以模擬真實的系統環境，加入相關動態系統的數學表示法，並通過嵌入式系統的輸入輸出將其與仿真系統平台相連。動態系統的數學表示法稱為「受控裝置仿真」，嵌入式系統控制模擬受控裝置，以測試系統
> 硬體在環（HIL）仿真必須包括感測器以及致動器的電子仿真，這些電子仿真是仿真的受控裝置以及待測嵌入式系統的介面。電子仿真感測器的數值是由仿真的受控裝置所控制，再由待測嵌入式系統讀取。待測嵌入式系統會實現控制演算法，改變讓致動器控制訊號。控制訊號的變化就會改變模擬受控裝置的控制輸入以及內部狀態。

例如，防鎖死煞車系統（ABS）開發的HIL仿真平台可能會有以下子系統的仿真受控裝置

* 車輛動力學，例如懸吊系統、輪子、輪胎、俯仰（pitch）、偏擺（yaw）及翻滾（Roll）
* 剎車系統液壓元件的動態
* 道路特性

---

> 在汽車應用當中「硬體在環仿真提供了一台供系統確認級驗證用的虛擬車輛。」，由於在針對引擎控制器的效能及診斷機能評估，若都要在汽車內進行測試，會有耗時、昂貴而且無法重現的問題。HIL仿真可以讓開發者評估新的硬體及軟體對策，滿足品質相的要求以及上市時間的限制。在典型的HIL器中，會用特製的實時處理器處理仿真引擎動態的數學模型，而且I/O單元可以連接車輛的感測器及執行器（多半是高度非線性的元件）。最後將待測的電子控制器（ECU）連接到此系統，再用一些仿真器產生的車輛行為來確認系統的行為。

### Dymola
> Dymola是符合Modelica的解決方案，可以有效地建模和仿真多物理動力系統。 Dymola快速解決了複雜的多學科系統建模問題，這些問題可以包含機械，電氣，電子，液壓，熱，控制，電力或面向過程的特徵和組件的組合。

- 系統研發
- 虛擬驗証
- 使用者體驗
- 基於3D模型
- FMI to AUTOSAR Softwaresow

:::info
CPO : code of plm openess
FMI : functional mockup interface
OSLC :　Open Services for Lifecycle Collaboration
Modelica:　是一種物件導向、聲明式的多領域建模語言，可用於基於組件的複雜系統建模。

:::

- ASim : (AUTOSAR Simulation) enables and early integration/verification of an AUTOSAR system allowing you simulate and test your virtual ECU on your computer.
- The Export Mode allows you exporting virtual ECUs as FMUs (Functional Mock-up Units) based on the FMI-standard.Those can be integrated into other simulation environments supporting the FMI standard (e.g. Dymola, Simulink, Silver) to run a SiL (Software-in-the-Loop) simulation.


















