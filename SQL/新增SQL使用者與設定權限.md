# 新增SQL使用者與設定權限

``` SQL
CREATE USER 'username'@'hostname' IDENTIFIED BY '密碼';
```
`username`就是設定名字`hostname`就是能進入的ip位置 % 是萬用字元，表示允許從任何地方登入或者用0.0.0.0

Ex:
``` sql
CREATE USER 'Eria'@'%' IDENTIFIED BY '12345678';
```
建立新使用者 Eria 並且密碼為 12345678，且允許從任何地方登入 (從本地端或遠端連線都可)。

> 下列指令可以查看目前使用者
``` sql
SELECT User,Host FROM mysql.user;
```
>以及查看Eria的權限(Eria可替換其他使用者)
``` sql
SHOW GRANTS FOR Eria;
```
___
創建好後使用者後要設定使用者對各個資料庫與Table的各項權限
``` sql
GRANT type_of_permission ON database_name.table_name TO 'username'@'hostname';
```
`type_of_permission`就是各個權限，`database_name.table_name`資料庫名稱與Table名稱，`username`和`hostname`(哪裡來的ip有權限)概念上與創建時一樣

> type_of_permission 有以下幾種
> * ALL PRIVILEGES - 所有的權限
> * CREATE - 可以建立資料表或資料庫的權限
> * DROP - 可以刪除資料表或資料庫的權限
> * DELETE - 可以在資料表中刪除資料的權限
> * INSERT - 可以新增資料到資料表的權限
> * SELECT - 可以查詢資料表的權限
> * UPDATE - 可以更新資料表中的資料的權限
> * GRANT OPTION - 可以授權使用權限給其他使用者的權限
可以用,來區隔
```sql
GRANT SELECT,INSERT ON customers.* TO 'Eria'@'%';
```
像是這個就是讓Eria任何ip位置都可以`SELECT`和`INSERT`查詢與新增資料到`customers`的所有Table
```sql
GRANT ALL PRIVILEGES ON *.* TO 'Eria'@'%';
```
給 Eria 在任何ip下所有資料庫和所有資料表的所有操作權限
``` sql
FLUSH PRIVILEGES;
```
在設定完之後記得要`FLUSH PRIVILEGES`做儲存