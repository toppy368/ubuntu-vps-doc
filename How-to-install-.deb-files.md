# 如何安裝 .deb 檔

文件將以 Visual Studio Code 為範例示範，若官方網站只提供 deb 檔，如何安裝它‧

1. 透過搜尋引擎找到該套件的官方網站  
此步驟可以檢查來源是否可靠，包含安全性等，基於安全理由，從網路上下載安裝檔時，建議直接從官方網站下載安裝檔比較好‧(或第三方網站提供的網址是官方/可信任來源也行)

2. 連上官方網站的下載頁面，通常是Dwonload  
參考網址：https://code.visualstudio.com/Download

3. 檢查下載選項  
Linux發行版當中， Ubuntu 與 Debian 可以使用 .deb 檔安裝，而 Fedora、SUSE 與 Red hat 可以用 .rmp 檔，使用者可以依照自己的需求下載檔案，本次教學以 Ubuntu 為主‧

下載時請注意，若官方提供的檔案為 .tar.gz 則為壓縮檔，下載後請先解壓縮，並透過指令進入解壓縮後新增的資料夾 (Downloads 裡面再多一層資料夾，內為解壓縮後的檔案) 再進行以下操作

4. 下載完成後，透過指令進入該資料夾

可用以下指令：  

    cd ~/Downloads

或以下完整指令：  

    cd /home/User/Downloads

5. 列出下載資料夾的所有檔案與詳細資料

可用以下指令：

    ls

將顯示以下結果：

    ~/Downloads$ ls
    code_1.53.2-1613044664_amd64.deb

請照到剛才下載的檔名：

    code_1.53.2-1613044664_amd64.deb

6. 透過 dpkg 套件安裝檔案  

Ubuntu 可透過 dpkg 來執行套件檔的安裝方式，在 Ubuntu 裡，套件安裝檔為 deb 檔，作用類似 Android 的 apk 檔，只是Linux的套件安裝不像 Windows 與 Android 可以直接執行，需要透過指令進行安裝，因此本次需要使用 dpkg 來執行套件安裝檔。

安裝範例如下：

    sudo dpkg -i <可執行的deb檔>

實際安裝步驟請用以下指令：

    sudo dpkg -i code_1.53.2-1613044664_amd64.deb

提醒：安裝任何檔案都需要使用 sudo 指令並輸入密碼以授權安裝檔案，這次Linux的安全設計‧

7. 安裝完成