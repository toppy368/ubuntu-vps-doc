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

## 疑難排解：Nginx  設定相關注意事項
### Nginx  設定相關注意事項
#### Nginx 設定檔位置    

    /etc/nginx/sites-available/default

你可以選擇用vi或其他編輯器打開此文件，此文件大部分的內容都有英文註解說明每個設定的用途，如果不懂可參考此專案的 [LNMP Installation process](https://github.com/toppy368/ubuntu-vps-doc/blob/master/LNMP%20Installation%20process.md) 文件檔，其中的 **設定Nginx** 章節會有設定內容的大部分詳細說明

另外如果 WordPress 的設定修改其中的內容，建議根據 [Nginx 官網的 WordPress 說明文件](https://www.nginx.com/resources/wiki/start/topics/recipes/wordpress/ )  設定 Nginx 設定檔

#### 設定固定網址  
請找到 **location / {**，並修改以下內容  

    try_files $uri $uri/ /index.php?$args;

 修改之後大概會像這樣  

    location / {
              # WordPress permalinks setup.
              try_files $uri $uri/ /index.php?$args;
    }

之後請記得將本文件存檔

#### 檢查 nginx 設定檔是否有錯誤的指令  

    sudo nginx -t

#### 重新啟動 Nginx  

    sudo systemctl reload nginx
