# 透過 Docker 安裝 Laravel (Laravel Sail)

Laravel 官方在 8.0 以後的版本新增加了 Laravel Sail，這技術是利用Docker與Docker Compose，使用者利用此方式可以不需要一一安裝Laravel的運作環境，可以快速安裝Laravel專案本體與運作環境。

## 原理說明
Docker 會在你的作業系統，例如 macOS 或各種 Linux 發行版中規劃一個空間，一般稱為"容器"，而容器可以裝各種服務，以本專案來說，Laravel是基於PHP程式語言與SQL資料庫運作的網頁開發框架，傳統模式下使用者需要安裝PHP與MySQL或MariaDB才能運作 (線上環境也需要nginx處理連線) ，而Docker可以透過簡單的指令幫你建置好環境，免除設定上的麻煩。

而 Laravel Sail 是透過腳本檔執行 Docker Compose ，並透過 Docker Compose 敘述的內容來建構各種 Laravel 所需要的環境與服務設定等，使用者只需裝好以下的 Docker 與 Docker Compose 就能利用官方提供的指令快速安裝好 Laravel ，比傳統方式簡化許多。

## 安裝 Docker Engine

URL : https://docs.docker.com/engine/install/

Ububnt URL：https://docs.docker.com/engine/install/ubuntu/

## Linux 設定 Docker 的注意事項 (標題暫定)

URL: https://docs.docker.com/engine/install/linux-postinstall/

## 安裝 Docker Compose

URL: https://docs.docker.com/compose/install/

## 安裝 Laravel 

URL：https://laravel.com/docs/8.x/installation

## Laravel Sail 相關說明

URL : https://laravel.com/docs/8.x/sail

### 啟動利用 Sail 所建立的專案

首先，先進入之前已經建立好的專案，官方範例已建立 example-app 專案

    cd example-app

之後，輸入以下指令以啟動此專案：

    ./vendor/bin/sail up

過程中會啟動此專案相關的Docker設定。

最後，請開啟瀏覽器並輸入 localhost 作為網址：

    http://localhost/