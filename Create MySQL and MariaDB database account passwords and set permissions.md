# 建立 MySQL 與 MariaDB 帳號並設定權限

## 使用管理員帳號創造新資料庫與新使用者帳號密碼

### 以 root 密碼登入資料庫
    # mysql -u root -p  
    Enter password: [root password]

這裡的 -u 表示帳號，root 為 Mysql 與開源分支的 MariaDB 預設的管理員帳號。
**注意：** 預設狀態下，root 不需帳號密碼即可登入，出現 Enter password 可直接使用空白密碼以 Enter 登入。

出現此段落表示成功登入：  

    Welcome to the MariaDB monitor.  Commands end with ; or \g.  
    Your MariaDB connection id is 41  
    Server version: 10.1.40-MariaDB-0ubuntu0.18.04.1 Ubuntu 18.04  

    Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.  

    Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.  

請在本段落輸入SQL指令：  

    MariaDB [(none)]>

看到以上指令，原則尚可進行任何的SQL指令操作，但本次只操作新增資料庫與新增使用者的指令，其餘指令需請讀者自行搜尋sql資料庫相關知識。

### 建立新資料庫供服務使用
請在此段落輸入指令：  

    MariaDB [(none)]> CREATE DATABASE <Your_database_name>;  
    Query OK, 1 row affected (0.00 sec)

請將範例中的 **<Your_database_name>** 刪除 **<>** 符號，並變更為你想創造的資料庫名稱供網站或會使用此資料庫的程式使用。

#### 小提示：指令成功與失敗的顯示畫面

若指令下達成功將出現此行：  

    Query OK, 1 row affected (0.00 sec)

若失敗將顯示類似指令：  

    ERROR 1064 (42000): You have an error in your SQL syntax;...

此行還會提示你是第幾行指令語法有問題等等，如果您常常下達sql指令，建議看看錯誤訊息詳細內容再修正，若只想進行本文章的操作，只需判斷此指令是否成功就好。

### 建立新使用者帳號與設定密碼

    MariaDB [(none)]> CREATE USER 'Your_new_username'@'localhost' IDENTIFIED BY 'This_user_password';
    Query OK, 0 rows affected (0.00 sec)

此行的 **'Your_new_username'** 為 **帳號** ， **'localhost'** 為 **主機ip** ，因為直接架設在此機器上所以會寫成localhost， **'This_user_password'** 為 **密碼** ，**請依照自身需求設定帳號名稱**，密碼建議越長越好。（對於"密碼長度月越長越好"這建議有疑問的讀者請自行搜尋強密碼）

### 設定新使用者可操作新資料庫相關權限

    MariaDB [(none)]> GRANT ALL PRIVILEGES ON <Your_database_name>.* TO 'Your_new_username'@'localhost';  
    Query OK, 0 rows affected (0.00 sec)

這一段是設定權限，設定資料庫可以讓某個使用者帳號登入並使用，因資料庫可能不只一個帳號，所以需要做這設定，指令中的 **<Your_database_name>** 為剛才新增的 **資料庫** ， **'Your_new_username'** 為 **使用者帳號**，請自行修改後執行此指令。

更新權限表：  
    MariaDB [(none)]> FLUSH PRIVILEGES;
    Query OK, 0 rows affected (0.00 sec)


## 測試新帳號與新資料庫是否能正常使用
