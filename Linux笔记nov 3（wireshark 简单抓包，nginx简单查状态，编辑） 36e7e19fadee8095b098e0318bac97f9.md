# Linux笔记nov.3（wireshark 简单抓包，nginx简单查状态，编辑）

笔记

## ***Wireshark* 抓包 新學**

| 主题 | 命令 / 语法 | 使用场景 | 要点 |
| --- | --- | --- | --- |
| 抓包（GUI） | sudo wireshark | 在虚拟机桌面打开图形界面 | SSH 里开不了 |
| 抓包（CLI） | sudo tcpdump -i ens33 | 在 SSH 里也能抓包，相当于后台单独选项运行 | -i 指定网卡（示例为 ens33） |
| 过滤器 | `http` | 只看 HTTP 封包 | 可在抓包工具中作为显示/捕获过滤条件使用（视工具而定） |
|  | `http and ip.addr == 192.168.x.x` | 只看指定 IP 的 HTTP | 将 192.168.x.x 替换成目标 IP |
| HTTP 状态码 | 200 | 请求成功 | 完整回传内容 |
|  | 304 | 内容未改变 | 浏览器使用缓存 |
|  | 404 | 资源不存在 | 找不到文件/路径 |
| HTTPS 原因 | HTTP vs HTTPS | 安全性对比 | HTTP 明文传输，可被 Wireshark 直接看到所有内容（含密码等）；HTTPS 加密后只会看到乱码 |

## ***nginx* 網站操作 新學**

| 网站操作 | 覆盖网页内容 | **echo "內容" | sudo tee /var/www/html/index.nginx-debian.html** | echo 产出文字；tee 写入文件并覆盖原内容 |
| --- | --- | --- | --- |
|  | 测试 nginx 回应 | ***curl [http://192.168.x.x](http://192.168.x.x/)*** | 用文字方式抓网页内容，确认服务可用，測試 nginx 有沒有回應 |
| 路径速查 | nginx 配置与网页目录 | /etc/nginx/ 設定檔 / /etc/nginx/sites-enabled/default 網站設定 / /var/www/html/ 網頁檔案 |  |