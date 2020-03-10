#  快速安裝 WordPress

## 前置條件
 1. 請安裝 LAMP 或 LNMP 網頁伺服器
 2. 請設定好 SQL 帳號並產生空的資料庫， WordPress 的安裝過程中，或填寫  wp-config.php 時需要這些連線資訊。


## 下載 WordPress  

###  切換到網站根目錄
    cd /var/www/html

### 下載並解壓縮

    wget https://tw.wordpress.org/wordpress-5.2.2-zh_TW.tar.gz  
    tar -xzvf wordpress-5.2.2-zh_TW.tar.gz  

請將下載網址更新成官網的最新版本
最新版本請參考此頁面：https://tw.wordpress.org/download/releases/  

接下來請修改nginx根目錄位置並填寫 wp-config.php 以完成安裝， wp-config.php 的填寫方法請對照 wp-config-sample.php 。（日後繼續更新此檔將說明）


#### 設定權限

若 WordPress 在安裝與更新套件過程中提示需要填入連線資訊，表示該程式沒有取得對外下載檔案的權限，此時應該設定權限

    sudo chown -R www-data:www-data /var/www/html

## 疑難排解：若發生異常，查詢各種錯誤紀錄的存放地點
若發生異常，若 WordPress 沒有產生任何錯誤訊息，但是卻出現不可預期的錯誤，例如 Nginx 出現 http 錯誤（通常會有代碼例如或404或其他），或是網頁畫面呈現全白（這是 PHP 的安全設計，最新的 PHP 不會將錯誤訊息提示在網頁上避免有人利用此錯誤進行攻擊。），此時 **你需要調閱紀錄檔來找線索並解決此錯誤**，這動作稱之為 **Debug** 也就是 **修正程式碼錯誤** 。

若懷疑疑似被駭客/黑客/惡意程式攻擊網站，也需要使用這些紀錄來調查異常狀態發生的原因，加以補強網站的結構預防下次出現異常。

### Log 紀錄存放資料夾

    /var/log

這是專門存放各種程式產生 log 存取或錯紀錄的資料夾

### PHP 紀錄的存放位置

    /var/log/php7.x-fpm.log

這裡 7.x 請依照實際需求對照，若你的版本為 7.2 就會顯示 php7.2fpm.log ，依此類推。

### Nginx 錯誤紀錄存放位置

    /var/log/nginx/error.log

錯誤紀錄， Nginx 的異常資訊，甚至是部份 PHP 的異常也會顯示在這檔案

### Nginx 網站訪問紀錄的存取位置

    /var/log/nginx/access.log

訪問紀錄，俗稱電磁紀錄，可以知道哪些ip開啟了網站的哪些功能。

## 疑難排解：Nginx  設定相關注意事項

### Nginx  設定相關注意事項
#### Nginx 設定檔位置    

    /etc/nginx/sites-available/default

你可以選擇用vi或其他編輯器打開此文件，此文件大部分的內容都有英文註解說明每個設定的用途，如果不懂可參考此專案的 [LNMP Installation process](https://github.com/toppy368/ubuntu-vps-doc/blob/master/LNMP%20Installation%20process.md) 文件檔，其中的 **設定Nginx** 章節會有設定內容的大部分詳細說明

另外如果 WordPress 的設定修改其中的內容，建議根據 [Nginx 官網的 WordPress 說明文件](https://www.nginx.com/resources/wiki/start/topics/recipes/wordpress/ )  設定 Nginx 設定檔

#### 設定固定網址  
請找到 **location / {**，並修改以下內容，如果透過 **VIM** 編輯器開啟設定檔，可以直接用 **/location / {** 搜尋該字元   

    try_files $uri $uri/ /index.php?$args;

 修改之後大概會像這樣  

    location / {
              # WordPress permalinks setup.
              try_files $uri $uri/ /index.php?$args;
    }

之後請記得將本文件存檔， **若是 VIM** 請輸入 **:** 進入指令模式並輸入 **qw** 存檔並離開

#### 檢查 nginx 設定檔是否有錯誤的指令  

    sudo nginx -t

#### 重新啟動 Nginx  

    sudo systemctl reload nginx
