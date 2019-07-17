## LNMP 安裝筆記

### 安裝與運作環境：
OS:Ububnt 18.04 or 14.04  
Web Server:Nginx  
code:PHP 7  
sql DB:MariaDB  

### 安裝流程簡介

	檢查主機更新與設定 → 安裝與設定 Nginx → 安裝SQL伺服器( MariaDB 或 Mysql 都可，推薦前者) → 設定SQL密碼與其他安全選項 → 安裝並設定 PHP - fpm → 完成

為了方便初學者理解以下這些步驟在做什麼，這裡提供上方的簡化流程。

### 前置作業
**注意：** 以下請開啟終端機輸入指令，一行一行執行  
#### 登入：
	ssh [root id@host ip]

#### 更新：
	sudo apt-get update
	sudo apt-get upgrade

### Install Nginx Server 安裝 Nginx 伺服器：
	sudo apt-get install nginx

#### Test Nginx on Work 測試 Nginx 正常運作：
請於網址欄輸入以下訊息：

	http://[host ip]

**注意：** 主機未簽署與申請 https 證書， https 將無法運作，請將網址手動改成 http ，以免無法開啟網站。

如果成功，將顯示以下畫面：

	Welcome to nginx!

	If you see this page, the nginx web server is successfully installed and working. Further configuration is required.

	For online documentation and support please refer to nginx.org.
	Commercial support is available at nginx.com.

	Thank you for using nginx.


### Install mariadb 安裝 mariadb：
	sudo apt-get install mariadb-server

這次使用 mariadb 取代 MySQL ，這是開源的 SQL 伺服器，可以當成 Fork 分支出來的版本。

**注意：** 安裝過程並沒有提示帳號密碼，也就是說 **此時資料庫的 root 帳號不需密碼就能登入** ，建議先新增一個同樣具有操作資料庫權限的帳號並刪除 root 帳號以策安全。

#### 設定 Mysql 或 MariaDB 資料庫

首先先登入：

	# mysql -u root -p  
	Enter password:

然後新增資料庫、新增帳號與設定密碼，同時將設定新資料庫與新帳號的權限關係，以下為快速設定的方法：

	Welcome to the MariaDB monitor.  Commands end with ; or \g.  
	Your MariaDB connection id is 41  
	Server version: 10.1.40-MariaDB-0ubuntu0.18.04.1 Ubuntu 18.04  

	Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.  

	Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

	MariaDB [(none)]> CREATE DATABASE <Your_database_name>;  
	Query OK, 1 row affected (0.00 sec)

	MariaDB [(none)]> CREATE USER 'Your_new_username'@'localhost' IDENTIFIED BY 'This_user_password';
	Query OK, 0 rows affected (0.00 sec)

	MariaDB [(none)]> GRANT ALL PRIVILEGES ON <Your_database_name>.* TO 'Your_new_username'@'localhost';  
	Query OK, 0 rows affected (0.00 sec)

	MariaDB [(none)]> FLUSH PRIVILEGES;
	Query OK, 0 rows affected (0.00 sec)

	MariaDB [(none)]> exit
	Bye

詳細說明請參考本專案的此文章，有每個操作的詳細說明：
[Create MySQL and MariaDB database account passwords and set permissions](https://github.com/toppy368/ubuntu-vps-doc/blob/master/Create%20MySQL%20and%20MariaDB%20database%20account%20passwords%20and%20set%20permissions.md)

#### Set mariadb secure Option 安裝 mariadb 安全選項：
	sudo mysql_secure_installation

**注意：** 關於 mysql secure installation 安全套件的詳細說明與中文簡譯請參考本專案的 [mysql_secure_installation.txt](https://github.com/toppy368/ubuntu-vps-doc/blob/master/mysql_secure_installation.txt) 文件。

#### Test mysql login 測試mysql登入
	sudo mysql -u Your_new_username -p
	Enter password:

如果成功將顯示以下畫面，可執行任意的 SQL code

	Welcome to the MariaDB monitor.  Commands end with ; or \g.
	Your MariaDB connection id is 51
	Server version: 10.1.34-MariaDB-0ubuntu0.18.04.1 Ubuntu 18.04

	Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

	Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

	MariaDB [(none)]>

此畫面中你可以使用 SQL 語法進行任何的操作 ( 請自行搜尋 SQL 語法並在此自學 ) ，如果要架設 WordPress 請先建立空的資料庫 ( Database ) 。  

如果要離開請輸入 **exit** 。  

	exit

### Install and set up PHP. 安裝並設定 PHP (PHP-fpm)

#### Install php and php connect to mysql set.  
#### 安裝 php 並且將 php 連接到 mysql ：  

	sudo apt-get install php-fpm php-mysql

#### 查詢PHP版本號
為了查詢 php.ini 的路徑，需要查詢版本號，請輸入以下指令：  

	php-cgi –version

以下為查詢結果：  

	Command 'php-cgi' not found, but can be installed with:

	apt install php7.2-cgi
	Please ask your administrator.

請留意此行：  

	apt install php7.2-cgi

本文目前安裝的版本為 **PHP 7.2** 版本，含 CGI 功能 ( 某些 PHP 框架會用到 ) ，版本號會影響 php.ini 位置，請將版本號抄下來。  

**注意：** 若操作時的 PHP 版本不是 7.2 版，則請依照實際內容為主。

#### Modify the php.ini settings. 修改 php.ini 設定。
輸入以下語法以 VIM 開啟 php.ini 檔案：

	sudo vi /etc/php/7.2/fpm/php.ini

**注意：**
1. 以上指令的路徑中， php 後方的 **7.2** 為版本號，如果操作的 PHP 並非 7.2 版本，請改成實際的版本號以符合實際路徑。  
2. 本範例使用 VIM 作為編輯器 ( 作者習慣 )，使用者也可採用 nano 等編輯器進行此操作。  

VIM可輸入/搜尋關鍵字(字串)：  

	/cgi.fix_pathinfo

搜到的結果會長這樣：

	;cgi.fix_pathinfo=1

此功能已被以分號 ; 註解，預設值為 1 表示 **啟用** 此功能，但若運行了還是會引發安全上的疑慮，能讓使用者對網站中的圖檔執行 PHP 腳本，將造成安全疑慮，詳情請自行搜索此參數，或閱讀文件註解上的網址。

請修改成以下內容，將分號去掉後，把 1 改成 0 關閉此功能：  

	cgi.fix_pathinfo=0

VIM 編輯提示：  
```
1. 搜尋結束後，可用 Enter 鍵跳出搜尋模式，可看到編輯游標。
2. 找到想修改的文字內容可按下 i 進入編輯模式，可輸入修改刪除文件內容。
3. 修改完畢後，可以按下 ESC 關閉編輯模式，再用 : 進入指令模式，執行 :wq 指令可將文件存檔後離開文件。
4. 若你改錯了，不想存檔想重新編輯，可以 : 進入指令模式 :q 不存檔離開文件。
```

存檔關閉文件後，請重新啟動 php 程式  

	sudo systemctl restart php7.2-fpm

### 設定Nginx

#### 修改Nginx設定檔  

	sudo vi /etc/nginx/sites-available/default

#### 修改此行，新增 index.php 為預設首頁  

	index index.php index.html index.htm index.nginx-debian.html;

請在裡頭新增 index.php  

	index.php

#### 指定URL的IP位置或網域  

	server_name _;

請改成以下結果  

	server_name [Your host ip or Domain Name];

[] 內的內容請用主機的IP或是網域名稱取代，如果已申請網域，請在DNS上新增A記錄並填上主機的IP，設定完畢後，任何使用者都可以使用網域名稱連接本伺服器的網站。


#### 設定 NGINX 連接到 php-fpm 的方法。
此文件的最下方有個被註解包住的 **pass PHP scripts to FastCGI server** 設定值，瀏覽 [PHP FastCGI Example - Nginx](https://www.nginx.com/resources/wiki/start/topics/examples/phpfcgi/) 可獲得詳細說明，從文件中的 Connecting NGINX to PHP FPM 段落可得知此段落可以設定 NGINX 連接到 PHP-fpm 的方法。

文件的最下方將看到以下段落：

	# pass PHP scripts to FastCGI server
    #
    #location ~ \.php$ {
    #       include snippets/fastcgi-php.conf;
    #
    #       # With php-fpm (or other unix sockets):
    #       fastcgi_pass unix:/var/run/php/php7.0-fpm.sock;
    #       # With php-cgi (or other tcp sockets):
    #       fastcgi_pass 127.0.0.1:9000;
    #}


應刪除註解並改成以下內容(說明註解不刪除，讓大家查文件)：

	location ~ \.php$ {
		include snippets/fastcgi-php.conf;

		# With php-fpm (or other unix sockets):
		#請將以下路徑的php7.0fpm.sock改成php7.2-fpm.sock(或您目前查到的版本號),以符合目前版號
		fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
    }

**注意：** 範例設定檔的版本為 **PHP 7.0 fpm** 版，已經不合乎目前裝的最新版本 **PHP 7.2 fpm** ，請留意此行並修改成您目前安裝的版本號

#### 設定讓Nginx取消存取.hatccess  
此段落已說明此設定的用意：如果此Nginx伺服器的根目錄與Apache跟目錄相同時，拒絕存取 .hatccess 檔

	# deny access to .htaccess files, if Apache's document root
    # concurs with nginx's one
    #
    #location ~ /\.ht {
    #       deny all;
    #}

請將此段落取消註解：

	location ~ /\.ht {
           deny all;
    }

最後文件存檔後離開

#### 測試設定檔語法正確並重新啟動Nginx伺服器

	sudo nginx -t

重啟Nginx伺服器

	sudo systemctl reload nginx


### 新增 info.php 測試PHP是否順利完成安裝

網頁伺服器根目錄如下：(在Ubunut下，Nginx與Apache都是同一個)  

	/var/www/html

#### 使用VIM新增 phpinfo.php

	sudo vi /var/www/html/info.php

#### 請新增以下PHP程式碼，將列出所有PHP版本細部資訊  

	<?php
	phpinfo();
	?>

#### 開啟以下網頁並瀏覽info.php頁面

	http://[Your host ip or Domain Name]/info.php

如果看到以下畫面就完成了

(擺放info.php圖檔)

**注意：** 此頁面將顯示主機內PHP的所有API與詳細設定的版本與功能資訊，此資訊可能會讓使用者嘗試存取網站內可能的漏洞，具安全疑慮，建議將本檔案刪除。


刪除的方法(也可用FTP客戶端用SFTP連接到此路徑)：

	sudo rm /var/www/html/info.php

### 大功告成 !

現在環境已完整的建立成功 ! 此環境可拿來架設 [WordPress](https://wordpress.org/) 等CMS系統、也可以開發網站並使用框架建立服務等。
