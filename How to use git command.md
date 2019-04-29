## 如何使用 Git 指令 How to use git command


### Git Add 加入檔案進 git  
#### 將 Helloworld.txt 加入git  
<pre lang="no-highlight"><code>
git add <b>Helloworld.txt</b>
</code></pre>
此動作會將Hellworld.txt加入git版控系統中  

#### 將所有檔案加入git  
<pre lang="no-highlight"><code>
git add <b>--all</b>
</code></pre>  

### Git status 檢查Git加入了那些檔案
```
$ git status
```
(這裡放置加入檔案後的結果)

### Git commit 加入修改內容記錄  
```
git commit -m "Commti TEXT"
```

### Git push 將修改傳送到Git雲端，及預設的origin / master 分支中  
<pre lang="no-highlight"><code>
git push <b>origin master</b>
<code>
這會將commit的檔案 **全數上傳** 到為 **origin** 或 **master** 分支，分支就像路徑一樣需要特別指定位置，而 origin 或 master 分支預設會顯示在首頁上，等於上線環境。  

#### 設定預設分支並將push內容上傳到 origin / master
git push --set-upstream origin master
