# 如何備份 WordPress 網站與備份的注意事項

這份文件是簡報的草稿，可以當成簡報大綱(主架構)的資料來源。

## 自我介紹


## 為什麼網站需要備份

    作者提示：這兩張圖需要說明狡兔有三窟的原因，同時需要檢查是否為CC0授權的圖檔或新聞圖檔 (註：CC0等於公共領域，至於新聞則是因為單純描述新聞內容不受著作權保護)

第一章圖片可用素材：
https://zh.wikipedia.org/wiki/File:Impact_event.jpg

第二張圖片可用素材：  
https://en.wikipedia.org/wiki/File:Wana_Decrypt0r_screenshot.png

> 授權條款說明：維基百科的授權條款都放在網址內文中，本簡報均採用公共領域或可免費商業使用的圖檔，以避免著作權侵權爭議。

## 為什麼網站需要備份 - 結論

第三張圖片可用素材：
https://www.pexels.com/photo/crop-man-sealing-cardboard-box-with-tape-4506249/

> 授權條款說明：https://www.pexels.com/license/

結論：防範(意外)於未然，狡兔有三窟！  

無論主機商、網站程式升級 (WordPress 主程式或套件升級發生意外)、或發生資安事故時，網站本身若有備份，可以先救回資料再並進行補救措施。  

若要客製化/對WordPress做不可預期的操作(例如：更改ＷordPress程式碼、手動操作資料庫等)，也必須備份以避免發生意外。  

平時也可整理網站所需要的內容，當成網站的緊急救難包/打包後的行李，未來當主機發生意外或需要搬家時 (例如主機商倒閉) ，可以將網站搬移至其他主機商。


## 備份網站的注意事項 - 圖檔素材

圖檔素材：https://www.irasutoya.com/2015/06/blog-post_344.html?m=1

> 授權條款說明：https://www.irasutoya.com/p/terms.html

## 備份網站的注意事項 - WordPress 成份說明

> 編輯備註：此內容為簡報的詳細版本，但可能會簡化

* ~~WordPress 主程式~~ ：WordPress主程式的PHP部分，不需備份此程式，因為 [WordPress.org](https://tw.wordpress.org/download/) 官網就有最新版本，直接下載最新版本吧 !
* SQL 資料庫：**網站的文章、套件設定與會員資料都會儲存在資料庫中** ，此為重要資料請一定要備份出來 !
    * XML 資料：正式名稱為 WordPress eXtended RSS (WXR)，可作為SQL資料的替代品，WordPress主選單下的 `工具 > 匯出程式` 可以找到 匯出XML 的選項，要匯入請於空的網站尋找 `工具 > 匯入程式` 即可匯入XML。
* 媒體庫、套件與佈景主題：
    * 媒體庫：這通常 **儲存文章的圖片與影片** ，通常 WordPress 預設的路徑為 `/<你的 WordPress 網站目錄>wp-content/uploads/`，但如果有變更媒體庫的位置，或把圖片放在另一個圖床伺服器，請以變更後的路徑為主。
    * 套件：路徑為 `/<你的 WordPress 網站目錄>/wp-content/plugins`。
    * 佈景主題：路徑為 `/<你的 WordPress 網站目錄>/wp-content/themes`。
* 網站、主機的各種設定：最重要的內容是`wp-config.php`裏頭儲存的主機位置與密碼等設定(也包含 WordPress 帳密)，如果你有使用 `SSH KEY` 或 `https 的憑證` 也請備份起來，避免進不去舊主機。

* WordPress 程式相關
    * ~~主程式~~ (因官網有此檔案，所以不需備份，但需知道網站正在運作的WordPress版本為多少)
    * 佈景主題 （路徑：`/<你的 WordPress 網站目錄>/wp-content/themes`）
    * 套件 （路徑：`/<你的 WordPress 網站目錄>/wp-content/plugins`）
    * 媒體庫 （路徑：`/<你的 WordPress 網站目錄>wp-content/uploads/`）
    * wp-config.php (WordPress 設定擋)
    * 其他套件設定 （例如Google網站工具的檔案、套件的API KEY與密碼等）



## 備網站備份的注意事項 - 站長操作備份的原則

> 作者提示：此段可能會刪除或簡化 （順序可能也會搬移）

* 虛擬主機使用者：虛擬主機有提供後台與FTP權限，需手動設定主機商給的空間並傳輸/安裝WordPress
* VPS 或 雲端主機 (GCP或AWS EC2等視同雲端主機) 使用者：需要手動網頁伺服器環境並安裝 WordPress **(此動作需要Linux指令，具有門檻)**
* 需要安裝 WordPress 網站並安裝套件 (plugins)

簡單來說就是 **需要具有架站的相關知識，同時具有維護網站的能力** ，當自己知道如何架站時，萬一發生不可預知的故障時，至少可以將網站還原回來，**因此這是很重要的基礎能力。**   

當然這些基礎知識對於第一次想架站的夥伴 **具有一定專業度** ，雖然計算機概論課本有明確提到 **主機商、網域、DNS之間的關係** ，但實戰需要更多設定，**因此需要耐心學習。**

如果你是 VPS 或 GCP / AWS / Azure 等空間的使用者，還需要具有 Linux 指令並安裝環境，這些操作可能需要 Debug/排除錯誤 的心理準備。(虛擬主機商都幫你搞定以上的操作)

## 手動備份解說 (會睡著建議簡單帶過或省略)
> 編輯備註：編輯簡報時請區分簡介與詳解的內容，此段可視情況刪減

### 虛擬主機備份法
本次只講解資料庫的備份方法，檔案備份請利用FTP工具或虛擬主機商提供的後臺進行備份。  
虛擬主機通常會給你cPlane等網站管理後臺，這些後臺通常也有檔案備份工具，因為各主機商提供的面板有差異，詳情請利用線上客服或客服表單詢問。

#### 利用 phpMyAdmin 備份 WordPress 的 SQL 資料庫
> 編輯備註：請在此張貼 phpMyAdmin 的備份資料庫操作

### VPS 雲端主機備份法
> 編輯備註：
> 1. 請家需要備份那些內容的細部項目與路徑直接移動過來
> 2. 可用 rsync 語法快速搬移目錄到自己的電腦

## 自動備份：UpdraftPlus 備份套件展示 (Demo時間)
官方下載網址：https://wordpress.org/plugins/updraftplus/
