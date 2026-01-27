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

### 從 GRUB 選單中確認解析度
重開機後，看到選擇作業系統選項時，請輸入  進入 Command 指令模式  
當看到 `grub> ` ，就表示你可以開始輸入指令了

請輸入以下指令以檢查 Grub 能抓到的螢幕解析度
```
vbeinfo
```

有可能會出現以下異常
```
error: can't find command 'vbeinfo'
```
此錯誤的原因是此電腦比較新型，GRUB已改成EFI方式啟動，目前輸入的 `vbeinfo` 指令不適用，因此需要更換指令  

請再次輸入並改成以下指令：
```
videoinfo
```
若成功，將比照剛才上個步驟，GRUB將列出所有能用的解析度，目前生效的解析度則以 `*` 標記起來

> 此時，請將顯示出來的解析度拍照或抄起來，接下來步驟會用到它。

輸入以下指令，離開 GRUB 並重開機：
```
reboot
```
您也可以使用此指令重開機：
```
exit
```

## 從作業系統中修改 GRUB 解析度設定

#### 字太小的原因
HiDPI 螢幕因為解析度太高，所以文字會越來越小，不利於閱讀，因此接下來的步驟需要降低 GRUB 的解析度來放大文字尺寸，而此步驟 **不會** 影響你在作業系統中的螢幕解析度 (兩者是分開設定的)

### 開啟 GURB 設定並修改選單的螢幕解析度

grub 檔案位置：
```
/etc/default/grub
```

使用 VIM 或 nano 開啟 GRUB 設定檔：
```
# 如果您習慣使用 nano 編輯器，請用此指令
# If you are used to using the nano editor, please use this command.
sudo nano /etc/default/grub

# 如果您習慣使用 VIM 編輯器，請用此指令
# If you are used to using the VIM editor, please use this command.
sudo vim /etc/default/grub
```


要修改的項目：
GRUB_GFXMODE=640x480

以及 vim 及 nano 的使用方式

更新 grub 指令：
sudo update-grub
