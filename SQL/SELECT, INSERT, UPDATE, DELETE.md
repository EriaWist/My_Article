# SELECT, INSERT, UPDATE, DELETE

### 假設Table內容長這樣
```sql=1
  id INT NOT NULL AUTO_INCREMENT, # ID 會自動生成
  name varchar(50) NOT NULL,  # 名稱
  descr varchar(200),  # 說明
  price INT NOT NULL,  # 價格
  PRIMARY KEY(id)      # 主要索引、PK、Primary Key(必要)
```

### 首先插入資料 `INSERT INTO` 
``` sql
INSERT INTO 資料表名稱 (name, descr, price)
  VALUES ('水', '可以喝', 20);
```
### 搜尋資料`SELECT FROM`
```sql=1
SELECT * FROM 資料表名稱;
```
取得`資料表名稱`的所有欄位所有資料
``` sql=1
SELECT id FROM 資料表名稱; #取得id欄位所有資料
```
也能夠取得特定欄位表
``` sql=1
SELECT price,descr FROM 資料表名稱 WHERE name='水';
```
取得欄位名稱為`水`的價格和說明，當然`WHERE`還有很多用法後續會介紹

### 更新資料`UPDATE`
``` sql=1
UPDATE 資料表名稱 SET descr = '多喝水沒事，沒事多喝水' WHERE name = '水';
```
把名字為`水`的資料，說明更新為`多喝水沒事，沒事多喝水`
### 刪除資料DELETE
```sql=
DELETE FROM 資料表名稱 WHERE name = '水';
```
