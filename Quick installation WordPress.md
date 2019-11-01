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

最新版本請參考此頁面：https://tw.wordpress.org/download/releases/  

接下來請修改nginx根目錄位置並填寫 wp-config.php 以完成安裝， wp-config.php 的填寫方法請對照 wp-config-sample.php 。（日後繼續更新此檔將說明）


#### 設定權限

若 WordPress 在安裝與更新套件過程中提示需要填入連線資訊，表示該程式沒有取得對外下載檔案的權限，此時應該設定權限

    sudo chown -R www-data:www-data /var/www/html
