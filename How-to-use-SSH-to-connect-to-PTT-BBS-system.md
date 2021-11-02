# 如何使用 SSH 連接 PTT BBS 系統
How to use SSH to connect to PTT BBS system

[PTT](https://www.ptt.cc/cls/1) 是全台灣最大的 BBS 系統，而 [BBS](https://zh.wikipedia.org/wiki/BBS) 為 ~~古老~~ 資深的網路論壇系統，是Web介面的網路論壇的前身，一般透過連接伺服器的遠端通訊協議進行連線，以往使用 Telnet 協議進行連線，如今可以使用安全性更高的 ssh 協議，也就是本專案中用來連接遠端伺服器、雲端主機服務的通訊方式來連接此論壇

以下將說明連接方式。

## 通用使用方法
若在 Linux 發行版或 Macbook 上，請直接使用終端機以 SSH 進行連線，設定SSH KEY的方式因為其他說明有，因此不再重新說明

### 預設方式：
    ssh bbs@ptt.cc

### Unicode連線方式：
    ssh bbsu@ppt.cc


## Windows 上的 SSH 使用說明

在 Windows 上，早期並沒有內建 SSH 協議，因此需要安裝額外軟體，例如使用 PuTTY 或其他套件來連線，但在 Windows 10 以後，作業系統已內建 SSH 的相關軟體與設定，您可以選擇直接使用終端機或是另外安裝軟體連線 (用Git內建的終端機也可以，因為Git也是透過SSH溝通的)

經測試，使用 PowerShell 可以連線，詳細指令可以參考以上 **通用使用方式** 的指示進行操作