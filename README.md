# ICND CLI
網路設備操作指令介面

網路作業系統軟體平台適用於 Cisco 各類硬體設備上，它不僅僅提供網路服務，也讓各類網路應用程式得以使用。

# IOS (Internet Operation System)

IOS 提供的網路服務，包括：

- [x] protocol 執行通訊協定

- [x] connection 設備連線

- [x] access 控制存取

- [x] interfaces(if) 增加介面

# EXEC Session

指令列介面可透過 console port 控制埠或是 aux port 輔助連接埠。

(1) 設備上的 Console Port 經由網路管理員的終端機進行設定。

(2) VPN + Telnet (遠端連線)

(3) Modem 數據機經 AUX Port 可讓網路管理者遠端進行設定 (現在比較少見)

    使用輔助連接埠連接的數據機，再透過電話撥號連線建立會談。

    需要遠方工程師技術支援時，才需要使用輔助連接埠替代主控台連接埠
    
# Download Software

初次設定，經過開機，完成接線後，網路連線與 IP 設定後沒問題下，可由下列三種來源取得軟體：

* 從 TFTP 伺服器下載設定檔案。

      //敬請先行確認遠端伺服器存儲空間和路由器的記憶體大小是否足夠。
      //#erase flash 能夠清除記憶體讓空間變大。
      //udp封包傳輸時會顯示驚嘆號" ! "每個封包傳輸成功會顯示一個驚嘆號。

      //先行確定有連上遠端伺服器。
      #copy flash tftp
      //將映像檔案備份至網路伺服器。
      //需要輸入來源檔名、遠端伺服器IP位址或名稱、目的地檔名。
      
      #copy tftp flash
      //將映像檔從遠端伺服器還原至快閃記憶體。
      //輸出將顯示 accessing ftp:// <IP address>/<destination file name>
      //flash(快閃記憶體檔案系統)、ftp(網路檔案系統或是使用檔案傳輸通訊協定的網路伺服器)、http 代表在網路中的某項設備內
      //其它尚有任何讀寫資料的終端 endpoint 如：
      //NVRAM、ROM、Modems 的 MUX 介面、BRI 的 MUX 介面，
      //Raw Memory System。
      
https://github.com/QueenieCplusplus/ICND_IFS/blob/master/README.md
      
* 從 HTTP 瀏覽器設定。

download -> 
         
 decompress ->
  
   load -------->

      //無論從何處遠端下載 ISO 映像檔案，
      //都必須先行解壓縮至快閃記憶體 flash 中，
      //並且要成功地載入 RAM 中，方才能執行。

* 此網路設備設有 IP，並且由 Telnet 遠端設定。

常見指令：

# ?

此時輸入 ? ， 此乃 content sensitive help ，能列出使用者模式下的所有指令。

# enter

按下 enter 當執行序開始時，路由器會顯示 hostname> ，表示路由器正在 user 模式，此模式沒有讓使用者能用來控制路由器的指令。

# enable

重要指令只有在 priviledged 模式下方能執行。在 hostname> 後輸入 enable 指令，可輸入相關密碼。
密碼輸入正確後，網路設備將顯示 hostname#，表示從使用者模式轉變成管理者模式。

回 user 模式則在 hostname# 後輸入 disable。

# show

輸入 show ? 可知道此指令的用法，可簡寫 show 為 sh、sho。
而 interface 的簡寫則為 int、inte、inter、interf。

# 啟動與設定交換機

* 歷史歷程暫存器 (buffer)

        ctrl + p (previous)

        ctrl + n (next)

        history

        show history

        show version

        show run (全名 show running-configuration)
        
        terminal history size (設定暫存器大小)

# sh int 

        show int (全名 show interfaces)

        show int status (查看所有介面狀態)

        show int 後接 介面 (顯示介面的基本資料)

# sh int eth 0/1 輸出檢視

    介面的編號格式為：<連接方式> <插槽編號> / <連接埠號>

- [x] enabled (active)

- [x] 10BaseT (speed)

- [x] MAC address

- [x] MTU

- [x] protocol 

# sh ip 輸出檢視

- [x] IP address

- [x] Subnet Mask

- [x] Default Gateway

- [x] Mgmet Vlan: 編號

- [x] Domain Name: 陳列出伺服器編號與 IP 位址

# conf term 

此為設定交換器的廣域設定模式，必須從 previledge 管理者模式切換而來。

        sw(config)
        //注意身份切換後的游標顯示方式，從 user -> previledge -> congfig

        sw(config)# ? 
        //線上輔助功能

        sw(config)#hostname + <為此台交換器命名的名稱>

        sw(config)#ip address + <IP 位址> + <子網路遮罩> 
        //替網路設備如交換器配置IP位址的情境有：
        //Telnet遠端登入
        //或是藉由 SNMP (簡易網路管理通訊協定) 管理此台網路設備。 

# 啟動與設定路由器

使用角色權限

    #enable password + <密碼>
    //為路由器設定密碼
    
    #enable secret + <密碼>
    //為密碼加密。
    
    #no enable secret + <密碼>
    //解除密碼設定。
   
    #service password-encryption
    //一般模式下，為伺服器設定檔的密碼加密。
    
為路由器對外連結做登入設定：從控制埠登入路由器。

    (config)#line console 0
    // 由全域(此刻為管理者模式)模式進入 line 模式。
    // console = 控制台
    
    (config-line)#login 
    (config-line)#password + <密碼>
    
https://www.misterq.cc/web-application/self-study/what-is-console/
    
為路由器對外連結做登入設定：從遠端登入(如 Telnet)路由器。

    (config)#line vty 04
    // vty = Virtual Type Terminal 虛擬終端機。
    // 數字04 代表已經開啟 0~4 個 vty 連線。
    
    (config-line)#password + <密碼>
   
常見的檢視路由設定之指令

    #sh int
    
    #show int serial 0
    
    (config-if)#config term
    //游標變化如上
    // if = 介面縮寫
    
    #exit
    
設定路由介面的頻寬

    #bandwidth 64

設定路由介面的時脈

    #clock rate 64000
    
讓控制埠無限期的開放，略過原本設定的安全機制，避免執行序逾時斷線。

    (config)#line console 0
    (config-line)#exec-timeout 0 0
    // 效果如同指令 no exec-timeout
    
讓輸入內容和輸出訊息不結成一塊，能各自成行。

    (config-line)#logging synchronous
    
# Case Sensitive 

為網路設備如交換器或是路由器設定密碼，要注意英文字母大小寫是有區別的。

# Terminal Editing

開啟加強版的編輯模式，要從管理者模式下啟動。

    (config)# terminal editing
    
* editing cmd set 

ctrl + a 移至該行起點。

ctrl + e 移至該行終點。

ctrl + f 將游標前移動一個字元。

ctrl + b 將游標後移動一個字元。

esc + f 將游標前移動一個字。

esc + b 將游標後移動一個字。

ctrl + d 刪除一個字元。

ctrl + k 刪除游標後的一行字。

ctrl + w 刪除游標前的一行字。

ctrl + u 刪去一整行。

ctrl + r 清除指令列內容至游標的位置。

backspace 刪除游標左側的一個字元。

tab 完成一個僅輸入的部分，但要能提供 IOS 辨識。

編輯指令集

# Clock 

設定路由器的計時器。

    #clocl ?
    //加上空格與問號，藉以進一步得知指令用法之提示。

    #clock set <hr:min:sec> <date> <month> <year>
    //範例如 clock set 16:41:56 18 June 2020
    
# ^

語法檢查時，會以次方符號提示何處發生錯誤。
    
# Ref Doc

https://david50.pixnet.net/blog/post/45217572-%5B筆記%5Dcisco基本指令-密碼設定


