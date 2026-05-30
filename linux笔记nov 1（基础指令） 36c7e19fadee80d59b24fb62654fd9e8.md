# linux笔记nov.1（基础指令）

笔记

网路

#### ip addr

查網卡和 IP 地址，找 `inet` 那行

#### ip route

查路由表，`default via` 是流量出口（網關）

#### ping 8.8.8.8

測試網路通不通，Ctrl+C 停止

#### ping [google.com](http://google.com)

測試 DNS + 外網，能解析出 IP = DNS 正常

#### dig [google.com](http://google.com)

查 DNS 解析詳細結果，看 ANSWER SECTION

#### nslookup [google.com](http://google.com)

簡易 DNS 查詢，和 dig 目的一樣

#### ss -tulnp

查哪些程式在監聽哪些端口

#### tcpdump -i ens33

抓網卡上所有進出的封包，看真實流量

**檔案系統**

#### ls

列出資料夾內容

#### ls -la

詳細列出，含隱藏檔和權限

#### cat /etc/resolv.conf

顯示檔案內容，這裡是查 DNS 設定

**軟體 & 服務管理**

#### sudo apt update

刷新軟體清單（不是升級）

#### sudo apt install xxx -y

安裝軟體，-y 自動同意所有詢問

#### sudo systemctl start nginx

啟動服務

#### sudo systemctl status nginx

查服務狀態，active(running) = 正常

#### sudo

用管理員身份執行指令

**遠端連線**

#### ssh user@ip

遠端登入控制另一台機器，這是管理伺服器最核心的操作