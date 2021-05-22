# Exposed
[Getting Started](https://github.com/JetBrains/Exposed/wiki/Getting-Started)
首先設定`build.gradle`
```  groovy
dependencies {
    implementation("org.jetbrains.exposed:exposed-core:$exposedVersion")
    implementation("org.jetbrains.exposed:exposed-dao:$exposedVersion")
    implementation("org.jetbrains.exposed:exposed-jdbc:$exposedVersion")
}
```
`$exposedVersion`的部分替換成當前版本

---
### connection連接
> 連接SQLite

Step
1. 將`org.sqlite.JDBC`導入
``` groovy
dependencies {
    //導入sqllite
    implementation 'org.xerial:sqlite-jdbc:3.34.0'
}
```
2. import Database
``` kotlin
import org.jetbrains.exposed.sql.Database
```

3. 連接sqlite
``` Kotlin
Database.connect("jdbc:sqlite:./data.db", "org.sqlite.JDBC")
```
---

## [DSL](https://github.com/JetBrains/Exposed/wiki/DSL)
### 創建`Table`:
Table需要複寫PrimaryKey來設定主key
``` kotlin
object StarWarsFilms : Table() {
  val id: Column<Int> = integer("id").autoIncrement()
  val sequelId: Column<Int> = integer("sequel_id").uniqueIndex()
  val name: Column<String> = varchar("name", 50)
  val director: Column<String> = varchar("director", 50)
  override val primaryKey = PrimaryKey(id, name = "PK_StarWarsFilms_Id") // PK_StarWarsFilms_Id is optional here
}
```
或者自動生成PrimaryKey id
```kotlin
object StarWarsFilms : IntIdTable() {
  val sequelId: Column<Int> = integer("sequel_id").uniqueIndex()
  val name: Column<String> = varchar("name", 50)
  val director: Column<String> = varchar("director", 50)
}
```
* 並且可以加上`.nullable()`代表可以為null
* 或者`.uniqueIndex()`代表此欄位不能重複
* 以及`.autoIncrement()`會自動增加數值Ex id = 1,2,3,4.....

### 接下來我們需要`transaction`當作一筆執行交易
``` kotlin
transaction {
}
```
在裡面就可以開始對資料庫進行操作了
``` Kotlin
SchemaUtils.create (Cities) //創造Table
```
建立Table
``` Kotlin
SchemaUtils.drop(Cities) //刪除Table
```
將Table刪除，假如更改了Table架構記得要刪除在建立否則會出錯

---
### 插入資料`Insert`
``` kotlin
val id = StarWarsFilms.insertAndGetId {
  it[name] = "The Last Jedi"
  it[sequelId] = 8
  it[director] = "Rian Johnson"
}
```
OR
``` kotlin
 val stPeteId = StarWarsFilms.insert {
  it[name] = "The Last Jedi"
  it[sequelId] = 8
  it[director] = "Rian Johnson"
} get StarWarsFilms.id //get 代表 get stPeteId 他會給StarWarsFilms的id
```

