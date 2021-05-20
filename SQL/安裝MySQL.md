# 安裝MySQL
###  在Ubuntu上:
 > 先更新一下apt
 ``` 
 sudo apt update
 ```
 > 安裝MySQL
```
sudo apt install mysql-server
```
___
### 設置MySQL:
```
sudo mysql_secure_installation
```
中間有很多問答

像是問你密碼複雜度(之後創建使用者之類的密碼複雜度)
```
Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 0
```
輸入密碼
```
New password: 

Re-enter new password: 
```
大致評估密碼強度問你是否繼續
```
Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : Y
```
SQL有個匿名使用者為了方邊安裝設定是否刪除
```
Remove anonymous users? (Press y|Y for Yes, any other key for No) : Y
```
是否拒絕遠端登入root Yes是拒絕遠端登入root
```
Disallow root login remotely? (Press y|Y for Yes, any other key for No) : Y
```
是否刪除測試資料庫
```
Remove test database and access to it? (Press y|Y for Yes, any other key for No) : Y
```
是否重開SQL套用設定
```
Reload privilege tables now? (Press y|Y for Yes, any other key for No) : Y
```
___
### 測試SQL:
```
sudo mysql -u root -p
```