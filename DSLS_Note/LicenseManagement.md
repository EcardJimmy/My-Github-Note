# 關於 AutoSAR Builder License 
## 授權管理及使用佔用Port: 4084, 4085

## 安裝
### 安裝啟用非圖形界面管理
- sudo bash ./startInstLicServ -noUI

### 啟用授權服務
- /usr/DassaultSystemes/DSLicenseServer/linux_a64/code/bin/DSLicSrv -startServer

### 關閉授權服務
- /usr/DassaultSystemes/DSLicenseServer/linux_a64/code/bin/DSLicSrv -stopServer

### 圖形界面管理
- /usr/DassaultSystemes/DSLicenseServer/linux_a64/code/bin/DSLicSrv -adminUI

### 非圖形界面管理
- /usr/DassaultSystemes/DSLicenseServer/linux_a64/code/bin/DSLicSrv -admin


## 管理
- 先確定服務為開啟狀態

### 圖形界面
- ./DSLicSrv -adminUI

### 命令行模式
- ./DSLicSrv -admin

### 命令行提示顯示為:
- admin> 

### 幫助:
- admin> ?

- admin> help

### 連結授權伺服器:
- admin>c localhost 4084

### 斷開已連結授權伺服器:
- admin>disc

### 滙入授權檔:
- admin>e -dir inputDir [-file file1 file2...]

- admin>e -dir /home/jimmy/Documents -file 1.LICZ

### Get current license server information:
- admin>gsi

### Show current license usage:
- admin>glu -all >> /home/jimmy/Documents/1.log

### Display logged server messages:
- admin>sl

### Exit the license administration tool:
- admin>quit


## 解除安裝:
- 停止服務:
    - /usr/DassaultSystemes/DSLicenseServer/linux_a64/code/bin/DSLicSrv -stopServer
- 刪除資料夾:
    - rm -rf /usr/DassaultSystemes/DSLicenseServer

## Client端設定
- 在 Windows "C:\ProgramData\DassaultSystemes\Licenses"資料夾

- 在Linux"/var/DassaultSystemes/Licenses"資料夾

- 建檔案:DSLicSrv.txt
    - 例:
        C:\ProgramData\DassaultSystemes\Licenses\DSLIcSrv.txt

- 內容:
    - 192.168.200.33:4085

## 詳細參數請參考DSLS.pdf第162頁


### Jimmy 查詢網卡製造商所得MAC Address
- MAC: F07BCB46391F
- F07BCB	Hon Hai Precision Ind. Co.,Ltd.
