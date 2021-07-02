# 導入與導出
可以把運行的容器轉移

---
### 導出
把容器導出成tar檔
```
docker ps
docker export [容器 ID] > ubuntu.tar
```
---
### 導入
把導出的容器導入
```
docker import /path/to/ubuntu.tar
```