﻿# 如何安裝及使用 SSH KEY

SSH 可以讓使用者遠端連線到別台主機進行各種操作，您可以不用親自跑到別台主機操作程式，只需透過此協議即可連接該主機進行各種的操作，但也因此可能會造成安全疑慮，所以SSH除了使用帳號密碼連接以外，也透過 SSH KEY 加密金鑰的方式保障遠端連線的安全性，一方面連線的過程是加密的 (原理與 https 相同)，另一方面，因為 SSH KEY 的設計，只有持有該金鑰檔的電腦或其他裝置可以連線到該台電腦，因此可以避免密碼被竊取的可能性(但需要開啟金鑰認證)

本篇將以Ubunut Disktop 16.04 版做示範，若您採用其他版本的Linux發行版，可能部分指令與路徑會有所不同，例如安裝/管理套件的 apt-get 指令要改用 yum ，或者是資料夾路徑會不同，若有不同之處我會在內文提醒，大家可以知道那些指令會不同，謝謝 !

## 在來源電腦(客戶端) 產生SSH KEY

### 1. 找到 Terminal 終端機
![Find the terminal](https://github.com/toppy368/VPS-HELP/blob/master/images/HowToSetUpandUseSSHKEY/FindtheTerminal.png)

### 2. 開啟 Terminal 終端機
![Open the Terminal](https://github.com/toppy368/VPS-HELP/blob/master/images/HowToSetUpandUseSSHKEY/OpentheTerminal.png)

### 3. 執行 ssh-keygen 進入 ssh key 安裝流程
請輸入這個指令
`ssh-keygen`  
接下來終端機會提醒你即將建立 ssh 金鑰，會分別建立 rsa 公鑰/私鑰到指定路徑(原理之後會說明)  
`Generating public/private rsa key pair.`

Tips: 若想做出更完整的設定，可以使用 `ssh-keygen -C` ，可以指定加密方式，與增加註解給 Git 服務等，詳情請自行使用 `ssh-keygen -help` 查詢使用方式。

### 4. 建立 .ssh 目錄
建立ssh key的路徑，按下Enter之後，檔案會儲存在此路徑當中  
`Enter file in which to save the key (/home/[Your ID]/.ssh/id_rsa):`

#### 4-1 Tips:若想另存一個以上的 SSH Key 該怎麼做 ?
Tips：若想新增不同的 ssh 檔 (例如一組 SSH KEY 給主機、一組給 Git )，可以根據以上路徑重新命名，例如在這一行直接輸入 `id_git_ssh` ，可直接產生此名稱的金鑰檔到根目錄，若想維持原有路徑另存新檔則建議輸入 `/home/[Your ID]/.ssh/id_git_ssh`

### 5. 輸入密碼
這裡會提示大家輸入 passphrase ，可以視為密碼，檔案會根據你輸入的內容進行加密，最短5個英文字，但是沒有長度限制與特殊符號限制，你可以直接使用強密碼原則即可

	Enter passphrase (empty for no passphrase):
	Enter same passphrase again:

本文件為了示範，輸入的passphrase字串為`TESTWORD`，但原則上建議設定強一點且不與網際網路服務共用的密碼以策安全

### 6. 顯示產生金鑰成功等相關訊息
出現以下訊息，表示ssh key檔案產生好了

	The key fingerprint is:
	SHA256:Yj1Y/qgVBv82tDAyrKbLo5oZQNhGY6NTAkIKkzrEzbQ toppy368@ubuntu
	The key's randomart image is:
	+---[RSA 2048]----+
	|XoX.             |
	|*@ =.            |
	|B.oE  . .        |
	|+o   . B         |
	|..    B S .      |
	|.    o = X .     |
	|.   o   o *      |
	| =.o   o . .     |
	|*.+o  .          |
	+----[SHA256]-----+

### 7. 找到.SSH 資料夾  
Ubuntu的SSH KEY會放在` /home/[你的ID]/.ssh `資料夾中，以下步驟將展示此資料夾的位置，確認金鑰正常產生之後可以複製備份起來，若日後遺失可以找得回來  

![Find the ssh folder 1](https://github.com/toppy368/VPS-HELP/blob/master/images/HowToSetUpandUseSSHKEY/Find_the_ssh_folder_1.png)

![Find_the_ssh_folder_2](https://github.com/toppy368/VPS-HELP/blob/master/images/HowToSetUpandUseSSHKEY/Find_the_ssh_folder_2.png)

按下`Ctrl + h`可以打開隱藏的資料夾，這樣就能找到 `.ssh` 資料夾

### 8. 公鑰/私鑰檔案  


## 在目的地端電腦 (伺服器/VPS/NAS/IoT開發板等) 加入你的 SSH KEY

### 9. 將 pub key 加入目的地端電腦  

### 10. 以 SSH 登入目的地端電腦
	ssh root@[主機端 IP 位置 / Your host's IP address.]  

### 11. 修改設定：取消密碼驗證，只認金鑰  


## 補充說明：匯入ssh 私鑰
	ssh-add ~/.ssh/id_rsa
