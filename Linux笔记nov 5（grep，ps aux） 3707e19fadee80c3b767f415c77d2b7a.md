# Linux笔记nov.5（grep，ps aux）

笔记

## **文字處理：*grep* 新學**

| 指令 | 用途 | 範例 |
| --- | --- | --- |
| `grep "字" 檔案` | 在檔案裡搜尋包含指定字串的行 | `grep "error" app.log` |
| `grep -c "字" 檔案` | 只計算符合的行數，不顯示內容 | `grep -c "error" app.log` |
| `指令 \| grep "字"` | 過濾另一個指令的輸出 | `ps aux \| grep nginx` |
| `grep "Chrome" access.log` | 從 nginx 日誌找特定 User-Agent（例如瀏覽器請求） | `grep "curl" access.log` |

## **進程管理 新學**

| 指令 | 用途 | 範例 / 備註 |
| --- | --- | --- |
| `ps aux` | 列出所有正在跑的程式，包含 PID、CPU、記憶體資訊 | — |
| `ps aux \| grep nginx` | 找 nginx 的進程，取得 PID | — |
| `kill PID` | 終止指定 PID 的進程（不是程式名稱） | 例：`kill 1234` |
| `sudo systemctl start nginx` | 用 systemctl 啟動服務，讓它受 systemd 管理 | 不要用 `sudo nginx` 直接啟動；直接啟動後 systemctl 可能查不到狀態（不在 systemd 管理下） |