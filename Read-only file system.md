# Read-only file system
犯了很白痴的錯要記得不能在根目錄建立DB文件`/data.db`
```
Exception in thread "main" java.sql.SQLException: opening db: '/data.db': Read-only file system
```
切記在專案底下創建`./data.db`
```
Database.connect("jdbc:sqlite:./data.db", "org.sqlite.JDBC")
```
