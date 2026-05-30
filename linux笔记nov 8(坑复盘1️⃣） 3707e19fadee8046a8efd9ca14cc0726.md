# linux笔记nov.8(坑复盘1️⃣）

笔记

**網路排查標準流程**

先 ping IP（8.8.8.8）→ 再 ping 域名（pornhub/google.com）→ 看路由表（ip route）→ 查 DNS（/etc/resolv.conf）

**不同子網為什麼 ping 不通**

**路由表**沒有那個網段的路徑，封包不知道往哪送。加路由才通，不是防火牆的問題

**DNS 壞掉的特徵**

能 ping 8.8.8.8（網路通）**但** ping google.com 失敗（無法解析域名）= DNS 出問題

**nginx 啟動失敗：Address already in use**

用 sudo nginx 啟動後，再用 **systemctl start nginx** 就衝突，也无法**用sys查状态**，因为**80 端口被佔了**（前面笔记有提过😒👌）

- **解法：先找到手動啟動的 nginx PID 殺掉，再用 systemctl 啟動**
    
    ```jsx
    ps aux | grep nginx → kill PID → sudo systemctl start nginx
    ```
    

**開防火牆後 nginx 連不進去**

sudo ufw enable 後所有端口**預設全擋**，包括 80

- **解法：手動放行 80 和 22**
    
    ```jsx
    sudo ufw allow 80 → sudo ufw allow 22
    ```
    

**nmap 顯示 host down，掃不到任何端口**

nmap 預設先 ping 目標**，防火牆擋掉 ping 就以為主機掛了**

- **解法：加 -Pn 跳過 ping 直接掃**
    
    ```jsx
    nmap -Pn 192.168.244.129
    ```
    

**不同子網 ping 不通**

第二台加了 192.168.2.10，從第一台 ping 不通，**路由表沒有那個網段**

- **解法：手動加路由**
    
    ```jsx
    sudo ip route add 192.168.2.0/24 via 192.168.244.129
    ```
    

**DNS 改壞後域名解析失敗**

**实验已验证**：把 resolv.conf 的 **nameserver 改成 1.2.3.4**，ping google.com 失敗但 ping 8.8.8.8 通

- **解法：改回正確的 DNS**
    
    ```jsx
    sudo nano /etc/resolv.conf → nameserver 8.8.8.8
    ```
    

👍