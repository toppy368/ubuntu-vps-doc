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

    MariaDB [(none)]> CREATE DATABASE <Your database name>;  
    
### 建立新使用者帳號與設定密碼

### 設定新使用者可操作新資料庫相關權限

## 測試新帳號與新資料庫是否能正常使用
