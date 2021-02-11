# ubuntu-vps-doc
這個案子是各種ubuntu的教學文檔，這份文件是收集我關於架設網站的詳細操作內容而成的使用手冊，我架站的過程會參考本專案的詳細內容進行操作，被我(作者)當成筆記本使用，基本上可以當成使用說明書使用。

對於閱讀本檔案的讀者或開發人員來說，我是比較希望大家把這檔案當成維基百科來用，大家可以基於Git的方式糾正文檔的錯誤並申請貢獻，若要提報文檔錯誤可以使用issue功能，直接申請修改內容可使用Git的 [pull request](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) 功能，謝謝 ! 

## 文章列表
* [How to use git command](https://github.com/toppy368/ubuntu-vps-doc/blob/master/How-to-use-git-command.md)：使用Git指令的簡易教學  

* [LNMP Installation process](https://github.com/toppy368/ubuntu-vps-doc/blob/master/LNMP-Installation-process.md) ：安裝 Nginx、PHP、MariaDB網頁伺服器環境的教學。  

* [Quick installation WordPress.md](https://github.com/toppy368/ubuntu-vps-doc/blob/master/Quick-installation-WordPress.md)：安裝完網頁伺服器後，安裝WordPress的教學  

* [mysql backup & Import.md](https://github.com/toppy368/ubuntu-vps-doc/blob/master/mysql-backup-&-Import.md)：資料庫的匯入匯出指令說明。

* [How to backup your WordPress website.md](https://github.com/toppy368/ubuntu-vps-doc/blob/master/How-to-backup-your-WordPress-website.md)：備份 WordPress 的注意事項，這是演講簡報的詳細資料，也用來提醒大家備份網站應該注意的內容與建議步驟。

* [Install Laravel with Docker.md](https://github.com/toppy368/ubuntu-vps-doc/blob/master/Install-Laravel-with-Docker.md)：Laravel提供了一個透過Docker快速安裝Laravel的方法，此文件已為此整理透過Docker建立 Laravel 專案的方式，此方法在 Laravel 官網稱為 Laravel Sail ‧

## LICENSE 著作權授權
本專案為 MIT LICENSE 著作權授權合約，詳細授權合約內容請參考本專案的 LICENSE 檔案。  

這是一份自由軟體許可證其中之一，關於開放文化與自由軟體相關的說明可參考 [自由軟體 - 維基百科，自由的百科全書](https://zh.wikipedia.org/wiki/%E8%87%AA%E7%94%B1%E8%BD%AF%E4%BB%B6)，關於 MIT LICENSE 的詳細說明請參考 [MIT授權條款 - 維基百科，自由的百科全書](https://zh.wikipedia.org/wiki/MIT%E8%A8%B1%E5%8F%AF%E8%AD%89) 。

## 如何貢獻

    取自於社會、用之於社會

這是一份以開放授權的方式提供出來的網站伺服器教學文件，歡迎大家提供各種意見與貢獻內容，你的貢獻將幫助其他讀者，感謝大家。

直接使用Git的方式進行操作即可，舉例來說：
* 若要提報文章錯誤內容：請提出 issue 。
* 若要申請修正或新增內容：請直接提出 pull request ，根據此運作原理，修改內容會經過審核，確認無誤後會將你的更新內容加入且合併進本案子中 (此動作稱為 Merge )，若內容有誤則會退回申請。

## 填坑專區：此處有坑洞，需要路平專案照顧，請小心請勿跌進去

* [Install Composer and Laravel](https://github.com/toppy368/ubuntu-vps-doc/blob/master/Install%20Composer%20and%20Laravel.md)：安裝 Laravel 的教學，未完待續。
* 需要合併以下專案，合併完成後以下專案將 **刪除** ：
    * [VPS-HELP](https://github.com/toppy368/VPS-HELP)
    * [phpMyAdmin_help](https://github.com/toppy368/phpMyAdmin_help)
* 專案L10n並Wiki化：讓本專案有容納基於同樣說明但多種語言方便各國人士閱讀的空間，同時Wiki化讓非Git使用者容易貢獻，如有需求或解法歡迎提出issue討論。
