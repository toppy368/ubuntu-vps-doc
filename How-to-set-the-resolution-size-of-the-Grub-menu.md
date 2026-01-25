# 如何設定 GRUB 選單的解析度

## 事前準備：檢查解析度  
### 在作業系統裡檢查解析度
首先，需要確認目前的螢幕解析度為何，若在 Ubuntu 可於 `設定 -> 螢幕` 找到

![](https://github.com/toppy368/ubuntu-vps-doc/blob/master/Images/Screen_resolution1.png)

![](https://github.com/toppy368/ubuntu-vps-doc/blob/master/Images/Screen_resolution2.png)

> 本步驟以 Ubuntu 為案例，若您使用其他 Linux 發行板，請自行搜索並尋找相關設定

確認完畢請將目前的解析度抄起來或拍照，接下的步驟會用到

### 重開機並確認螢幕解析度

首先請先重開機  

若你在終端機，請輸入以下指令：
```
reboot
```

重開機後，看到選擇作業系統選項時，請輸入 `c` 進入 Command 指令模式