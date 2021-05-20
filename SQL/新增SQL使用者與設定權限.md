# 新增SQL使用者

``` SQL
CREATE USER 'username'@'hostname' IDENTIFIED BY '密碼';
```
`username`就是設定名字`hostname`就是能進入的ip位置 % 是萬用字元，表示允許從任何地方登入或者用0.0.0.0

Ex:
``` sql
CREATE USER 'Eria'@'%' IDENTIFIED BY '12345678';
```
建立新使用者 Eria 並且密碼為 12345678，且允許從任何地方登入 (從本地端或遠端連線都可)。
