# 透過 Docker 安裝 Laravel (Laravel Sail)

Laravel 官方在 8.0 以後的版本新增加了 Laravel Sail，這技術是利用Docker與Docker Compose，使用者利用此方式可以不需要一一安裝Laravel的運作環境，可以快速安裝Laravel專案本體與運作環境。

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

## 啟動利用 Sail 所建立的專案

首先，先進入之前已經建立好的專案，官方範例已建立 example-app 專案

cd example-app

之後，輸入以下指令以啟動此專案：

./vendor/bin/sail up

過程中會啟動此專案相關的Docker設定。

最後，請開啟瀏覽器並輸入 localhost 作為網址：

http://localhost/