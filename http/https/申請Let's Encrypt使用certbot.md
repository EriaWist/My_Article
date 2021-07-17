# 申請免費的 ssl tls 可以透過certbot進行申請與認證
- #### [Let's Encrypt官網](https://letsencrypt.org/zh-tw/docs/#)
- #### [certbot網站](https://certbot.eff.org/)
---
### 需要材料:
#### 1. 域名Domain Name
#### 2. 伺服器server
#### 3. 伺服器要有靜態ip並且能夠對外

---
### 流程
1. 到[certbot網站](https://certbot.eff.org/)往下滑選擇作業系統並
2. 跟者說明下指令
3. 當下到 `sudo certbot certonly --standalone` 或者 `sudo certbot certonly --webroot` 根據需求選擇
4. 並且閱讀終端機內的訊息跟者執行
---
### certbot 語法
當申請完成想要查看 key 時
```
cerbot certificates
```