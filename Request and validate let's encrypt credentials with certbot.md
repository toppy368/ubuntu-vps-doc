# 使用 certbot 申請與驗證  let's encrypt 憑證

官方網址：https://certbot.eff.org/

## 開啟教學文件的方法  
進入官網後，請注意這行字，並選擇適合的條件，網站會引到你進入適合教學文件：  
**My HTTP website is running  (Software) on (System)**

**Software** 請填寫你網站運作在那種網頁伺服器，可能是 Apache 也可能是 Nginx  
**System** 請填寫這網站坐在哪個作業系統上

## 事後測試憑證是否正常運作
請執行這一條
**sudo certbot renew --dry-run**

這指令會自動測試憑證是否正常運作與是否自動續約，安裝後請一定要確認這件事
執行完畢後也注意說明 **IMPORTANT NOTES:** ，這將告訴你必要的注意事項
