# 如何在 Apache 與 nginx 上安裝 WordPress  
## WordPress 簡介  
WordPress 是一個採用 PHP 及 MySQL 為平台的部落格架站軟體，使用者只需將 [WordPress.org](https://wordpress.org) 提供的安裝包安裝於VPS上，填一些簡單的設定資料，一套完整的部落格就產生出來了 ! 

這個架站軟體的好處是，使用者不需要從頭寫模板及背後的程式碼，只要提供可以讓 WordPress 運作的伺服器環境，就能夠順利的架設自己的網站，同時因為開放原始碼及 CMS 的特性，提供了完整的後台介面及自由度大的模板、套件功能，讓使用者能將這套系統用於其他用途，例如企業官網、電子商務網站 (可配合 woocommerce )等  

## 安裝前的事前準備
根據 [WordPress.org](https://wordpress.org) 官網提供的 [系統需求](https://wordpress.org/about/requirements/)，安裝 WordPress 建議的環境如下：  
> * PHP version 7 or greater  
> * MySQL version 5.6 or greater OR MariaDB version 10.0 or greater  
> * HTTPS support  

根據我的實務經驗，同時也根據以上官方需求，在 VPS 上安裝 WordPress 需要準備以下幾個項目：

本文件假設大家都裝了 Apache 或 nginx ，也假設大家都裝好了支援 WordPress 的 SQL/MariaDB 與 PHP 引擎，因此將不對環境安裝做解說，若讀者沒有安裝以上環境，請搜尋相關的安裝方式，謝謝 ! 