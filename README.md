# ICND CLI
網路設備操作指令介面


網路作業系統軟體平台適用於 Cisco 各類硬體設備上，它不僅僅提供網路服務，也讓各類網路應用程式得以使用。

# IOS (Internet Operation System)

IOS 提供的網路服務，包括：

- [x] 執行通訊協定

- [x] 設備間連線

- [x] 控制存取

- [x] 可增加介面

# EXEC Session

指令列介面可透過

(1) 設備上的 Console Port 經由網路管理員的終端機進行設定。

(2) VPN + Telnet (遠端連線)

(3) Modem 數據機經 AUX Port 可讓網路管理者遠端進行設定 (現在比較少見)

    使用輔助連接埠連接的數據機，再透過電話撥號連線建立會談。

    需要遠方工程師技術支援時，才需要使用輔助連接埠替代主控台連接埠
    
# Download Software

初次設定，經過開機，完成接線後，網路連線與 IP 設定後沒問題下，可由下列三種來源取得軟體：

* 從 TFTP 伺服器下載設定檔案。

* 從 HTTP 瀏覽器設定。

* 此網路設備設有 IP，並且由 Telnet 遠端設定。

常見指令：

# ?

按下 enter 當執行序開始時，路由器會顯示 hostname> ，表示路由器正在 user 模式，此模式沒有讓使用者能用來控制路由器的指令。

此時輸入 ? ， 此乃 content sensitive help ，能列出使用者模式下的所有指令。

重要指令：

# enable

重要指令只有在 priviledged 模式下方能執行。在 hostname> 後輸入 enable 指令，可輸入相關密碼。
密碼輸入正確後，網路設備將顯示 hostname#，表示從使用者模式轉變成管理者模式。

回 user 模式則在 hostname# 後輸入 disable。

# show

輸入 show ? 可知道此指令的用法，可簡寫 show 為 sh、sho。
而 interface 的簡寫則為 int、inte、inter、interf。

# 啟動與設定交換機

* 歷史歷程暫存器

ctrl + p (previous)

ctrl + n (next)

history

show history

show version

show run (全名 show running-configuration)

# sh int 

show int (全名 show interfaces)

show int status (查看所有介面狀態)

show int 後接 介面 (顯示介面的基本資料)

# sh int eth 0/1 輸出檢視

enabled (active)

10BaseT (port speed)

MAC address

MTU

protocol allowance

# sh ip 輸出檢視

IP address

Subnet Mask

Default Gateway

Mgmet Vlan: 編號

Domain Name:

陳列出伺服器編號與 IP 位址

# conf term 

此為設定交換器的廣域設定模式，必須從 previledge 管理者模式切換而來。

sw(congig)# ? 
//線上輔助功能

sw(config)#hostname + <為此台交換器命名的名稱>

sw(config)#ip address + <IP 位址> + <子網路遮罩> 

# 啟動與設定路由器


(to be continued...)












