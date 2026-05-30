# Linux笔记nov.6(防火墙ufw）

笔记

## **防火牆 ufw 新學**

| 指令 | 用途 |
| --- | --- |
| sudo ufw enable | 開啟防火牆，預設擋掉所有連線 |
| sudo ufw allow 80 | 放行 80 端口（nginx 網頁） |
| sudo ufw deny 80 | 封鎖 80 端口 |
| sudo ufw status | 查目前所有防火牆規則 |